**Execute these steps on one of the front end VMs**

**Setup production.ini file -**

1. Verify sqlalchemy.url has correct value for 01 PostgreSQL server instance
	![image.png](/.attachments/image-7e5f2a98-e98c-4bb0-8986-5d508af57ce4.png)

2. Uncomment and change value for ckan.datastore.write_url and ckan.datastore.read_url
	![image.png](/.attachments/image-e4eb7e64-6a19-4841-99ff-85ceb439cdf7.png)
	
3. Uncomment these datastore parameters 
	![image.png](/.attachments/image-86b0df7a-df9e-4780-afd2-e56dc000f900.png)

4. Change the ckan.site_url to the opendata portal url
	![image.png](/.attachments/image-c20476d7-7595-45c4-ab55-0fbb9cb5d74e.png)

5. Set ckan.auth.create_default_api_keys = true
	![image.png](/.attachments/image-1517bf21-35e3-4f6e-9f25-ff190a5ca0d6.png)

6. Verify solr and redis parameters have correct values here 
	![image.png](/.attachments/image-a245de9c-47d7-4647-af5a-b61df5b9a195.png)

7. Plugins and Views -
		a. Add these plugins in ckan.plugins - datastore datapusher recline_map_view pdf_view tasmu_theme recline_graph_view
		b. Add this view in ckan.view.default_views - recline_map_view
		c. Uncomment ckan.preview.json_formats
		d. Uncomment ckan.preview.text_formats
		e. Uncomment ckan.preview.image_formats
	![image.png](/.attachments/image-1d4f3348-47a2-45da-b0fe-0a6677786574.png)

8. Language settings for English and Arabic support -
	ckan.locale_default = en
	ckan.locale_order = en ar
	ckan.locales_offered = en ar
	![image.png](/.attachments/image-1c1fdebd-7c66-4a98-ba85-c9a728dce39e.png)

9. Datapusher configuration -
	Uncomment these parameters and add ckan.datapusher.callback_url_base = https://127.0.0.1:5000/
	![image.png](/.attachments/image-90251361-42af-4840-bb44-292155c69897.png)

10. SendGrid configuration -
	Uncomment these parameters and add smtp.password (SendGrid key)
	![image.png](/.attachments/image-2a95b252-62c1-4cfc-88ec-29c331194ea4.png)

Setup PostgreSQL Server -

1. Connect to the PostgreSQL Server -
	psql "host=gresql-<sub>-apps-ckan-<env>-we-04.postgres.database.azure.com port=5432 dbname=postgres user=<username>@gresql-cpd-apps-ckan-tst-we-04 password=<password> sslmode=require"
	
2. Execute SQL Commands -
	CREATE DATABASE datastore_default;
	CREATE ROLE datastore_user WITH LOGIN NOSUPERUSER INHERIT NOCREATEROLE NOREPLICATION PASSWORD 'Tasmu54321';
	CREATE ROLE ckan_default WITH LOGIN NOSUPERUSER INHERIT NOCREATEROLE NOREPLICATION PASSWORD 'Tasmu54321';
	GRANT ALL PRIVILEGES ON DATABASE datastore_default TO ckan_default;

	\c datastore_default
	
	REVOKE CREATE ON SCHEMA public FROM PUBLIC;
	REVOKE USAGE ON SCHEMA public FROM PUBLIC;
	
	GRANT CREATE ON SCHEMA public TO "citus";
	GRANT USAGE ON SCHEMA public TO "citus";
	
	GRANT CREATE ON SCHEMA public TO "ckan_default";
	GRANT USAGE ON SCHEMA public TO "ckan_default";
	
	-- take connect permissions from main db
	REVOKE CONNECT ON DATABASE "citus" FROM "datastore_user";
	
	-- grant select permissions for read-only user
	GRANT CONNECT ON DATABASE "datastore_default" TO "datastore_user";
	GRANT USAGE ON SCHEMA public TO "datastore_user";
	
	-- grant access to current tables and views to read-only user
	GRANT SELECT ON ALL TABLES IN SCHEMA public TO "datastore_user";
	
	-- grant access to new tables and views by default
	ALTER DEFAULT PRIVILEGES FOR USER "ckan_default" IN SCHEMA public
	GRANT SELECT ON TABLES TO "datastore_user";
	
	-- a view for listing valid table (resource id) and view names
	CREATE OR REPLACE VIEW "_table_metadata" AS
	SELECT DISTINCT
	substr(md5(dependee.relname || COALESCE(dependent.relname, '')), 0, 17) AS "_id",
	dependee.relname AS name,
	dependee.oid AS oid,
	dependent.relname AS alias_of
	FROM
	pg_class AS dependee
	LEFT OUTER JOIN pg_rewrite AS r ON r.ev_class = dependee.oid
	LEFT OUTER JOIN pg_depend AS d ON d.objid = r.oid
	LEFT OUTER JOIN pg_class AS dependent ON d.refobjid = dependent.oid
	WHERE
	(dependee.oid != dependent.oid OR dependent.oid IS NULL) AND
	-- is a table (from pg_tables view definition)
	-- or is a view (from pg_views view definition)
	(dependee.relkind = 'r'::"char" OR dependee.relkind = 'v'::"char")
	AND dependee.relnamespace = (
	SELECT oid FROM pg_namespace WHERE nspname='public')
	ORDER BY dependee.oid DESC;
	ALTER VIEW "_table_metadata" OWNER TO "ckan_default";
	GRANT SELECT ON "_table_metadata" TO "datastore_user";
	
	-- _full_text fields are now updated by a trigger when set to NULL
	CREATE OR REPLACE FUNCTION populate_full_text_trigger() RETURNS trigger
	AS $body$
	BEGIN
	IF NEW._full_text IS NOT NULL THEN
	RETURN NEW;
	END IF;
	NEW._full_text := (
	SELECT to_tsvector(string_agg(value, ' '))
	FROM json_each_text(row_to_json(NEW.*))
	WHERE key NOT LIKE '\_%');
	RETURN NEW;
	END;
	$body$ LANGUAGE plpgsql;
	ALTER FUNCTION populate_full_text_trigger() OWNER TO "ckan_default";
	
	-- migrate existing tables that don't have full text trigger applied
	DO $body$
	BEGIN
	EXECUTE coalesce(
	(SELECT string_agg(
	'CREATE TRIGGER zfulltext BEFORE INSERT OR UPDATE ON ' ||
	quote_ident(relname) || ' FOR EACH ROW EXECUTE PROCEDURE ' ||
	'populate_full_text_trigger();', ' ')
	FROM pg_class
	LEFT OUTER JOIN pg_trigger AS t
	ON t.tgrelid = relname::regclass AND t.tgname = 'zfulltext'
	WHERE relkind = 'r'::"char" AND t.tgname IS NULL
	AND relnamespace = (
	SELECT oid FROM pg_namespace WHERE nspname='public')),
	'SELECT 1;');
	END;
$body$;
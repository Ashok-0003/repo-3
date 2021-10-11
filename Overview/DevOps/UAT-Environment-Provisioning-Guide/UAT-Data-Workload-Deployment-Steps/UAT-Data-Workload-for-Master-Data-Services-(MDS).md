# MDS Installation tutorial for UAT.

## 1. Deploy the Infrastructure
[MDS Infrastructure Deployment pipeline](https://dev.azure.com/TASMUCP/TASMU%20Central%20Platform/_build?definitionId=1559)

## 2. Configure the MDS manually.

1. Open the **vm-cpd-datamds-uat-we-01** VM with bastion interface and sign in to the terminal.

1. Open the Master Data Services Configuration Manager and then select Database Configuration in the left pane.

1. Select Create Database to open the Create Database Wizard. Select Next.

1. On the Database Server page, complete the SQL Server instance field, and then choose the Authentication type. Select Test Connection to confirm that you can use your credentials to connect to the database via the chosen authentication type. Select Next.
**Note:** Your authentication must contain the "**sysadmin**" rule for managed instances.
![image.png](/.attachments/image-e0e218d3-0cb4-4dd6-8b99-fad2a3aa6e95.png)
1. Type a name in the Database name field. Optionally, to select a Windows collation, clear the SQL Server default collation check box and select one or more of the available options. For example, Case-sensitive. Select Next.
![image.png](/.attachments/image-44395c66-f0dc-484d-b8e8-06ac778ac8d4.png)
1. In the User name field, specify the Windows account of the default super user for Master Data Services. A super user has access to all functional areas and can add, delete, and update all models.
![image.png](/.attachments/image-3d613e80-bbf2-4098-8de5-5925fa9287a1.png)
1. Select Next to view a summary of the settings for the Master Data Services database. Select Next again to create the database. You'll see the Progress and Finish page.

1. After the database is created and configured, select Finish.
1. On the Database Configuration page in the Master Data Services Configuration Manager, choose Select Database.
1. Select Connect, choose the Master Data Services database and then select OK.
![image.png](/.attachments/image-55ae345f-1962-4625-8921-f25cb5070574.png)
1. In Master Data Services Configuration Manager, select Web Configuration in the left pane.

1. In the Website list box, choose Default Web Site, and then select Create to create a web application.
![image.png](/.attachments/image-9f171f66-9351-4ced-b767-f2b3a49b5ed7.png)
**Note:** If you select Default Web Site, you'll need to separately create a web application. If you choose Create new website in the list box, the application is automatically created.
1. In the Application Pool section, enter a different user name, enter the password, and then select OK.
![image.png](/.attachments/image-f9704ef0-1bc8-4e54-8519-14ada5fbf570.png)
**Note:** Make sure that the user can access the database with the Active Directory Integrated authentication that you recently created. Alternatively, you can change the connection in web.config later.
1. On the Web Configuration pane in the Web application window, select the application you've created, and then choose Select in the Associate Application with Database section.
1. Select Connect and choose the Master Data Services database that you want to associate with the web application. Select OK.
1. You've finished setting up the website. The Web Configuration page now displays the website you selected, web application you created, and the Master Data Services database associated with the application.
![image.png](/.attachments/image-76f6ae24-0468-4c33-afb6-f7d043cd70e0.png)
1. Select Apply. You'll see the Configuration Complete message. Select OK in the message box to launch the web application. The website address is http://server name/web application/.

## Reference article 
[https://docs.microsoft.com/en-us/sql/master-data-services/master-data-services-host-database-on-managed-instance?view=sql-server-ver15](https://docs.microsoft.com/en-us/sql/master-data-services/master-data-services-host-database-on-managed-instance?view=sql-server-ver15)

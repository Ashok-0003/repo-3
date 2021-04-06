[Release Note_6d Billing_V 0.6_03-04-2021.docx](/.attachments/Release%20Note_6d%20Billing_V%200.6_03-04-2021-99b56b57-ce0d-415b-91f8-9ac6f9e9928e.docx)
🔧1.0 What’s New (New delivered user stories)
List out the new user stories that you delivered.
User Story Id (in MSI backlog)	Delivery State (total, partial.)	If Partial list here the remaining	Dependencies	New ETA if partial delivery
NA				
				

List the deferred user stories and ETA:
User Story Id (in MSI backlog)	Dependencies	Reason of postponement	New ETA 
NA			
			

Describe the impact and actions for L1, L2 support 
🚀 2.0 Fixed Defects
2.1 Defect#1 
Defect Description: FN-B2B-Order failed after payment. (Payment is successful, but order got failed due to Data too long for column).
Defect id: 33270.
Current state: Resolved.
ID Defect(Link to MSI backlog)	ID defect in vendor backlog (if already opened)	Delivery State(total fix, partial fix)	Dependencies 	Technical details	Remark
33270
33270
Total Fix	Impacted applications: Billing / API	DB configuration change. Column length of the bundle id is increased. 	Defect is resolved.

Defect#2: 
Defect Description: Status was not getting completed if a order with more than one suborders.
Defect id: This defect is internally identified by 6d team.
Current state: Resolved
ID Defect(Link to MSI backlog)	ID defect in vendor backlog (if already opened)	Delivery State(total fix, partial fix)	Dependencies 	Technical details	Remark
N/A(Internally identified)	N/A (Internally identified)	Total fix	Impacted application: Order Management.	Code Change. When we are having multiple suborders, we are considering the 1st suborder status.	
Code fix is completed.

Defect#3
Defect Description: Email not sending from NG and getting exception.
Defect id: 33786
Current state: Resolved

ID Defect(Link to MSI backlog)	ID defect in vendor backlog (if already opened)	Delivery State(total fix, partial fix)	Dependencies 	Technical details	Remark
33786
33786
Total fix	Impacted application: NG	Code Change. 
Based on MSFT error code(401), NG is setting internal error code. Based on the internal error code, NG will call  OAuth registration API and retry the notification.	Code fix is completed.


Defect#4: 
Defect Description: Invoice should show zero rental subscriptions.
Defect id: This defect is internally identified by 6d team.
Current state: Resolved
ID Defect(Link to MSI backlog)	ID defect in vendor backlog (if already opened)	Delivery State(total fix, partial fix)	Dependencies 	Technical details	Remark
N/A(Internally identified)	N/A (Internally identified)	Total fix	Impacted application: Billing Core.	Code Change. 
Implemented invoice for zero rental subscription	
Code fix is completed.

Defect#5 – Performance testing
Defect Description: Connection Exception from Billing during API Load Testing(Connection got refused in between load run)
Defect id: This defect is internally identified by 6d team.
Current state: Resolved.
ID Defect(Link to MSI backlog)	ID defect in vendor backlog (if already opened)	Delivery State(total fix, partial fix)	Dependencies 	Technical details	Remark
N/A (Internally identified)	N/A (Internally identified)	Total Fix	Impacted applications: Billing application/ DB	Change in connections configured: min pool size 0 and max pool size 40 and Table Indexing have been added to get better TPS 
Code Change	Defect is resolved.


Defect#6 – Performance testing
Defect Description: During API Load testing through JMETER, We observed "Connection is getting refused from OM in between the process
Defect id: This defect is internally identified by 6d team.
Current state: Resolved
ID Defect(Link to MSI backlog)	ID defect in vendor backlog (if already opened)	Delivery State(total fix, partial fix)	Dependencies 	Technical details	Remark
N/A (Internally identified)	N/A (Internally identified)	Total fix	Impacted application: Order Management.	Configuration change and Code Change. Increased max no of connections in property file to 60 .to get better TPS.
	
Code fix is completed.

Defect#7 – Performance testing
Defect Description: During SubmitSubscriptionOrder API and UpdateOrder API with 10Threads ,Rampup10,Loop10 , Seen Lock Exception
Defect id: This defect is internally identified by 6d team.
Current state: Resolved
ID Defect(Link to MSI backlog)	ID defect in vendor backlog (if already opened)	Delivery State(total fix, partial fix)	Dependencies 	Technical details	Remark
N/A (Internally identified)	N/A (Internally identified)	Total fix	Impacted application: Order Management/DB	Code Change. transaction got locked so took more time and table indexing was done.
	
Code fix is completed.

Defect#8 – Performance testing
Defect Description: All OM related APIS taking more time for processing and resulting less TPS.
Defect id: This defect is internally identified by 6d team.
Current state: Resolved.
ID Defect(Link to MSI backlog)	ID defect in vendor backlog (if already opened)	Delivery State(total fix, partial fix)	Dependencies 	Technical details	Remark
N/A (Internally identified)	N/A (Internally identified)	Total fix	Impacted application: Order Management.	Code Change. 
Disabled select query to get connection pool details and to get max seq_id while inserting into tables in property file.	
Code fix is completed.

Defect#9 – Security Testing
Defect Description: Security validation - Web Security Vulnerability - Insecure Direct object reference
Defect id: This defect is internally identified by 6d team.
Current state: Resolved.
ID Defect(Link to MSI backlog)	ID defect in vendor backlog (if already opened)	Delivery State(total fix, partial fix)	Dependencies 	Technical details	Remark
N/A (Internally identified)	N/A (Internally identified)	Total Fix	Impacted applications: 
Enterprise_ui	Code change
Enabled access control check using privilege	Defect is 
resolved.

Defect#10 – Security Testing
Defect Description: Security validation - Web Security Vulnerability - Private IP addresses Disclosed
Defect id: This defect is internally identified by 6d team.
Current state: Resolved
ID Defect(Link to MSI backlog)	ID defect in vendor backlog (if already opened)	Delivery State(total fix, partial fix)	Dependencies 	Technical details	Remark
N/A(Internally identified)	N/A (Internally identified)	Total fix	Impacted application: Enterprise_ui	Code Change. 
Removed the internal IP address from the CSP Response header	Code fix is completed.


Defect#11 – Security Testing
Defect Description: Security validation - Web Security Vulnerability - Multiple SSL vulnerabilities
Defect id: This defect is internally identified by 6d team.
Current state: Resolved

ID Defect(Link to MSI backlog)	ID defect in vendor backlog (if already opened)	Delivery State(total fix, partial fix)	Dependencies 	Technical details	Remark
N/A(Internally identified)	N/A (Internally identified)	Total fix	Impacted application: Enterprise_ui	Code Change. 
Added the SSL configuration in the standalone.xml file	Code fix is completed.

Defect#12 – Security Testing
Defect Description: Security validation - Information disclosure through Error messages
Defect id: This defect is internally identified by 6d team.
Current state: Resolved

ID Defect(Link to MSI backlog)	ID defect in vendor backlog (if already opened)	Delivery State(total fix, partial fix)	Dependencies 	Technical details	Remark
N/A(Internally identified)	N/A (Internally identified)	Total fix	Impacted application: Enterprise_ui	Code Change. 
Started showing generic error message for different error codes	
Code fix is completed.

Defect#13 – Security Testing
Defect Description: Security validation - Web Security Vulnerability - Host Header Injection
Defect id: This defect is internally identified by 6d team.
Current state: Resolved
ID Defect(Link to MSI backlog)	ID defect in vendor backlog (if already opened)	Delivery State(total fix, partial fix)	Dependencies 	Technical details	Remark
N/A(Internally identified)	N/A (Internally identified)	Total fix	Impacted application: Enterprise_ui	Code Change. 
Introduced host header validation	
Code fix is completed.


Defect#14 – Security Testing
Defect Description: Security validation - Improper implementation of content-security policy header
Defect id: This defect is internally identified by 6d team.
Current state: Resolved.
ID Defect(Link to MSI backlog)	ID defect in vendor backlog (if already opened)	Delivery State(total fix, partial fix)	Dependencies 	Technical details	Remark
N/A (Internally identified)	N/A (Internally identified)	Total Fix	Impacted applications: 
Retail Portal	Code change
IP address is not disclosed in policy header	Defect is 
resolved.

Defect#15 – Security Testing
Defect Description: Security validation - Multiple SSL vulnerabilities
Defect id: This defect is internally identified by 6d team.
Current state: Resolved
ID Defect(Link to MSI backlog)	ID defect in vendor backlog (if already opened)	Delivery State(total fix, partial fix)	Dependencies 	Technical details	Remark
N/A(Internally identified)	N/A (Internally identified)	Total fix	Impacted application: Retail Portal	Code Change. 
Enabled latest version of SSL 	
Code fix is completed.


Defect#16 – Security Testing
Defect Description: Security validation - Private IP addresses Disclosed
Defect id: This defect is internally identified by 6d team.
Current state: Resolved

ID Defect(Link to MSI backlog)	ID defect in vendor backlog (if already opened)	Delivery State(total fix, partial fix)	Dependencies 	Technical details	Remark
N/A(Internally identified)	N/A (Internally identified)	Total fix	Impacted application: Retail Portal	Code Change. 
Ensured IP addresses are not disclosed.	
Code fix is completed.

Defect#17 
Defect Description: [6D API Schema Mismatch]Incorrect Mapping of columns in View Consumption Data Grid
Defect id: 33692
Current state: Resolved
ID Defect

33692
	ID defect in vendor backlog 
33692
Delivery State(total fix, partial fix)	Dependencies 	Technical details	Remark
		Total fix	Impacted application: Report module	Code Change. 
Column order is revised	
Code fix is completed.


Defect#18 
Defect Description: Invoice Presentation Issue (rentals name, cdr header name)
Defect id: This defect is internally identified by 6d team.
Current state: Resolved

ID Defect(Link to MSI backlog)	ID defect in vendor backlog (if already opened)	Delivery State(total fix, partial fix)	Dependencies 	Technical details	Remark
N/A(Internally identified)	N/A (Internally identified)	Total fix	Impacted application: Billing	Code Change. Increased the width of Names(plan&header)	
Code fix is completed.


Defect#19 – Security Testing
Defect Description: Security validation - API Security Vulnerability - Improper input validation (Low)
Defect id: This defect is internally identified by 6d team.
Current state: Resolved.
ID Defect(Link to MSI backlog)	ID defect in vendor backlog (if already opened)	Delivery State(total fix, partial fix)	Dependencies 	Technical details	Remark
N/A (Internally identified)	N/A (Internally identified)	Total Fix	Impacted applications: 
Billing 	Code change
Validated the input parameter.	Defect is 
resolved.

Defect#20 – Security Testing
Defect Description: Security validation - API Security Vulnerability - Information disclosure through Error messages
Defect id: This defect is internally identified by 6d team.
Current state: Resolved.
ID Defect(Link to MSI backlog)	ID defect in vendor backlog (if already opened)	Delivery State(total fix, partial fix)	Dependencies 	Technical details	Remark
N/A (Internally identified)	N/A (Internally identified)	Total Fix	Impacted applications: 
Billing 	Code change
Validated the input parameter.	Defect is 
resolved.

Defect#21 – Security Testing
Defect Description: Private IP addresses Disclosed
Defect id: This defect is internally identified by 6d team.
Current state: Resolved.
ID Defect(Link to MSI backlog)	ID defect in vendor backlog (if already opened)	Delivery State(total fix, partial fix)	Dependencies 	Technical details	Remark
N/A (Internally identified)	N/A (Internally identified)	Total Fix	Impacted applications: 
Enterprise_ui	Code change
Disabled the private ip disclosed in the internal level	Defect is 
resolved.

Defect#22 – Security Testing
Defect Description: Security validation - Web Security Vulnerability - Host Header Injection
Defect id: This defect is internally identified by 6d team.
Current state: Resolved
ID Defect(Link to MSI backlog)	ID defect in vendor backlog (if already opened)	Delivery State(total fix, partial fix)	Dependencies 	Technical details	Remark
N/A(Internally identified)	N/A (Internally identified)	Total fix	Impacted application: Enterprise_ui	Code Change. 
Removed the host header injection address from the response	
Defect is resolved.


Defect#23 – Security Testing
Defect Description: Security validation - Information disclosure through Error messages
Defect id: This defect is internally identified by 6d team.
Current state: Resolved

ID Defect(Link to MSI backlog)	ID defect in vendor backlog (if already opened)	Delivery State(total fix, partial fix)	Dependencies 	Technical details	Remark
N/A(Internally identified)	N/A (Internally identified)	Total fix	Impacted application: Enterprise_ui	Code Change. 
Added validation for security validation in code level and disclosed error message	
Code fix is completed.

Defect#24 – Performance testing
Defect Description: Internal Server Error from OM logs
Defect id: This defect is internally identified by 6d team.
Current state: Resolved.
ID Defect(Link to MSI backlog)	ID defect in vendor backlog (if already opened)	Delivery State(total fix, partial fix)	Dependencies 	Technical details	Remark
N/A (Internally identified)	N/A (Internally identified)	Total fix	Impacted application: SM and Billing	Code Change. 
connection count increased for Billing and SM proxy url .	
Code fix is completed.

Defect#25 – Performance testing
Defect Description: 
1) optimizations to make DB insert faster and incoming 2) final response log printing logic changes 3)passthrough api added unique txn id. 
Defect id: This defect is internally identified by 6d team.
Current state: Resolved.
ID Defect(Link to MSI backlog)	ID defect in vendor backlog (if already opened)	Delivery State(total fix, partial fix)	Dependencies 	Technical details	Remark
N/A (Internally identified)	N/A (Internally identified)	Total fix	Impacted application: COM	Code Change. 
Modified the table Foreign key & sequence generator logic changed.	
Code fix is completed.


Defect#26 
Defect Description: ITSM stage getting completed if we try update order status even if other stages are failed.
Defect id: This defect is internally identified by 6d team.
Current state: Resolved
ID Defect(Link to MSI backlog)	ID defect in vendor backlog (if already opened)	Delivery State(total fix, partial fix)	Dependencies 	Technical details	Remark
N/A(Internally identified)	N/A (Internally identified)	Total fix	Impacted application: COM	Code Change. 
validation for Update Order is enabled	
Code fix is completed.

Defect#27
Defect Description: Benefit Reset is not happening after subscription renewal.
Defect id: This defect is internally identified by 6d team.
Current state: Resolved
ID Defect(Link to MSI backlog)	ID defect in vendor backlog (if already opened)	Delivery State(total fix, partial fix)	Dependencies 	Technical details	Remark
N/A(Internally identified)	N/A (Internally identified)	Total fix	Impacted application: 
SM	Configuration change. Resetting the Benefits based on the Boolean.
	
Code fix is completed.

Defect#28
Defect Description: Refund for cancel subscription from SM getting error from OM
Defect id: This defect is internally identified by 6d team.
Current state: Resolved
ID Defect(Link to MSI backlog)	ID defect in vendor backlog (if already opened)	Delivery State(total fix, partial fix)	Dependencies 	Technical details	Remark
N/A(Internally identified)	N/A (Internally identified)	Total fix	Impacted application: 
SM	Configuration change. Corrected OM request packet. 
	
Code fix is completed.

Defect#29
Defect Description: NG needs service_provider_name for configuring email template
Defect id: This defect is internally identified by 6d team.
Current state: Resolved
ID Defect(Link to MSI backlog)	ID defect in vendor backlog (if already opened)	Delivery State(total fix, partial fix)	Dependencies 	Technical details	Remark
N/A(Internally identified)	N/A (Internally identified)	Total fix	Impacted application: 
SM	Configuration change. Populated service provider name in the Query package API response. 
	
Code fix is completed.

User story #-17692
Need to deploy code for the User story for “ As a Billing Platform , when the product configuration is updated in the Portal by ITSM manually ,notification to be sent to the Service Consumer/Provider”

Defect#30 – Performance testing
Defect Description:  Expected request were not achieved in API gateway.
Defect id: This defect is internally identified by 6d team.
Current state: Resolved.
ID Defect(Link to MSI backlog)	ID defect in vendor backlog (if already opened)	Delivery State(total fix, partial fix)	Dependencies 	Technical details	Remark
N/A (Internally identified)	N/A (Internally identified)	Total fix	Impacted application: COM	Config Change. Thread(request) count number was increased.
	
Defect is completed.

Defect#31 
Defect Description:  Failure case handling for Add subscription.
Defect id: This defect is internally identified by 6d team.
Current state: Resolved.
ID Defect(Link to MSI backlog)	ID defect in vendor backlog (if already opened)	Delivery State(total fix, partial fix)	Dependencies 	Technical details	Remark
N/A (Internally identified)	N/A (Internally identified)	Total fix	Impacted application: Billing, COM	Code Change. Service creation internally handled by billing. Instead of update service state, used update account state. 	
Defect is completed.


Defect#32
Defect Description:  ProfileCreation failed at Billing for Arabic profile
Defect id: This defect is internally identified by 6d team.
Current state: Resolved.
ID Defect(Link to MSI backlog)	ID defect in vendor backlog (if already opened)	Delivery State(total fix, partial fix)	Dependencies 	Technical details	Remark
N/A (Internally identified)	N/A (Internally identified)	Total fix	Impacted application: Billing, COM	Code Change. First /last name are mandatory only for English. For Arabic, made first_name_ol and last_name_ol are mandatory.	
Defect is completed.

Defect#33
Defect Description:  COM need to pass service provider name passed by SM to NG
Defect id: This defect is internally identified by 6d team.
Current state: Resolved.
ID Defect(Link to MSI backlog)	ID defect in vendor backlog (if already opened)	Delivery State(total fix, partial fix)	Dependencies 	Technical details	Remark
N/A (Internally identified)	N/A (Internally identified)	Total fix	Impacted application: COM	Code Change.  In Query package API, ‘createdByName’ tag is mapped as service provider name towards NG	
Defect is completed.


Defect#34
Defect Description:  [APIGW] Accept new key standardUnit in the plan synch request from event grid and pass it down to SM
Defect id: This defect is internally identified by 6d team.
Current state: Resolved.
ID Defect(Link to MSI backlog)	ID defect in vendor backlog (if already opened)	Delivery State(total fix, partial fix)	Dependencies 	Technical details	Remark
N/A (Internally identified)	N/A (Internally identified)	Total fix	Impacted application: APIGW	Code Change. standardUnit value under planBenefits to be mapped to accountUnitType inside activationBenefit towards SM 	
Defect is completed.

Defect#35
Defect Description:  In PlanSync Request, Event grid is passing 'StandardUnit=Count' to API GW, but API GW in turn passing unit type as API Calls to SM 
Defect id: This defect is internally identified by 6d team.
Current state: Resolved.
ID Defect(Link to MSI backlog)	ID defect in vendor backlog (if already opened)	Delivery State(total fix, partial fix)	Dependencies 	Technical details	Remark
N/A (Internally identified)	N/A (Internally identified)	Total fix	Impacted application: APIGW	Code Change.  standardUnit value under tariffs to be mapped to UnitType inside tariffList towards SM	
Defect is completed.


Defect#36
Defect Description:  Notification audit issue.
Defect id: This defect is internally identified by 6d team.
Current state: Resolved.
ID Defect(Link to MSI backlog)	ID defect in vendor backlog (if already opened)	Delivery State(total fix, partial fix)	Dependencies 	Technical details	Remark
N/A (Internally identified)	N/A (Internally identified)	Total fix	Impacted application: NG/Mo_router	Config/Code Change.  url configured.adaptor level response part changed.	
Defect is completed.


Defect#37 – Performance Testing
Defect Description:  Notification going twice for cancel subscription.
Defect id: This defect is internally identified by 6d team.
Current state: Resolved.
ID Defect(Link to MSI backlog)	ID defect in vendor backlog (if already opened)	Delivery State(total fix, partial fix)	Dependencies 	Technical details	Remark
N/A (Internally identified)	N/A (Internally identified)	Total fix	Impacted application: COM	Config Change.  Table update.	
Defect is completed.

Defect#38 – Performance testing
Defect Description:  Request Id is not printing in Billing logs
Defect id: This defect is internally identified by 6d team.
Current state: Resolved.
ID Defect(Link to MSI backlog)	ID defect in vendor backlog (if already opened)	Delivery State(total fix, partial fix)	Dependencies 	Technical details	Remark
N/A (Internally identified)	N/A (Internally identified)	Total fix	Impacted application: Billing	Config Change.  Table update.	
Defect is completed.


Defect#39– Performance testing
Defect Description: Billing took more time in case of Make Payment API during Spike testing.
Defect id: This defect is internally identified by 6d team.
Current state: Resolved.
ID Defect(Link to MSI backlog)	ID defect in vendor backlog (if already opened)	Delivery State(total fix, partial fix)	Dependencies 	Technical details	Remark
N/A (Internally identified)	N/A (Internally identified)	Total fix	Impacted application: Billing	Code Change
Optimization done  to increase TPS.	
Code fix is completed.

Defect#40
Defect Description: Some of the fields are coming in English while we generating Arabic invoice.
Defect id: This defect is internally identified by 6d team.
Current state: Resolved.
ID Defect(Link to MSI backlog)	ID defect in vendor backlog (if already opened)	Delivery State(total fix, partial fix)	Dependencies 	Technical details	Remark
N/A (Internally identified)	N/A (Internally identified)	Total fix	Impacted application: Billing	Configuration Change
DB configuration.	
Fix is completed.


Defect#41– Performance testing
Defect Description: Request Id is not printing in Billing logs.
For DownloadInvoice API corresponding Apigateway transaction request-id is not printing in Billing logs.
Defect id: This defect is internally identified by 6d team.
Current state: Resolved.
ID Defect(Link to MSI backlog)	ID defect in vendor backlog (if already opened)	Delivery State(total fix, partial fix)	Dependencies 	Technical details	Remark
N/A (Internally identified)	N/A (Internally identified)	Total fix	Impacted application: Billing	Code Change
Code change to print request id in billing logs.	
Code fix is completed.

Defect#42– Performance testing
Defect Description: GetCreditManagmentDetails-Received less TPS during capacity testing
Defect id: This defect is internally identified by 6d team.
Current state: Resolved.
ID Defect(Link to MSI backlog)	ID defect in vendor backlog (if already opened)	Delivery State(total fix, partial fix)	Dependencies 	Technical details	Remark
N/A (Internally identified)	N/A (Internally identified)	Total fix	Impacted application: COM,SM	Code Change
Code change and DB queries for optimization.	
Code fix is completed.

Defect#43– Performance testing
Defect Description: Threads are getting blocked during SPIKE Testing. 
Defect id: This defect is internally identified by 6d team.
Current state: Resolved.
ID Defect(Link to MSI backlog)	ID defect in vendor backlog (if already opened)	Delivery State(total fix, partial fix)	Dependencies 	Technical details	Remark
N/A (Internally identified)	N/A (Internally identified)	Total fix	Impacted application: COM	Code Change/Configuration change.
Framework Logic has been changed.	
Code fix is completed.


Defect#44
Defect Description:  FN-B2C- Description and Vendor details are not shown in order screen after order is created.
Defect id: 34540.
Current state: Resolved.
ID Defect(Link to MSI backlog)	ID defect in vendor backlog (if already opened)	Delivery State(total fix, partial fix)	Dependencies 	Technical details	Remark
34540
34540
Total Fix	Impacted applications: COM	Configuration change. updated the DB queries for Order Description	Defect is resolved.


Defect#45
Defect Description:  SIT- Bugs raised due to 6D APIs rendering unexpected response code to front End.
Defect id: 33949
Current state: Resolved.
ID Defect(Link to MSI backlog)	ID defect in vendor backlog (if already opened)	Delivery State(total fix, partial fix)	Dependencies 	Technical details	Remark
33949
33949
Total Fix	Impacted applications: COM 	Configuration change. Code developed. 	Defect is resolved.

Defect#46
Defect Description:  FN-Portal-Unable to see the  Maximum daily spend option on Subscription Details page.
Defect id: 34362
Current state: Resolved.
ID Defect(Link to MSI backlog)	ID defect in vendor backlog (if already opened)	Delivery State(total fix, partial fix)	Dependencies 	Technical details	Remark
34362
34362
Total Fix	Impacted applications: COM 	Configuration change. Code developed. 	Defect is resolved.


Defect#47– Performance testing
Defect Description: During Spike testing, Create Adjustment API received(9.5TPS) less than targeted TPS.. 
Defect id: This defect is internally identified by 6d team.
Current state: Resolved.
ID Defect(Link to MSI backlog)	ID defect in vendor backlog (if already opened)	Delivery State(total fix, partial fix)	Dependencies 	Technical details	Remark
N/A (Internally identified)	N/A (Internally identified)	Total fix	Impacted application: COM	Code Change.
	
Code fix is completed.

Defect#48
Defect Description: Cancel subscription showing pending instead of fail
Defect id: This defect is internally identified by 6d team.
Current state: Resolved.
ID Defect(Link to MSI backlog)	ID defect in vendor backlog (if already opened)	Delivery State(total fix, partial fix)	Dependencies 	Technical details	Remark
N/A (Internally identified)	N/A (Internally identified)	Total fix	Impacted application: COM	Code Change.
	
Code fix is completed.

Defect#49
Defect Description: View subscription having exception.
Defect id: This defect is internally identified by 6d team.
Current state: Resolved.
ID Defect(Link to MSI backlog)	ID defect in vendor backlog (if already opened)	Delivery State(total fix, partial fix)	Dependencies 	Technical details	Remark
N/A (Internally identified)	N/A (Internally identified)	Total fix	Impacted application: COM	Code Change.
	
Code fix is completed.

Defect#50
Defect Description: In View subscription com not sending status filter parameter to sm.
Defect id: This defect is internally identified by 6d team.
Current state: Resolved.
ID Defect(Link to MSI backlog)	ID defect in vendor backlog (if already opened)	Delivery State(total fix, partial fix)	Dependencies 	Technical details	Remark
N/A (Internally identified)	N/A (Internally identified)	Total fix	Impacted application: COM	Code Change.
	
Code fix is completed.

Defect#51
Defect Description:   Bill conforms, Billing to OM status change API is wrong.

Defect id: This defect is internally identified by 6d team.
Current state: Resolved.
ID Defect(Link to MSI backlog)	ID defect in vendor backlog (if already opened)	Delivery State(total fix, partial fix)	Dependencies 	Technical details	Remark
N/A (Internally identified)	N/A (Internally identified)	Total Fix	Impacted applications: Billing/BillingCore	Code change: 
Changed Billing to om status change api. Previously calling wrong api ( lifecycle change api) for billing status change. 	Defect is resolved.

Defect#52
Defect Description:   Some of the fields are coming in English while we are generating Arabic invoice

Defect id: This defect is internally identified by 6d team.
Current state: Resolved.
ID Defect(Link to MSI backlog)	ID defect in vendor backlog (if already opened)	Delivery State(total fix, partial fix)	Dependencies 	Technical details	Remark
N/A (Internally identified)	N/A (Internally identified)	Total Fix	Impacted applications: Billing/BillingCore	Code change: code changes done for pick the values in call_type_name_ol
Configuration change. updated the DB queries for  support Arabic values
  	Defect is resolved.

Defect#53
Defect Description:  performance changes for view subscription .
Defect id: This defect is internally identified by 6d team.
Current state: Resolved.
ID Defect(Link to MSI backlog)	ID defect in vendor backlog (if already opened)	Delivery State(total fix, partial fix)	Dependencies 	Technical details	Remark
N/A (Internally identified)	N/A (Internally identified)	Total Fix	Impacted applications: Billing/BillingAPI	Code change:  
  property query changed to native query.
Configuration change. updated the DB queries for indexing

	Defect is resolved.

Defect#54
Defect Description:    performance testing for download invoice and viewsubscriotions.
Defect id: This defect is internally identified by 6d team.
Current state: Resolved.
ID Defect(Link to MSI backlog)	ID defect in vendor backlog (if already opened)	Delivery State(total fix, partial fix)	Dependencies 	Technical details	Remark
N/A (Internally identified)	N/A (Internally identified)	Total Fix	Impacted applications: Billing/BillingAPI	Code change:  
changed one session part for optimization

Configuration change. updated the DB queries for indexing
  	Defect is resolved.



2.3 Differed open Defects.
List the defect fixes that could not be completed and fixed in the current release
Defect ID(in MSI Backlog)	ID defect in vendor backlog (if already opened)	Description	Technical details	Reason of postponement	New ETA
					
					

⭐ 3.0 Improvements
List out all improvements that you've made to your product.





💻 4.0 Reviewers 

Prepared By	Implementation team
Company name	6d Technologies
Reviewed by 	Elango Periasami
Approved by 	


[Release Note_6d Billing_V 1.6_22-05-2021.docx](/.attachments/Release%20Note_6d%20Billing_V%201.6_22-05-2021-1b77ed0f-e8e6-481b-a3e3-ca5b7535be77.docx)


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
Defect Description:    performance testing for download invoice and view subscriptions.
Defect id: This defect is internally identified by 6d team.
Current state: Resolved.
ID Defect(Link to MSI backlog)	ID defect in vendor backlog (if already opened)	Delivery State(total fix, partial fix)	Dependencies 	Technical details	Remark
N/A (Internally identified)	N/A (Internally identified)	Total Fix	Impacted applications: Billing/BillingAPI	Code change:  
changed one session part for optimization

Configuration change. updated the DB queries for indexing
  	Defect is resolved.

Defect#55
Defect Description: FN - My TASMU Portal - My Smart Services screen keeps loading
Defect id:34769
Current state:
ID Defect(Link to MSI backlog)	ID defect in vendor backlog (if already opened)	Delivery State(total fix, partial fix)	Dependencies 	Technical details	Remark
34769
34769
Total Fix	Impacted applications: Billing 	Code change
	Issue is fixed

Defect#56
Defect Description: Subscription Type is not shown in Subscriptions page
Defect id: 34842
Current state: Resolved
ID Defect(Link to MSI backlog)	ID defect in vendor backlog (if already opened)	Delivery State(total fix, partial fix)	Dependencies 	Technical details	Remark
34842
34842
Total fix	Impacted application: 
Billing	Code change	Issue is fixed.


Defect#57 
Defect Description: Onboarding Failure
Defect id: This defect is internally identified by 6d team.
Current state: Resolved.
ID Defect(Link to MSI backlog)	ID defect in vendor backlog (if already opened)	Delivery State(total fix, partial fix)	Dependencies 	Technical details	Remark
N/A (Internally identified)	N/A (Internally identified)	Total fix	Impacted application: COM	Configuration change. Updated the DB queries
	
Issue is fixed.

Defect#58
Defect Description: Onboarding Failure
Defect id: This defect is internally identified by 6d team.
Current state: Resolved.
ID Defect(Link to MSI backlog)	ID defect in vendor backlog (if already opened)	Delivery State(total fix, partial fix)	Dependencies 	Technical details	Remark
N/A (Internally identified)	N/A (Internally identified)	Total fix	Impacted application: COM	DB Configuration change.
	
Issue is fixed.

Defect#59
Defect Description: In admin portal addon page subscriptions are not showing
Defect id: This defect is internally identified by 6d team.
Current state: Resolved.
ID Defect(Link to MSI backlog)	ID defect in vendor backlog (if already opened)	Delivery State(total fix, partial fix)	Dependencies 	Technical details	Remark
N/A (Internally identified)	N/A (Internally identified)	Total fix	Impacted application: Retail CRM portal	Configuration change. DB change.
	
Issue is fixed.

Defect#60
Defect Description: FN-SMS/Email-SMS and Email received after invoice generation are not readable. 
Defect id: 34650
Current state: Resolved
ID Defect(Link to MSI backlog)	ID defect in vendor backlog (if already opened)	Delivery State(total fix, partial fix)	Dependencies 	Technical details	Remark
34650
34650
Total fix	Impacted application: 
NG	Code change	Issue is fixed.

Defect#61
Defect Description: FN-B2B/B2C- Product/Service Name should be displayed in Orders Page
Defect id:  34145
Current state: Resolved
ID Defect(Link to MSI backlog)	ID defect in vendor backlog (if already opened)	Delivery State(total fix, partial fix)	Dependencies 	Technical details	Remark
34145
34145
Total fix	Impacted application: 
COM	Configuration change	Deployed in preprod/UAT. Msft should send the tag . pls refer the ADO comment.

Defect#62
Defect Description: Implement OAuth at all 6d APIs
Defect id:  34486
Current state: Resolved – please refer ADO comment.
ID Defect(Link to MSI backlog)	ID defect in vendor backlog (if already opened)	Delivery State(total fix, partial fix)	Dependencies 	Technical details	Remark
34486
34486
Total fix	Impacted application: 
COM	Code change	Deployed in preprod/UAT.

Defect#63
Defect Description: Billing system is not supporting YYYY-MM-DDTHH:mm:ss.sssZ this date format.
Defect id: This defect is internally identified by 6d team.
Current state: Resolved.
ID Defect(Link to MSI backlog)	ID defect in vendor backlog (if already opened)	Delivery State(total fix, partial fix)	Dependencies 	Technical details	Remark
N/A (Internally identified)	N/A (Internally identified)	Total fix	Impacted application: 
Billing	Code change	Issue is fixed.

Defect#64
Defect Description: Benefit counter not available in SM.
Defect id:  Internally identified.
Current state: Resolved.
ID Defect(Link to MSI backlog)	ID defect in vendor backlog (if already opened)	Delivery State(total fix, partial fix)	Dependencies 	Technical details	Remark
N/A as internally identified bug	N/A as internally identified bug	Total fix	Impacted application: 
SM	Code change	Fixed.

Defect#65
Defect Description: Cancel subscription call is needed for auto renewal=false case. Trigger to ITSM has to be invoke for this scenario.
Defect id:  Internally identified.
Current state: Resolved 
ID Defect(Link to MSI backlog)	ID defect in vendor backlog (if already opened)	Delivery State(total fix, partial fix)	Dependencies 	Technical details	Remark
N/A as internally identified bug	N/A as internally identified bug	Total fix	Impacted application: 
SM	Code change	Fixed.


Defect#66
Defect Description: FN-Billing Portal-Newly created profile are pending [SM ADD subscriber pending]
Defect id:  34972
Current state: Resolved – please refer ADO comment.
ID Defect(Link to MSI backlog)	ID defect in vendor backlog (if already opened)	Delivery State(total fix, partial fix)	Dependencies 	Technical details	Remark
34972
34972
Total fix	Impacted application: 
COM	Configuration change	Fixed.

Defect#67
Defect Description: 
[BIL][Charge Frequency and Charge Factor]  As a Billing system, I want to support monthly invoice cycle  for a billing account with Subscriptions having varying charge frequency (Daily, Weekly, Monthly, Yearly) and charge factor.
Current state: Resolved.
ID Defect(Link to MSI backlog)	ID defect in vendor backlog (if already opened)	Delivery State(total fix, partial fix)	Dependencies 	Technical details	Remark
Not applicable	Not applicable	Total fix	Impacted application: 
Billing	For a billing account with Subscriptions having varying charge frequency (Daily, Weekly, Monthly, Yearly) and charge factor.	Fixed.


User story:  #68
Defect Description: FN-Billing Portal-Newly created profile are pending [SM ADD subscriber pending]
Defect id:  14249
Current state: Resolved
ID Defect(Link to MSI backlog)	ID defect in vendor backlog (if already opened)	Delivery State(total fix, partial fix)	Dependencies 	Technical details	Remark
14249
14249
Total fix	Impacted application: 
COM	New development	Resolved

Defect#69
Defect Description: Order status is completed but still some stages are pending in suborder 
Defect id:  Internally identified.
Current state: Resolved 
ID Defect(Link to MSI backlog)	ID defect in vendor backlog (if already opened)	Delivery State(total fix, partial fix)	Dependencies 	Technical details	Remark
N/A as internally identified bug	N/A as internally identified bug	Total fix	Impacted application: 
COM	Code change	Resolved.

Defect/New enhancement #70
Defect Description: Billing Solution Notifications- Content Approvals
Defect id:  20313
Current state: Resolved
ID Defect(Link to MSI backlog)	ID defect in vendor backlog (if already opened)	Delivery State(total fix, partial fix)	Dependencies 	Technical details	Remark
20313
20313
Total fix	Impacted application: 
Billing/SM	Configuration change	Resolved



Defect #71
Defect Description: FN-Billing Portal-Newly created profile are pending for approval on billing side hence unable to complete any order
Defect id: 34972
Current state: Resolved
ID Defect(Link to MSI backlog)	ID defect in vendor backlog (if already opened)	Delivery State(total fix, partial fix)	Dependencies 	Technical details	Remark
34972
34972
Total fix	Impacted application: 
COM	Configuration change	Resolved

Defect #72
Defect Description: FN-Billing Portal-When Account status is changed from Suspend to Active, notifications are not triggered
Defect id: 34963
Current state: Resolved
ID Defect(Link to MSI backlog)	ID defect in vendor backlog (if already opened)	Delivery State(total fix, partial fix)	Dependencies 	Technical details	Remark
34963
34963
Total fix	Impacted application: 
COM	Configuration change	Resolved

Issue/New enhancement #73
Defect Description: As Billing system [COM module] , once the synchronous response is received from ITSM , Billing need to trigger an email to configured one or many ids
Current state: Resolved
ID Defect(Link to MSI backlog)	ID defect in vendor backlog (if already opened)	Delivery State(total fix, partial fix)	Dependencies 	Technical details	Remark
N/A	N/A	Total fix	Impacted application: 
COM	This is new requirement and code change.	Resolved

Issue/New enhancement #74
Defect Description: As Billing system [NG module] , I want to support sending multiple email ids to MSFT Notification API so that COM module can trigger an email to configured one or many ids , once the synchronous response is received from ITSM. 
Current state: Resolved
ID Defect(Link to MSI backlog)	ID defect in vendor backlog (if already opened)	Delivery State(total fix, partial fix)	Dependencies 	Technical details	Remark
N/A	N/A	Total fix	Impacted application: 
NG	This is new requirement and code change.	Resolved

Defect#75
Defect Description: Billing Portal not loading 
Defect id:  Internally identified.
Current state: Resolved 
ID Defect(Link to MSI backlog)	ID defect in vendor backlog (if already opened)	Delivery State(total fix, partial fix)	Dependencies 	Technical details	Remark
N/A as internally identified bug	N/A as internally identified bug	Total fix	Impacted application: 
Retail Portal	Environment Issue.	Resolved.

Defect#76
Defect Description: Subscription is automatically terminating in the grace period after renewal call. 
Defect id:  Internally identified.
Current state: Resolved 
ID Defect(Link to MSI backlog)	ID defect in vendor backlog (if already opened)	Delivery State(total fix, partial fix)	Dependencies 	Technical details	Remark
N/A as internally identified bug	N/A as internally identified bug	Total fix	Impacted application: 
SM	Code Change.	Resolved.

Defect/New change #77
Defect Description: As Billing system [COM module] , Cancel Subscription request to ITSM  should include the system attribute values received on update order status  while "add subscription". 
Defect id:  Internally identified.
Current state: Resolved 
ID Defect(Link to MSI backlog)	ID defect in vendor backlog (if already opened)	Delivery State(total fix, partial fix)	Dependencies 	Technical details	Remark
N/A as internally identified bug	N/A as internally identified bug	Total fix	Impacted application: 
OM	New Change.	Resolved.

Defect #78
Defect Description: FN-Billing Portal-When Account status is changed from Suspend to Active, notifications are not triggered
Defect id: 35503
Current state: Resolved
ID Defect(Link to MSI backlog)	ID defect in vendor backlog (if already opened)	Delivery State(total fix, partial fix)	Dependencies 	Technical details	Remark
35503
35503
Total fix	Impacted application: 
Retail Portal	Code change	Resolved


Defect #79
Defect Description:  For a specific plan, we could see that tariffs are attached incorrectly. We have got a total of 9 ppu pulse for a tariff which is not required.
Current state: Resolved
ID Defect(Link to MSI backlog)	ID defect in vendor backlog (if already opened)	Delivery State(total fix, partial fix)	Dependencies 	Technical details	Remark
N/A (Internally identified)	N/A (Internally identified)	Total fix	Impacted application: 
APIGW	Code change.
Tariff is attached properly for that specific plan	Resolved

Defect #80
Defect Description: After Renewal got failed and status moved to G, data is inserting in RenewalSuccessCount, LastRenewalSuccessDate and ChargeAmount.
Current state: Resolved.
ID Defect(Link to MSI backlog)	ID defect in vendor backlog (if already opened)	Delivery State(total fix, partial fix)	Dependencies 	Technical details	Remark
N/A (Internally identified)	N/A (Internally identified)	Total Fix	Impacted applications: SM	Code change: 
We are increasing RenewalFailureCount and updating LastRenewalFailureDate  if renewal got failed
	Defect is resolved.

Defect #81 
Defect Description: Cancel subscription call is needed for auto renewal=false case. Trigger to ITSM has to be invoke for this scenario.
Current state: Resolved.
ID Defect (Link to MSI backlog)	ID defect in vendor backlog (if already opened)	Delivery State (total fix, partial fix)	Dependencies 	Technical details	Remark
N/A (Internally identified)	N/A (Internally identified)	Total Fix	Impacted applications: SM	Code change: 
After calling OM for cancel subscription we are keeping subscription in intermediate status as P 
	Defect is resolved.

Defect #82
Defect Description: Dunning is sending wrong outstanding and due date to NG.
Defect id: 35727
Current state: Resolved.
ID Defect (Link to MSI backlog)	ID defect in vendor backlog (if already opened)	Delivery State (total fix, partial fix)	Dependencies 	Technical details	Remark
35727
35727
Total Fix	Impacted applications: Billing	Code change.
	Defect is resolved.

Defect #83
Defect Description: No Details is shown in order screen for cancelled subscription order request.
Defect id: 35779
Current state: Resolved.
ID Defect (Link to MSI backlog)	ID defect in vendor backlog (if already opened)	Delivery State (total fix, partial fix)	Dependencies 	Technical details	Remark
35779
35779
Total Fix	Impacted applications: COM	Configuration change.
	Defect is resolved.

Defect #84
Defect Description: FN-Notification-Plan name is not mentioned in Renewal Failed notification.
Defect id: 35909
Current state: Resolved.
ID Defect (Link to MSI backlog)	ID defect in vendor backlog (if already opened)	Delivery State (total fix, partial fix)	Dependencies 	Technical details	Remark

35909

35909
Total Fix	Impacted applications: SM	Code change.
	Defect is resolved.

Defect #85
Defect Description: Invoice generated is not as per template.
Defect id:  35887
Current state: Resolved.
ID Defect (Link to MSI backlog)	ID defect in vendor backlog (if already opened)	Delivery State (total fix, partial fix)	Dependencies 	Technical details	Remark
35887
35887
Total Fix	Impacted applications: Billing	Code change.
	Defect is resolved.

Defect #86
Defect Description: FN-Billing Portal-Subscriptions are stuck in Grace State.
Defect id: 35879
Current state: Resolved.
ID Defect (Link to MSI backlog)	ID defect in vendor backlog (if already opened)	Delivery State (total fix, partial fix)	Dependencies 	Technical details	Remark

35879

35879
Total Fix	Impacted applications: SM	Code change.
	Defect is resolved.

New Enhancement #87
Defect Description: Schedule a JIT invoice and Book service fee.
Defect id: NA
Current state: Developed.
ID Defect (Link to MSI backlog)	ID defect in vendor backlog (if already opened)	Delivery State (total fix, partial fix)	Dependencies 	Technical details	Remark
N/A 	N/A 	Total Fix	Impacted applications: Billing	Code change.
	

New Enhancement #88
Defect Description: [Invoice Template enhancement] Separate images must be configurable for English Invoice and Arabic Invoice

Defect id: NA
Current state: Developed.
ID Defect (Link to MSI backlog)	ID defect in vendor backlog (if already opened)	Delivery State (total fix, partial fix)	Dependencies 	Technical details	Remark
N/A
	N/A 
	Total Fix	Impacted applications: 
Billing	Code change.
	

New Enhancement #89
Defect Description: API centric New enhancement.

Defect id: NA
Current state: Developed.
ID Defect (Link to MSI backlog)	ID defect in vendor backlog (if already opened)	Delivery State (total fix, partial fix)	Dependencies 	Technical details	Remark
N/A 	N/A 
	Total Fix	Impacted applications: 
Mediation processor,CGW	Code change.
	


Defect #90
Defect Description: Subject field in the notification messages are in should be in Arabic language.
Defect id:  36007
Current state: Resolved.
ID Defect (Link to MSI backlog)	ID defect in vendor backlog (if already opened)	Delivery State (total fix, partial fix)	Dependencies 	Technical details	Remark
36007
36007
Total Fix	Impacted applications: Billing	Code change.
	Defect is resolved.

Defect #91
Defect Description: Email is received instead of SMS on paying invoice dues.
Defect id:  35952
Current state: Resolved.
ID Defect (Link to MSI backlog)	ID defect in vendor backlog (if already opened)	Delivery State (total fix, partial fix)	Dependencies 	Technical details	Remark
35952
35952
Total Fix	Impacted applications: Billing	Code change.
	Defect is resolved.

Defect #92
Defect Description: APIGW is appending extra values in SM URL.
Current state: Resolved
ID Defect(Link to MSI backlog)	ID defect in vendor backlog (if already opened)	Delivery State(total fix, partial fix)	Dependencies 	Technical details	Remark
N/A (Internally identified)	N/A (Internally identified)	Total fix	Impacted application: 
APIGW	Code change.
APIGW to discard extra values in SM URL	Resolved

New Enhancement #93
Defect Description: API-GW, the SAS tokens to be fetched from KeyVault to access the storage accounts to download the metering files. 

Defect id: NA
Current state: Developed.
ID Defect (Link to MSI backlog)	ID defect in vendor backlog (if already opened)	Delivery State (total fix, partial fix)	Dependencies 	Technical details	Remark
N/A
	N/A 
	Total Fix	Impacted applications: 
APIGW	Code change. API-GW has to get the appropriate SAS token set to access the storage account, pass the same to download the files.
	



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


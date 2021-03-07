**_Release Note_**  

**1.0 What’s New (New delivered user stories)**
NA

_**🚀 2.0 Fixed Defects**_
**2.1 Defect#1** 
Defect Description: FN-B2B-Order failed after payment. (Payment is successful, but order got failed due to Data too long for column).
Defect id: 33270.
Current state: Resolved.
ID Defect(Link to MSI backlog)	ID defect in vendor backlog (if already opened)	Delivery State(total fix, partial fix)	Dependencies 	Technical details	Remark
33270
33270
Total Fix	Impacted applications: Billing / API	DB configuration change. Column length of the bundle id is increased. 	Defect is resolved.

**Defect#2:** 
Defect Description: Status was not getting completed if a order with more than one suborders.
Defect id: This defect is internally identified by 6d team.
Current state: Resolved
ID Defect(Link to MSI backlog)	ID defect in vendor backlog (if already opened)	Delivery State(total fix, partial fix)	Dependencies 	Technical details	Remark
N/A(Internally identified)	N/A (Internally identified)	Total fix	Impacted application: Order Management.	Code Change. When we are having multiple suborders, we are considering the 1st suborder status.	
Code fix is completed.

**Defect#3**
Defect Description: Email not sending from NG and getting exception.
Defect id: 33786
Current state: Resolved

ID Defect(Link to MSI backlog)	ID defect in vendor backlog (if already opened)	Delivery State(total fix, partial fix)	Dependencies 	Technical details	Remark
33786
33786
Total fix	Impacted application: NG	Code Change. 
Based on MSFT error code(401), NG is setting internal error code. Based on the internal error code, NG will call  OAuth registration API and retry the notification.	Code fix is completed.


**Defect#4:** 
Defect Description: Invoice should show zero rental subscriptions.
Defect id: This defect is internally identified by 6d team.
Current state: Resolved
ID Defect(Link to MSI backlog)	ID defect in vendor backlog (if already opened)	Delivery State(total fix, partial fix)	Dependencies 	Technical details	Remark
N/A(Internally identified)	N/A (Internally identified)	Total fix	Impacted application: Billing Core.	Code Change. 
Implemented invoice for zero rental subscription	
Code fix is completed.

**Defect#5 – Performance testing**
Defect Description: Connection Exception from Billing during API Load Testing(Connection got refused in between load run)
Defect id: This defect is internally identified by 6d team.
Current state: Resolved.
ID Defect(Link to MSI backlog)	ID defect in vendor backlog (if already opened)	Delivery State(total fix, partial fix)	Dependencies 	Technical details	Remark
N/A (Internally identified)	N/A (Internally identified)	Total Fix	Impacted applications: Billing application/ DB	Change in connections configured: min pool size 0 and max pool size 40 and Table Indexing have been added to get better TPS 
Code Change	Defect is resolved.


**Defect#6 – Performance testing**
Defect Description: During API Load testing through JMETER, We observed "Connection is getting refused from OM in between the process
Defect id: This defect is internally identified by 6d team.
Current state: Resolved
ID Defect(Link to MSI backlog)	ID defect in vendor backlog (if already opened)	Delivery State(total fix, partial fix)	Dependencies 	Technical details	Remark
N/A (Internally identified)	N/A (Internally identified)	Total fix	Impacted application: Order Management.	Configuration change and Code Change. Increased max no of connections in property file to 60 .to get better TPS.
	
Code fix is completed.

**Defect#7 – Performance testing**
Defect Description: During SubmitSubscriptionOrder API and UpdateOrder API with 10Threads ,Rampup10,Loop10 , Seen Lock Exception
Defect id: This defect is internally identified by 6d team.
Current state: Resolved
ID Defect(Link to MSI backlog)	ID defect in vendor backlog (if already opened)	Delivery State(total fix, partial fix)	Dependencies 	Technical details	Remark
N/A (Internally identified)	N/A (Internally identified)	Total fix	Impacted application: Order Management/DB	Code Change. transaction got locked so took more time and table indexing was done.
	
Code fix is completed.

**Defect#8 – Performance testing**
Defect Description: All OM related APIS taking more time for processing and resulting less TPS.
Defect id: This defect is internally identified by 6d team.
Current state: Resolved.
ID Defect(Link to MSI backlog)	ID defect in vendor backlog (if already opened)	Delivery State(total fix, partial fix)	Dependencies 	Technical details	Remark
N/A (Internally identified)	N/A (Internally identified)	Total fix	Impacted application: Order Management.	Code Change. 
Disabled select query to get connection pool details and to get max seq_id while inserting into tables in property file.	
Code fix is completed.

**Defect#9 – Security Testing**
Defect Description: Security validation - Web Security Vulnerability - Insecure Direct object reference
Defect id: This defect is internally identified by 6d team.
Current state: Resolved.
ID Defect(Link to MSI backlog)	ID defect in vendor backlog (if already opened)	Delivery State(total fix, partial fix)	Dependencies 	Technical details	Remark
N/A (Internally identified)	N/A (Internally identified)	Total Fix	Impacted applications: 
Enterprise_ui	Code change
Enabled access control check using privilege	Defect is 
resolved.

**Defect#10 – Security Testing**
Defect Description: Security validation - Web Security Vulnerability - Private IP addresses Disclosed
Defect id: This defect is internally identified by 6d team.
Current state: Resolved
ID Defect(Link to MSI backlog)	ID defect in vendor backlog (if already opened)	Delivery State(total fix, partial fix)	Dependencies 	Technical details	Remark
N/A(Internally identified)	N/A (Internally identified)	Total fix	Impacted application: Enterprise_ui	Code Change. 
Removed the internal IP address from the CSP Response header	Code fix is completed.


**Defect#11 – Security Testing**
Defect Description: Security validation - Web Security Vulnerability - Multiple SSL vulnerabilities
Defect id: This defect is internally identified by 6d team.
Current state: Resolved

ID Defect(Link to MSI backlog)	ID defect in vendor backlog (if already opened)	Delivery State(total fix, partial fix)	Dependencies 	Technical details	Remark
N/A(Internally identified)	N/A (Internally identified)	Total fix	Impacted application: Enterprise_ui	Code Change. 
Added the SSL configuration in the standalone.xml file	Code fix is completed.

**Defect#12 – Security Testing**
Defect Description: Security validation - Information disclosure through Error messages
Defect id: This defect is internally identified by 6d team.
Current state: Resolved

ID Defect(Link to MSI backlog)	ID defect in vendor backlog (if already opened)	Delivery State(total fix, partial fix)	Dependencies 	Technical details	Remark
N/A(Internally identified)	N/A (Internally identified)	Total fix	Impacted application: Enterprise_ui	Code Change. 
Started showing generic error message for different error codes	
Code fix is completed.

**Defect#13 – Security Testing**
Defect Description: Security validation - Web Security Vulnerability - Host Header Injection
Defect id: This defect is internally identified by 6d team.
Current state: Resolved
ID Defect(Link to MSI backlog)	ID defect in vendor backlog (if already opened)	Delivery State(total fix, partial fix)	Dependencies 	Technical details	Remark
N/A(Internally identified)	N/A (Internally identified)	Total fix	Impacted application: Enterprise_ui	Code Change. 
Introduced host header validation	
Code fix is completed.


**Defect#14 – Security Testing**
Defect Description: Security validation - Improper implementation of content-security policy header
Defect id: This defect is internally identified by 6d team.
Current state: Resolved.
ID Defect(Link to MSI backlog)	ID defect in vendor backlog (if already opened)	Delivery State(total fix, partial fix)	Dependencies 	Technical details	Remark
N/A (Internally identified)	N/A (Internally identified)	Total Fix	Impacted applications: 
Retail Portal	Code change
IP address is not disclosed in policy header	Defect is 
resolved.

**Defect#15 – Security Testing**
Defect Description: Security validation - Multiple SSL vulnerabilities
Defect id: This defect is internally identified by 6d team.
Current state: Resolved
ID Defect(Link to MSI backlog)	ID defect in vendor backlog (if already opened)	Delivery State(total fix, partial fix)	Dependencies 	Technical details	Remark
N/A(Internally identified)	N/A (Internally identified)	Total fix	Impacted application: Retail Portal	Code Change. 
Enabled latest version of SSL 	
Code fix is completed.


**Defect#16 – Security Testing**
Defect Description: Security validation - Private IP addresses Disclosed
Defect id: This defect is internally identified by 6d team.
Current state: Resolved

ID Defect(Link to MSI backlog)	ID defect in vendor backlog (if already opened)	Delivery State(total fix, partial fix)	Dependencies 	Technical details	Remark
N/A(Internally identified)	N/A (Internally identified)	Total fix	Impacted application: Retail Portal	Code Change. 
Ensured IP addresses are not disclosed.	
Code fix is completed.





**2.3 Differed open Defects.**
List the defect fixes that could not be completed and fixed in the current release
Defect ID(in MSI Backlog)	ID defect in vendor backlog (if already opened)	Description	Technical details	Reason of postponement	New ETA
					
					

**⭐ 3.0 Improvements**
List out all improvements that you've made to your product.





**💻 4.0 Reviewers** 

Prepared By	Abhinav T 
Company name	6d Technologies
Reviewed by 	Elango Periasami
Approved by 	


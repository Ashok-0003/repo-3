[Release Note_6d Billing_V 0.1_24-02-2021.docx](/.attachments/Release%20Note_6d%20Billing_V%200.1_24-02-2021-8e3264c4-df51-45cd-ae47-dfb66821cd22.docx)

**Release Note**  

**🚀 2.0 Fixed Defects**

**_2.1 Defect#1_** 
Defect Description: FN-B2B-Order failed after payment. (Payment is successful, but order got failed due to Data too long for column).
Defect id: 33270.
Current state: Resolved.
ID Defect(Link to MSI backlog)	ID defect in vendor backlog (if already opened)	Delivery State(total fix, partial fix)	Dependencies 	Technical details	Remark
33270
33270
Total Fix	Impacted applications: Billing / API	DB configuration change. Column length of the bundle id is increased. 	Defect is resolved.

_**2.2 Defect#2:**_ 
Defect Description: Status was not getting completed if a order with more than one suborders.
Defect id: This defect is internally identified by 6d team.
Current state: Resolved
ID Defect(Link to MSI backlog)	ID defect in vendor backlog (if already opened)	Delivery State(total fix, partial fix)	Dependencies 	Technical details	Remark
N/A(Internally identified)	N/A (Internally identified)	Total fix	Impacted application: Order Management.	Code Change. When we are having multiple suborders, we are considering the 1st suborder status.	
Code fix is completed.


**💻 4.0 Reviewers** 

Prepared By	Abhinav T 
Company name	6d Technologies
Reviewed by 	Elango Periasami
Approved by 	


**1. Product Data**
1. Product family is known as Product in portal .Product family can have Bundle product or individual product attached to it. so, we need to create a Product family first. While creating product family we need to enter the mandatory field as well as "Short description", "Decimal Supported" ,"Price overview", "Profile Type"(B2B individual or B2B Organization), "Catalogue Type" ,"Product Category" and "Product Subcategory". So that This record will visible in Portal.

2. The Product Bundle or Individual product is said to be "Plan" in the Portal. Now we can create the Product Bundle .We need to enter the mandatory fields and enter the "Parent" field .The "Parent" should be the "Product Family" what we have already created. For the better visibility in the portal, we can add "Price Overview" , "price Overview Term ". 
We need to add "Marketplace Product Charge" and "Marketplace Product Lifecycle" for the bundle level. We can move to the "Bundle & Association" tab . we can associate the Bundle product there. Now we need to Publish the "Product". 

3. For the Individual Product , we need to enter all the mandatory fields and fill the "Parent" field . Then we can add the "Marketplace Product Lifecycle", "Marketplace Product Plan Benefit", "Marketplace Product Charge", "Marketplace Product Tariff" and "Marketplace Product Usage Limit". Then Publish the Product.
---
Tool for migrating some portion of products.
[Product Catelog Data Migration.docx](/.attachments/Product%20Catelog%20Data%20Migration-5113cdcc-c92d-4998-b98a-6cd2752fbd90.docx)

**2. Knowledge Articles Data** 

  1. Please follow the below link for create knowledge articles and how to update translations of knowledge articles. Similarly we can add the related article as well.

https://docs.microsoft.com/en-us/dynamics365/customer-service/customer-service-hub-user-guide-knowledge-article

2. This is how we can link related Knowledge article from KB Article.
open Knowledge Article record. Then summary->Related Information->Related Articles . Same way we can link the related product from KB Article.

![RelatedArticle1.png](/.attachments/RelatedArticle1-7364b827-f8d5-46eb-96bb-95b13ff80b00.png) 

![RelatedArticle2.png](/.attachments/RelatedArticle2-fcbe81e4-1a51-4260-8f96-2538d0ed8e04.png)

3.In KB Article, When we are selecting the related product as below:
- profile types = b2c individual, b2c business owner
- catalogue type = use case
- product category = smart eservices
As per the Above Condition , It will "My Tasmu" Portal.

In KB Article , When we are selecting the related product as below:
-  profile types = b2b individual, b2b organisation
- catalogue type = tasmu
- product category = tasmu product & services
As per the Above Condition , It will "Marketplace" Portal.

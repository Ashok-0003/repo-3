##**Patch base.html**

```
cd /opt/bitnami/ckan/venv/src/ckan/ckan/templates 
sudo vi base.html
```
 
**On line 113, add the following code snippet (refer image below)**

<script type="text/javascript"> 
var currentLanguage = document.getElementsByTagName('html')[0].getAttribute('lang'); 
var aTag = document.getElementById('motctmlogo'); 
var footerLink = document.getElementById('footerLink'); 
if (currentLanguage == "ar") { 
footerLink.innerHTML = "ﺎﻠﺼﻔﺣﺓ ﺎﻟﺮﺌﻴﺴﻳﺓ ﻞﻤﻨﺻﺓ ﺖﺴﻣﻭ"; 
aTag.href = https://www.motc.gov.qa/ar; 
} else { 
aTag.href = https://www.motc.gov.qa/en; 
} 
</script>  

![image.png](/.attachments/image-aa8cf0b2-4a57-405c-8957-4beba0ac947b.png)
		
##**Patch footer.html**
```
sudo vi /opt/bitnami/ckan/venv/src/ckan/ckan/templates/footer.html 
```
###1. Change first div class from **col-md-8** to **col-md-6** 
###2. Add new div code for footer logo -  

```
<div class="col-md-3">
{% block footer_logo %} 
<a class="motctmlogo" href=”https://www.motc.gov.qa/” target=”_blank”>
<img height="32" src="/base/images/ckan-footerlogo-white.png" alt="{{ g.site_title }}" title="{{ g.site_title }}" />
</a>
{% endblock %} 
</div> 
```
###3. Change last div class from **col-md-4** to **col-md-3** 
	![image.png](/.attachments/image-4f03d9a6-7ad5-4d1e-8edf-7dfce41c6b0c.png)
		 
##**Patch header.html**
```
sudo vi /opt/bitnami/ckan/venv/src/ckan/ckan/templates/header.html 
```
**On line 75 add – height=”50” (refer image below)** 
![image.png](/.attachments/image-605f41a8-0c07-4ad2-ac1e-3881798a6386.png)
		
##**Apply theme and restart service**

```
cd /opt/bitnami/ckan/venv/src/ckan/ckanext/ckanext-tasmu_theme 
sudo python setup.py develop 
sudo service bitnami restart
```
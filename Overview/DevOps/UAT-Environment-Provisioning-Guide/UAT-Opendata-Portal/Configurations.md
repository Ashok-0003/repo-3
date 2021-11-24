[[_TOC_]]

## **Setup AZ Copy**

### **Download AZ Copy for Linux**
	sudo wget https://aka.ms/downloadazcopy-v10-linux
### **Unzip AZ Copy**
	sudo  tar -xvf downloadazcopy-v10-linux

## **Setup Tasmu Theme**

### **Navigate path**
	cd /opt/bitnami/ckan/venv/src/ckan/ckanext

### **AZ Copy Tasmu Theme folder**
	(Always replace SAS key from storage account with correct permissions)
	sudo ~/azcopy_linux_amd64_10.13.0/azcopy copy "https://stcpdappsckantstwe01.blob.core.windows.net/ckanfiles/ckanext-tasmu_theme/?sp=racwdl&st=2021-11-24T14:03:47Z&se=2021-11-24T22:03:47Z&spr=https&sv=2020-08-04&sr=c&sig=a5%2BF0KxNWT%2BiUXdqrwk4XpjW2zW0PUM9oJj9iXm2P6s%3D" . --overwrite=prompt --check-md5 FailIfDifferent --from-to=BlobLocal --recursive

### **Navigate path**
	cd ckanext-tasmu_theme

### **Setup Tasmu Theme**
	sudo python setup.py develop

##**Update Postgres backend**

### **Navigate path**
	cd /opt/bitnami/ckan/venv/src/ckan/ckanext/datastore/backend/
	
### **AZ Copy Postgres.py file**
	(Always replace SAS key from storage account with correct permissions)
	sudo ~/azcopy_linux_amd64_10.13.0/azcopy copy "https://stcpdappsckantstwe01.blob.core.windows.net/ckanfiles/postgres.py?sp=racwdl&st=2021-11-24T14:03:47Z&se=2021-11-24T22:03:47Z&spr=https&sv=2020-08-04&sr=c&sig=a5%2BF0KxNWT%2BiUXdqrwk4XpjW2zW0PUM9oJj9iXm2P6s%3D" . --overwrite=prompt --check-md5 FailIfDifferent --from-to=BlobLocal --recursive
	
## **Set Permissions**

sudo chown www-data /opt/bitnami/ckan/data
sudo chmod u+rwx /opt/bitnami/ckan/data

## **Setup Datapusher**

### **Navigate path & create Datapusher directory**
	cd /opt/bitnami/ckan
	sudo mkdir datapusher

### **Install Python virtual env and dependencies**
	sudo apt install python3-venv python3-dev build-essential
	sudo apt-get install python-dev python-virtualenv build-essential libxslt1-dev libxml2-dev git libffi-dev
	sudo python3 -m venv /opt/bitnami/ckan/datapusher
	sudo /opt/bitnami/ckan/datapusher/bin/python3 -m pip install --upgrade pip
	sudo pip3 install --upgrade requests

### **Create and clone Datapusher source code**
	sudo mkdir /opt/bitnami/ckan/datapusher/src
	cd /opt/bitnami/ckan/datapusher/src
	sudo git clone -b 0.0.17 https://github.com/ckan/datapusher.git

### **Setup Datapusher**
	cd datapusher
	sudo /opt/bitnami/ckan/datapusher/bin/pip install -r requirements.txt
	sudo /opt/bitnami/ckan/datapusher/bin/python setup.py develop
	sudo addgroup www-data
	sudo adduser  www-data www-data
	sudo /opt/bitnami/ckan/datapusher/bin/pip install uwsgi

### **Update datapusher path in uwsgi file and grant permissions**
	sudo vi /opt/bitnami/ckan/datapusher/src/datapusher/deployment/datapusher-uwsgi.ini
	![image.png](/.attachments/image-10f60fde-9c8d-4077-bb52-d568b30ea17c.png)
	cd /opt/bitnami/ckan/datapusher/bin
	sudo chmod 777  uwsgi
	sudo chmod 777 /tmp/ckan_service.log

### **Register Datapusher as a service**
```
cd /etc/systemd/system
sudo nano datapusher.service
```

   ![image.png](/.attachments/image-1c19dca3-d6bb-490b-afcd-6a5d46435ecb.png)
	
```
[Unit]
Description = CKAN Datapusher service
[Service]
User=bitnami
WorkingDirectory=/opt/bitnami/ckan/datapusher/bin/
ExecStart=/opt/bitnami/ckan/datapusher/bin/uwsgi -i /opt/bitnami/ckan/datapusher/src/datapusher/deployment/datapusher-uwsgi.ini
Type=simple
TimeoutStopSec=10
Restart=on-failure
RestartSec=5
[Install]
WantedBy=multi-user.target
```

### **Enable and check status for Datapusher service**
	sudo systemctl daemon-reload
	sudo systemctl enable datapusher
	sudo systemctl start  datapusher
	sudo systemctl status datapusher
	
## **Setup PdfView and GeoView Extensions**

sudo pip install ckanext-pdfview
sudo pip install ckanext-geoview

## **Restart Bitnami Service**

sudo service bitnami restart
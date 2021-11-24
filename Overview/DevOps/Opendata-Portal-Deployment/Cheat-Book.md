##CKAN Logs -
`vi /opt/bitnami/ckan/logs/ckan.log`

##Datapusher Logs -
`vi /tmp/ckan_service.log`

##Check status for Bitnami service -
`sudo service bitnami status`
`sudo systemctl status bitnami`

##Check status for Datapusher service -
`sudo service datapusher service`
`sudo systemctl status datapusher`

##Check Datapusher is up and running -
`curl localhost:8800`
(if response is an error that means service is down, check logs)

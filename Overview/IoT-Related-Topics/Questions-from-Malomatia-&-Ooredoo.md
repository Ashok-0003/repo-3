
•	Is it possible to set a storage Quota? If yes, what happens if the storage Quota exceeds its limit, then do we get alert.
R. can you clarify this question. 

•	Is it possible to set limits to MQTT and HTTPS calls per seconds, what happens if the calls exceed the limits do we get an alert?  
R. Please see this link for Azure IoT Hub throttling details - Understand Azure IoT Hub quotas and throttling | Microsoft Docs. Yes, see  429 ThrottlingException as the queue fills up.

•	Are there MQTT or HTTPS requests Queue, can we put a limit on the size of the Queue.
R. IoT Hub message maximum retention for device-to-cloud messages is 7 days. See this article IoT Hub throttling and you | Azure Blog and Updates | Microsoft Azure

•	How flexible with Integration with other enterprise applications or other proprietary software? 
R. can you clarify this question? Azure IoT Hub provides API’s and SDK’s for integration Understand the Azure IoT SDKs | Microsoft Docs

•	For integration with other non-Microsoft systems, does it require expert knowledge of MS stack
R. same as above. 

•	Are there any APIs that allow custom Web Development or external applications to interact with Azure, please provide details?
R. more details are required to provide an answer.

•	Please provide detailed information on the Communication Protocols Supported by Azure IoT hub.
R. Azure IoT Hub communication protocols and ports | Microsoft Docs
 

•	Confirm if Azure supports NB-IoT, LoRaWAN, SigFox
R. Yes - Azure IoT Hub | Sigfox Partner Network | The IoT solution book; Azure/iotedge-lorawan-starterkit: Experimental sample implementation of LoRaWAN components to connect LoRaWAN antenna gateway running IoT Edge directly with Azure IoT. (github.com); 

•	Please confirm if PKI certificates are supported, if yes please provide detailed information on the support for PKI certificates.
R. Yes – Overview of Azure IoT Hub X.509 CA security | Microsoft Docs; Overview of Azure IoT Hub X.509 CA security | Microsoft Docs

•	Does Azure have a device certification program for its IoT hub?
R. Yes - Azure Certified Device catalog (preview)

•	Does Azure have a list of PKI supported devices and gateways? If Yes, please provide them
R. Not sure that list exists.

•	Please confirm if any production-ready use cases on Azure, including that, use PKI devices.
R. yes, there are multiple use cases in production using azure and iot hub.

•	Please confirm the encryption algorithm (e.g. sha256) supported on these devices and the Azure IoT hub.. 
R. This question is for device providers.

•	Please confirm and provide details if the Azure IoT hub supports Cloud Fieldbus, Modbus, and other protocols.
R. through gateways - Translate modbus protocols with gateways - Azure IoT Edge | Microsoft Docs

•	How easy is the device integration, does it provide a full set of features in the SaaS model for device integration and management? 
R. can you clarify this question?

•	Does Streaming Analytics and ML are integrated into the core IoT Hub, can you please provide more details.
R. Azure ASA and ML are Azure Services that work with Azure IoTHub to provide end to end solutions. See for an example - Process real-time IoT data streams with Azure Stream Analytics | Microsoft Docs

•	Does Azure support Batch analysis on Streaming Analytics and ML
R. by Batch analysis we assume you mean sending the payload to an Azure storage account and then do batch processing with Hadoop and/or Spark. Yes. Route IoT device messages to Azure Storage with Azure IoT Hub | Azure Blog and Updates | Microsoft Azure; 


This document discusses about the connectivity of remote apple system and the network configuration that is necessary.

Pre-requisites:
Mac-Local-Agent connected to internet, installed all required development tools. For reference visit <a href="https://docs.microsoft.com/en-us/xamarin/ios/get-started/installation/windows/connecting-to-mac/">Pairing to mac</a> and <a href="https://docs.microsoft.com/en-us/xamarin/ios/get-started/installation/"> Xamarin ios installation </a> 

Connection Configuration for Mac:
1. To connect the mac-local-agent from a remote machine the following ports needs to be enabled at the router connected to mac-local-agent

| Port | Protocol | Port-Connection |
|--|--|--|
| 3283 | TCP | Apple Remote Desktop |
| 22 | TCP | SSH connection |
| 6000 | UDP | Visual Studio connection |
2. Enable these ports in the router and configure for port forwarding to the mac-local-agent's ip.
eg: router-public-ip (x.x.x.x:3283) to mac-local-agent-ip(192.168.1.3:3238)

Test the port availability using <a href="https://www.yougetsignal.com/tools/open-ports/"> tool </a>

Pairing to the mac-local-agent from a remote machine should be possible now.





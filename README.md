# Reverse-proxy-tunnel-in-Mikrotik-via-x--u-i
**How to create a reverse tunnel in Mikrotik using the X-Ray platform?  It is very smart that we can create a reverse tunnel in Mikrotik using this platform**  
**According to the following commands, activate the Docker container in Mikrotik, then enter other commands to create interfaces and install the panel in your Mikrotik terminal**  

**After completing these steps, you can see the rest of the work in the video below on our YouTube channel**  
## 📺 Video Tutorial
🎥 Watch the full installation and usage guide on YouTube:  
👉 [Click here to watch the video](https://www.youtube.com/watch?v=iRSnJI5AI4w)

**Enter the following commands in order in the terminal**

**enable mikrotik container**

/system/device-mode/update container=yes  
/system/device-mode/print    

**Creating a virtual interface and giving it an IP address, and finally adding it to the Docker bridge and providing access to the internet**

/interface/bridge/add name=dockers  
/ip/address/add address=172.17.0.1/24 interface=dockers  
/interface/veth/add name=veth1 address=172.17.0.2/24 gateway=172.17.0.1  
/interface/bridge/port add bridge=dockers interface=veth1  
/ip/firewall/nat/add chain=srcnat action=masquerade src-address=172.17.0.0/24   

**If your server has IP version 6, you can configure it like this**

ipv6:fc07:55::1/64 set to bridge interface

ipv6:fc07:55::2/64 set to veth

**Configuring Docker Registry Link**  

container/config/set registry-url=https://registry-1.docker.io tmpdir=pull   

**Finally, pull the Docker image**  

Docker image : alireza7/x-ui:latest    

**Why we use this image for Docker**
**Ease of use, support for many protocols and most importantly, automatic restart after possible router reboot**  

https://www.youtube.com/@mikronet_plus


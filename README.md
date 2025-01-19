
<p align="center">
<img src="https://i.imgur.com/Ua7udoS.png" alt="Traffic Examination"/>
</p>

<h1>Network Security Groups (NSGs) and Inspecting Traffic Between Azure Virtual Machines</h1>
In this tutorial, we observe various network traffic to and from Azure Virtual Machines with Wireshark as well as experiment with Network Security Groups. <br />




<h2>Environments and Technologies Used</h2>

- Microsoft Azure (Virtual Machines/Compute)
- Remote Desktop
- Various Command-Line Tools
- Various Network Protocols (SSH, RDH, DNS, HTTP/S, ICMP)
- Wireshark (Protocol Analyzer)

<h2>Operating Systems Used </h2>

- Windows 10 (21H2)
- Ubuntu Server 20.04

<h2>High-Level Steps</h2>

- Step 1 Create a Virtual Machine (both windows and linux) and Resource Group
- Step 2 Install Wireshark
- Step 3 Observe differnt types of traffic (SSH, RDH, DNS, HTTP/S, ICMP) using ping, ipconfig and nslookup

<h2>Actions and Observations</h2>

<p>
  
![image](https://github.com/user-attachments/assets/cb472f46-28ba-4eac-aea3-948f6fb0f53d)
![image](https://github.com/user-attachments/assets/539d844b-02d9-4c55-a7cf-fa112203a79f)
![image](https://github.com/user-attachments/assets/6a74dc81-0d75-4a2d-8a4a-e2f0b22cbd00)

Creating a Virtual Machine and Resource Group is pretty simple. Just log into Microsoft Azure and create a subscription account. AFter that click on resource group and name it whatever you like. Set the location to anywhere (just remember where you put it so you can have both in the same region). Click review and create. For the Virtual Machine go back to the home page and click on virtual machine, put it in the same resource group (should be the only option if you made one resource group), set it in the same region as the resource group. Now for image make sure you put it under windows 10 pro (it may default to a lynex), make sure the size is 2vcpus otherwise it may run quite a bit slower (do not worry about the price since that only matters if your running the virtual machine for 24/7 otherwise its only a dollar or two), create a user name and password be sure to write it down, check the licensing box at the bottom. Then click next twice, you should be at networking (you can change the virtual network if you like). Once that is done just click review and create and let it setup. To create a linux vm is basically the same as a windows the only two fields that change is the image (Ubuntu Server 24) and authentication type (change to password and use the same one as you did for the windows vm). Click next till you get to networking and make sure its in the same virtual network as the other one (you may have to refresh because it has an issue where it may not find it due to creating virtual machines too quickly). When you have it in the same virtual network go ahead and click review and create. To check if done correctly, go to virtual machines and click on either one and look on the right hand side (Virtual network/subnet) and they should both have the same text.

![image](https://github.com/user-attachments/assets/98075d30-b4dc-4abc-97b6-cb5370429558)

Once everything is complete go ahead and use the login information to login to Remote Desktop (if using MAC, you will have to download it first from the app store). Once you are all signed into the remote desktop go ahead and download wireshark on the Virtual Machine (www.wireshark.org). Use the Windows x64 installer and once download, open the file and keep clicking next and install (do not worry about what is on the screen). Click I agree and install again until it has completely installed. This program is what will allow you to view traffic between the virtual machines. 

![image](https://github.com/user-attachments/assets/5af650ce-5acb-4411-b979-0c4069812223)
![image](https://github.com/user-attachments/assets/45210709-e8f1-451e-81e5-1bbfa59d0176)
![image](https://github.com/user-attachments/assets/1fa5d0ca-b8ec-4ef3-8c7b-83b9a8384a8a)

After wireshark is installed, you can close everything and go to start and find wireshark (should have a shark fin for the logo). Once opened highlight the interface has the line on it (this is the communication line) and click the fin in the top left and it should start running a bunch of data. Do not worry as this is all the traffic that is being sent between the networks and being captured. All the numbers on the left side are called IP packets (small chunk of data being sent over the internet containing information and any necessary detail to get to the right destination). Think of it as a post office sending to a bunch of addresses. To fiter certain types of traffic (example ping,icmp) just type in the filter/search bar and it will cut out everything but that type of traffic (you won't see anything at first with the ICMP command). To ping the other virtual machine, open up powershell and type ping 10.0.0.5 (or whatever your PRIVATE IP address for your linux vm is) and you should get a reply. If you look at the wireshark you should now see some communication happening and notice that you will see a request from one ip and a reply from the other ip. This is showing that both are communicating with each other. ICMP stands for internet control message protocol and is the protocol that ping uses to chcek if another computer reachable on the network line. Ping is also used for troubleshooting to check connectivity between two points. These are just a few of the things you can do and if you want more detail on any of these commands I recommend going to ChatGPT or copilot to get better information as there is so much information on all of these. Same goes for public vs private ip addresses. In short, public ip addressess are used to surf the internet and private ip addresses cannot but private ip addresses are also much more secure as they sent informaiton that is encrypted and cannot be hacked. There are also very detailed youtube videos that creators have made that explain these topics in much better detail if your more of a visual learner.
</p>
<br />


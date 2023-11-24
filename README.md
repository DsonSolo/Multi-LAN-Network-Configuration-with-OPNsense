# Multi-LAN Network Configuration with OPNsense
Setting up a Multi-LAN Network infrastructure with the implementation of an OPNsense Next-Generation Firewall (NGFW).

## What is a Multi-LAN Network?
A Multi-LAN (Local Area Network) Network refers to a network setup that includes multiple distinct local networks within a larger networked environment. In a Multi-LAN configuration, each LAN operates independently but is interconnected, allowing data and information to flow between them.

Download a Windows 10 ISO Image and select a virtualization application; in this illustration, we will utilize the Oracle VM along with the OPNsense image.

Windows 10 ISO:
https://www.microsoft.com/en-us/software-download/windows10

Oracle VM:
https://www.virtualbox.org/wiki/Downloads

OPNsense:
https://opnsense.org/download/

Configure network settings by navigating to File > Tools > Network Manager. Under the NAT Networks tab, click the 'Create' button and employ the settings depicted in the image below. I am labeling my network as WAN with the IP 192.168.10.0/24.

![Screenshot](https://github.com/DsonSolo/Multi-LAN-Network-Configuration-with-OPNsense/blob/main/Start.png)

After creating the VM with the OPNsense image, I'm now configuring the VM's network settings. Right-click > Settings > Network. Under Adapter 1, I'm setting it to NAT Network and using the WAN configuration we just established.

![Screenshot](https://github.com/DsonSolo/Multi-LAN-Network-Configuration-with-OPNsense/blob/main/2.png)

In the network settings, for Adapter 2, I'm configuring it as an Internal Network named LAN. As for Adapter 3, I'm repeating the process, but this time naming it Guest_LAN. Now, our network consists of three networks: WAN for internet access and two Guest Networks, forming our Multi-LAN setup.

![Screenshot](https://github.com/DsonSolo/Multi-LAN-Network-Configuration-with-OPNsense/blob/main/3.png)

Running the OPNsense VM is the initial step. Upon running it, the Firewall needs configuration before it becomes operational. We'll start by choosing Option 1 - Assigning Interfaces and allocate our WAN network with the designated 192.168.10.0/24 address. 

For the LAN, enter the prompted configuration after selecting 1. Following the Assignment of Interfaces, we'll move on to Option 2 - Set Interface IP address, where you can customize the settings as desired. Upon completion, OPNsense will provide a link to access the firewall panel in the browser, as shown below:

![Screenshot](https://github.com/DsonSolo/Multi-LAN-Network-Configuration-with-OPNsense/blob/main/image4.png)

Utilize the provided link to configure and secure your Firewall. In my instance, the IP is http://192.168.2.1, and the default login credentials should be username: root & password: opnsense. Alternatively, you can access the OPNsense VM and choose option 3 to reset the password. 

After logging in, navigate to Lobby > Password to change the default password. Additionally, ensure to go into Systems and update to the latest version.

![Screenshot](https://github.com/DsonSolo/Multi-LAN-Network-Configuration-with-OPNsense/blob/main/image5.png)

Now, with WAN and LAN Networks set up by default, we need to add the 3rd network through OPNsense, as DHCP-assigned IPs will be managed by OPNsense. 

In the panel, navigate to Interfaces > Assignments, add the 3rd Network, and name it Guest_LAN. Our Multi-LAN Network should now be fully operational.

![Screenshot](https://github.com/DsonSolo/Multi-LAN-Network-Configuration-with-OPNsense/blob/main/image6.png)

Navigate to Services > DHCPv4 > Guest_LAN. Set the IP address for this network; I simply used 192.168.3.1. Ensure it's enabled and configured correctly. 

When you boot up PC1 and PC2, PC1 should be on the LAN Network (192.168.2.x), and PC2 should be on Guest_LAN (192.168.3.x).







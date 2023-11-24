## Multi-LAN Network Configuration with OPNsense
Setting up a Multi-LAN Network infrastructure with the implementation of an OPNsense Next-Generation Firewall (NGFW).

# What is a Multi-LAN Network?
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






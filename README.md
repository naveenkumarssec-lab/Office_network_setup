# Simple Office Networking Design using CISCO packet tracer.

Case Study: ABC company deals with selling and buying of items which are basically operated from the headquearters. the company is intending to open a branch near the local village the company requires young IT graduates to design the network for the branch the network is intended to operate separately from the HQ network.

Being a small network the company the following requirements during implementation:

a) One router and one switch to be used (all CISCO products)
b) 3 departments (Admin/IT, Finance/HR and customer service/Reception)
c) Each department is required to be in different VLANS.
d) Each department is required to have wireless network for the users.
e) Host devices in the network are required to obtain IPv4 address automatically.
f) Device in all the departments are required to communicate with each other.

Assume the ISP gave out a base network of 192.168.1.0 you as the young network engineer who has been hired, design and implement a network considering the above requirements.

# Installing Components in Cisco packet tracer:

Picking components router, pc, switch, printers and so on bottom of the screen in the cisco packet tracer

Connecting router, switch, pc and other components using fast ethernet cable. for each department consist admin, finance, customer service.
# Screenshot

![]()

# Setup Virtual local network

Creating VLAN for each department enable dividing single physical switch port to separate group of logical port to isolate the network it enhance security and speed of packet travel.

# Screenshot





# Configuring router to make communication amoung the departments

Here make communication amoung the different VLANs 10, 20 30.
- Comment lines in router.
> en;
>conf t;
>int gig0/0;
>no sh;
>do wr;
>exit;

- The above comment line defines enabling gig0/0 ethernet cable which in router to communicate all the networks

>int gig0/0.10;
>encapsulation dot1Q 10;
>ip address 192.168.1.1 255.255.255.192;
>exit;

- Above comment line make a traffic tag ID for VLAN 10 (Admin department) to communicate through gig0/0 ethernet and assigning IP address for this network.

>int gig0/0.20;
>encapsulation dot1Q 20;
>ip address 192.168.1.65 255.255.255.192;
>exit;

- Above comment line make a traffic tag ID for VLAN 20 (Finance department) to communicate through gig0/0 ethernet and assigning IP address for this network.

>int gig0/0.30;
>encapsulation dot1Q 30;
>ip address 192.168.129 225.255.255.192;
>do wr;
>exit;
>do sh start;

- Above comment line make a traffic tag ID for VLAN 20 (Finance department) to communicate through gig0/0 ethernet and assigning IP address for this network.

#DHCP configuration for assign IP automatically

config> service dhcp;
>ip dhcp pool Admin-local;
>network 192.168.1.0 255.255.255.192;
>default-router 192.168.1.1;
>dns-server 192.168.1.1;
>domain-name Admin.local;
>exit;

dncp conf 2nd subnet

>ip dhcp pool Finance-local;
>network 192.168.1.64 255.255.255.192;
>default-router 192.168.1.65;
>dns-server 192.168.1.65;
>domain-name Finance.local;
>exit;

dhcp conf 3rd subnet

>ip dhcp pool Customer-local;
>network 192.168.1.128 255.255.255.192;
>default-router 192.168.1.129;
>dns-server 192.168.1.129;
>domain-name Customer.local;
>exit;

>do wr;

- Above lines denotes DHCP configuration for assigning ip for every device in each network automatically.

# Screenshot


# Wireless connectivity using access point device.

To provide Wi-Fi for smartphones, laptops, and tablets in your Cisco Packet Tracer office network, you can connect a wireless access point (AP) to your switch. The wireless devices will connect to the AP, and the AP will bridge their traffic into your office VLAN.

# Screenshot









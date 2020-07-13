# TCP/IP

## IP protocol
* Introduces IP addresses and submasks
* Responsible for routing information over from one IP to another over routers
* routing table based on network information (from mask)
* Internet addresses by allocated by InterNIC (the organization that administers the internet)

### Subnet mask

### Default gateway
* When the request is send when the router can not find desired IP on the current network

## TCP protocol
* once computers found each other over IP how they will communicate
* data are grouped into "packets"
* packets are send in groups

* "windowing" process by which the information is transmited
-> "client" send group of packets to server and wait for the confirmation of "last seen" packet
-> if the last packet is correct it makes the window "larger" try to send more packets at once
   or it may also decrease the window size and resend not confirmed packets

## DNS
* mapping of domain names to IP address
* distributed system of servers

## DHCP
* assignes dynamic IP address
* when computer connect to network it will send request to DHCP server which will return IP address, subnet mask, default gateway and DNS server
* another option would be to set this manually (static case) not that much fun
* the data are valid for some fixed period after which the computer re-request DHCP server

## NAT (Network address translation)
* each router connecting directly to internet need unique IP address (external IP)
* router has NAT table so that it knows how to send responses back do internal IP
* the main idea is that every device do not need unique IP address
* you can have NAT behind NAT and so on

## Subnet mask
* tell what part of IP address is network identifier and what part is device identifier

* A class subnet 255.0.0.0 (10.x.x.x)
* B class subnet 255.255.0.0 (172.16.x.x)
* C class subnet 255.255.255.0 (192.168.0.x)

* Consider a case when you have 192.168.0.x internal network (class C). You have then 254 addresses available and 150 devices, but you want to divide them into
  groups of 50, 50, 50 that can only communicate within the group. You can divide the network into 4 another networks using 2 extra bits for subnet 192.168.0.192   would be the network address. Therefore then will be 64 - 2 = 62 IP addresses available in each of the four subnets. The valid hosts will be:
  
   192.168.123.1-62
   192.168.123.65-126
   192.168.123.129-190
   192.168.123.193-254

* By changing subnet mask you can not increase the number of IP addresses but can restrict communication within those networks. (you just devide the range, and actually lost some IP addresses due to network/broadcast address for each subnet)

* if there are computers all connected to the same switch but not part of the same subnet, unless the router
  makes it possible they can not communicate with each other
* 192.168.1.1/255.255.255.0 (example)
* you should set subnet mask based on how many subnetworks you want to create resp. how many devices you
  want to have within one network
  


* 32 bits are divided into "a" bits for network and "b" bits for device
* you have 2^b - 2 options for device (excluding broadcast address with all ones and network address with all zeros)

* very well explained here https://support.microsoft.com/en-us/help/164015/understanding-tcp-ip-addressing-and-subnetting-basics




# TCP/IP

## IP protocol
* Introduces IP addresses and submasks
* Responsible for routing information over from one IP to another over routers

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


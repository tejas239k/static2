# static2
Another example of static routing with 3 routers sales, It and hr

#Router_Configurations#
#sales#
enable
configure terminal
hostname sales
interface fa0/0
ip address 192.168.1.1 255.255.255.0
no shutdown
exit
interface fa0/1
ip address 200.128.1.1 255.255.255.0
no shutdown
exit
ip route 152.168.0.0 255.255.0.0 200.128.1.2
#(ip route network subnet mask next hop)#

#it#
enable
configure terminal
hostname it
interface fa0/0
ip address 152.168.1.1 255.255.0.0
no shutdown
exit
interface fa0/1
ip address 200.128.1.2 255.255.255.0
no shutdown
exit
interface fa1/0
ip address 172.12.1.1 255.255.0.0
no shutdown
exit
ip route 192.168.1.0 255.255.255.0 200.128.1.1
ip route 10.0.0.0 255.0.0.0 172.12.1.2
#(ip route network subnet mask next hop)#

#hr#
enable
configure terminal
hostname hr
interface fa0/0
ip address 10.1.1.1 255.0.0.0
no shutdown
exit
interface fa0/1
ip address 172.12.1.2 255.255.255.0
no shutdown
exit
ip route 192.168.1.0 255.255.255.0 200.128.1.1
ip route 152.168.0.0 255.255.0.0 172.12.1.1
#(ip route network subnet mask next hop)#

# Networking-Assignment-3

Assignment 3

Listen

Hide Assignment Information

Instructions

Please watch the videos posted in the Bright Space (go to content tab table of contents -module labs 2) Chapters 3 and 4 vlan concepts and intervlan routing

Videos to watch:

to watch the videos go to content tab --- table of contents --- module --- LAB 2

VLAN parts 1-7 explains the vlan concepts

VLAN part 8-explains intervlan routing

LAB SCENARIO

Use 192.168.168.1.0/24 as the main network and create a VLSM Scheme for the following host requirements

Sales 20, Marketing 5

Use the following topologies to implement the Intervlan routing

1.Router on the stick

2 Layer 3 switch (3560 24-port multilayer switch in the packet tracer)

Pl Note: Attach the vism scheme along with the lab

Due on Sep 14, 2025 11:59 PM

Available on Sep 3, 2025 12:01 AM. Access restricted before availability starts.

Available until Dec 14, 2025 11:59 PM. Access restricted after availability ends.

Final Lab Commands

Floating Static route  (this should be configured on all 3 routers)
in the global configuration
# ip route   <destination nid> <destination subnet mask> <next hop router's ip address> 
<administrative distance more than 120 eg 121>

RIP :  (this should be configured on all 3 the routers>
router rip
version 2
network <nid of the network connected to LAN network>
network <nid of the network connected to another router>
no auto-summary

DHCP  on router (acting as DHCP server)
Ip dhcp excluded-address<ip address>
ip dhcp pool<poolname>
network <nid> <subnetmask>
default-router <ip address of the router>

Relay agent : this should be  configured on the relay agent router in the interface that is close to the dhcp client
#int <>
ip helper-address <ip address of the interface of the dhcp srv to which the relay agent connects>

Configuration on the switch:
Creating vlan

Switch(config)#vlan 10
Switch(config-vlan)#name <name of the vlan>
Switch(config-vlan)#int range fa0/1 - 10
Switch(config-if-range)#switchport mode access
Switch(config-if-range)#switchport access vlan 10
Switch(config-if-range)#exit
Trunk link configuration
Switch(config)#INT FA0/24
Switch(config-if)#switchport mode trunk
                 
Switch(config-if)#switchport trunk native vlan <vlan number> 


Show commands on switch:
Show vlan br : shows the vlan information in the switch
Show interfaces trunk: shows the configured trunk links on the lo switch and the vlans allowed through the trunk link
Show run: shows running configuration in the switch

Show commands on the router :
Show ip route : to see the router’s routing table
Show interfaces brief: gives brief info about the status of all the interfaces of the router
Show ip dhcp pool :  displays information about the configured DHCP pools
Show ip dhcp binding: view binding information for IP addresses and corresponding DHCP client hardware addresses.
Show run: shows running configuration in the router

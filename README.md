# Voice-VLANs

<h2>Description</h2>
Configure two VLANs, one for PCs and one for IP phones. Configure ROAS on router. Verify results with show/ping/traceroute.

<h2>Environments Used </h2>

- <b>Cisco Packet Tracer</b> (2.2.43) <br />

- <b>Cisco IOS 2800 Software, Version 15.1(4)M4</b>  <br />

- <b>Cisco IOS Denali, Catalyst L3 Switch Software, Version 16.3.2</b> <br />

[Software Configuration Guide](https://www.cisco.com/c/en/us/td/docs/switches/lan/catalyst3650/software/release/16-3/configuration_guide/b_163_consolidated_3650_cg.html)<br />

<h2>Diagram </h2>
<img src="https://i.imgur.com/dX80aU9.png" height="80%" width="80%" />

<h2>Walk-through:</h2>
SW1(config-if)#int range g1/0/2 - 3 <br />
SW1(config-if-range)#switchport mode access <br />
SW1(config-if-range)#switchport access vlan 10 <br />
SW1(config-if-range)#switchport voice vlan 20 <br />
SW1(config-if-range)#int g1/0/1 <br />	
SW1(config-if)#switchport mode trunk <br />
SW1(config-if)#switchport trunk allowed vlan 10,20 <br />
SW1(config-if)#do show vlan <br />
<img src="https://i.imgur.com/xbgjPgG.png" height="80%" width="80%" />
<br />
<br />
R1(config)#int f0/0.10
R1(config-subif)#encapsulation dot1q 10
R1(config-subif)#ip address 192.168.10.1 255.255.255.0
R1(config-subif)#no shut
R1(config-subif)#int f0/0.20
R1(config-subif)#encapsulation dot1q 20
R1(config-subif)#ip address 192.168.20.1 255.255.255.0
R1(config-subif)#no shut
R1(config-subif)#int f0/0
R1(config-if)#no shut
R1(config-if)#no shut
<img src="https://i.imgur.com/teD8Ayw.png" height="80%" width="80%" />
<br />
<br />
Verify results with show/ping/traceroute.
<img src="https://i.imgur.com/6Fzu1ii.png" height="80%" width="80%" />
<img src="https://i.imgur.com/xlWkk8h.png" height="80%" width="80%" />
<img src="https://i.imgur.com/cHCEJer.png" height="80%" width="80%" />
<img src="https://i.imgur.com/Sa11YMh.png" height="80%" width="80%" />

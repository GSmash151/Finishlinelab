#### ISP-R1
SET-UP Username & Password & SSH Encryption 
```c
enable password cisco
banner motd #UNAUTHORIZED ACCESS IS PROHIBITED!!!!#
no ip domain-lookup
service password-encryption
username cisco password cisco
ip domain-name finishline.com
crypto key generate rsa general-keys modulus 1024
line console 0
password cisco
login
exec-timeout 15 0
exit
ip ssh version 2
line vty 0 15
login local
transport input ssh
access-class 2 in 
exit 
do wr
```
Set-up Trunk to Data-SW
```c
interface fa0/0/0
switchport mode trunk
switchport trunk allowed vlan 10,20
no shutdown
exit
```
Set-up Trunk to DMZ-SW
```c
interface fa0/0/1
switchport mode trunk 
switchport trunk allowed vlan 50,60,70,80
no shutdown
exit
```
Set-up Trunk to DMZ-SW
```c
interface fa0/0/2
switchport mode trunk 
switchport trunk allowed vlan 40,90
no shutdown
exit
do wr
```
IP Address Configuration
```c
interface fa0/0/0
description Link to Data-SW
ip address 192.168.3.1 255.255.255.0
no shutdown
exit
interface fa0/0/1
description Link to DMZ-SWin
ip address 10.10.3.1 255.255.255.0
no shutdown
exit
interface fa0/0/2
description Link to Wire_SW
ip address 192.168.2.1 255.255.255.0
no shutdown
exit
interface se0/1/0
description Link to Cloud-Router
no shutdown
exit 
do wr
```
IP DHCP Excluded-Address Configuration
```c
ip dhcp excluded-address 192.168.3.1 192.168.3.10   ! Exclude for Data VLAN
ip dhcp excluded-address 192.168.5.1 192.168.5.10   ! Exclude for Voice VLAN
ip dhcp excluded-address 192.168.2.1 192.168.2.10   ! Exclude for Wireless VLAN
```
DHCP for Data VLAN 10 - `192.168.3.0/24`
```c
ip dhcp pool DATA_VLAN10
 network 192.168.3.0 255.255.255.0
 default-router 192.168.3.1
 dns-server 10.10.3.1
 domain-name finishline.com
```
DHCP for Voice VLAN 20 - `192.168.5.0/24`
```c
ip dhcp pool VOICE_VLAN20
network 192.168.5.0 255.255.255.0
default-router 192.168.5.1
dns-server 10.10.3.1
domain-name finishline.com
```
DHCP for Wireless VLAN  90 - `192.168.2.0/24`
```c
ip dhcp pool WIRELESS_VLAN90
network 192.168.2.0 255.255.255.0
default-router 192.168.2.1
dns-server 10.10.3.1
domain-name finishline.com
```
OSPF Configuration
```c
router ospf 1
 network 192.168.3.0 0.0.0.255 area 0    ! Data Network
 network 10.10.3.0 0.0.0.255 area 0      ! DMZ Network
 network 192.168.2.0 0.0.0.255 area 0    ! Wireless Network
```
#### Data-SW & DMZ-SW &  Wireless-SW
Username&Password&SSH Encryption
```c
enable password cisco
banner motd #UNAUTHORIZED ACCESS IS PROHIBITED!!!!#
no ip domain-lookup
service password-encryption
username cisco password cisco
ip domain-name finishline.com
crypto key generate rsa general-keys modulus 1024
line console 0
password cisco
login
exec-timeout 15 0
exit
ip ssh version 2
line vty 0 15
login local
transport input ssh
access-class 2 in 
exit 
do wr
```
#### Data-SW 
Set Vlans
```c
vlan 10
 name PCs_Printers
vlan 20
 name Voice
```
Trunk to Router
```c
interface gig0/1
 switchport mode trunk
 switchport trunk allowed vlan 10,20
```
Access Ports
```c
intface fa0/1
switchport mode access
switchport nonegotiate 
switchport access vlan 10
switchport voice vlan 20
no shutdown
exit
intface fa0/2
switchport mode access
switchport nonegotiate 
switchport access vlan 10
switchport voice vlan 20
no shutdown
exit
intface fa0/3
switchport mode access
switchport nonegotiate 
switchport access vlan 10
switchport voice vlan 20
no shutdown
exit
intface fa0/4
switchport mode access
switchport nonegotiate 
switchport access vlan 10
no shutdown
exit
intface fa0/5
switchport mode access
switchport nonegotiate 
switchport access vlan 10
no shutdown
exit
do wr
```
Spanning-Tree Configuration 
```c
spanning-tree mode rapid-pvst
interface range fastEthernet0/1-5
spanning-tree portfast trunk
spanning-tree bpduguard enable
exit
spanning-tree vlan 10,20 priority 4096
```
#### DMZ-SW
Set Vlans
```c
vlan 50
 name EMAIL_Servers
vlan 60
 name FTP_Servers
vlan 70
 name DNS_Servers
vlan 80
 name WEB_Servers
```
Trunking to Router
```c
interface gig0/1
switchport mode trunk
switchport trunk allowed vlan 50,60,70,80
```
Access Ports
```c
interface fa0/1
 switchport mode access
 switchport nonegotiate 
 switchport access vlan 50  ! EMAIL Server
 no shutdown

interface fa0/2
 switchport mode access
 switchport nonegotiate 
 switchport access vlan 60  ! FTP Server
 no shutdown

interface fa0/3
 switchport mode access
 switchport nonegotiate 
 switchport access vlan 70  ! DNS Server
 no shutdown

interface fa0/4
 switchport mode access
 switchport nonegotiate 
 switchport access vlan 80  ! WEB Server
 no shutdown
```
Spanning-Tree Configuration
```c
spanning-tree mode rapid-pvst
interface range fastEthernet0/1-4
spanning-tree portfast trunk
spanning-tree bpduguard enable
exit
spanning-tree vlan 50,60,70,80 priority 4096
```
#### Wire-SW
Set Vlans
```c
vlan 90
 name Wireless
vlan 40
 name Management
```
Interface Configuration
```c
interface gig0/1
switchport mode trunk
switchport trunk allowed vlan 40,90
no shutdown
exit
interface fa0/1
switchport mode access
switchport access vlan 40  ! Management PC
no shutdown
```
Access Points for Wireless VLAN
```c
interface gig0/2
switchport mode access
switchport access vlan 90  ! Access Point for 3 Laptops
```
Spanning-Tree Configuration:
```c
spanning-tree mode rapid-pvst
spanning-tree vlan 40,90 priority 4096
```
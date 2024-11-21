#### FinishLine Switch 1

Set Trunk
```
interface range g0/1-2
switchport mode trunk
switchport nonegotiate
switchport trunk native vlan 1000
switchport trunk allowed vlan 10,20,30,40,99
interface po1
switchport mode trunk
switchport nonegotiate
switchport trunk native vlan 1000
switchport trunk allowed vlan 10,20,30,40,99
```
VTP & DOMAIN 
```
vtp domain FinishlineLab
vtp version
```
VLAN
```
vlan 10
name Web Server
vlan 20
name PC-A
vlan 30
name Receptionist-A
vlan 40
name FLAP-1
vlan 99
name Management
```

DCHP Pool
```
ip dhcp excluded-address 192.168.3.1 192.168.4.1
ip dhcp pool LAN_POOL
network 192.168.3.0 255.255.255.0
default-router 192.168.3.1
dns-server 8.8.8.8
lease infinite
```
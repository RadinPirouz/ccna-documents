# 🌐 Interface & IP Information

## Interface Details

```bash
show interface status
show interface FastEthernet 0/1
show interfaces FastEthernet 0/1 switchport
````

## IP Interface Overview

```bash
show ip interface brief
```

## Assign IP to VLAN Interface

```bash
interface vlan 30
ip address 192.168.1.100 255.255.255.0
no shutdown
exit
```

```bash
interface vlan 10
ip address 192.168.1.1 255.255.255.255
exit
```

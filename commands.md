# 🛠️ Cisco CLI Commands – Quick Reference Guide

A handy reference for essential Cisco IOS commands.

---

## 🔄 Reboot the Device

Reload (reboot) the switch or router:

```bash
reload
```

---

## 📝 Configuration Management

### Show Configurations

Current running configuration:

```bash
show running-config
```

Saved startup configuration:

```bash
show startup-config
```

Show running config for a specific interface:

```bash
show running-config interface FastEthernet 0/1
```

### Set Hostname

Change the device name:

```bash
hostname <new-hostname>
```

### Save Configuration

Save running config to NVRAM:

```bash
wr
```

Manually copy to startup config:

```bash
copy running-config startup-config
```

Copy to flash:

```bash
copy running-config flash:
```

---

## 🗃️ File and Memory Management

Read file contents:

```bash
more <file-name>
```

Delete a file:

```bash
delete <file-name>
```

Erase the startup configuration:

```bash
erase startup-config
```

Format flash memory:

```bash
format flash:
```

---

## 🌐 Interface & IP Information

### Interface Details

Show detailed status:

```bash
show interface status
```

Show specific interface details:

```bash
show interface FastEthernet 0/1
```

Show switchport config of an interface:

```bash
show interfaces FastEthernet 0/1 switchport
```

### IP Interface Overview

Brief summary of IP interfaces:

```bash
show ip interface brief
```

### VLAN & Trunk Info

Show VLANs:

```bash
show vlan
show vlan brief
```

Show trunking ports:

```bash
show interfaces trunk
```

---

## 🌐 VLAN Configuration Examples

### Create VLAN

```bash
configure terminal
vlan 10
name MyVLAN
exit
```

### Create Multiple VLANs

```bash
configure terminal
vlan 30,40
name MyVLAN
exit
```

### Delete VLAN

```bash
no vlan 10
```

### Assign VLAN to Port

```bash
configure terminal
interface FastEthernet 0/1
switchport mode access
switchport access vlan 10
exit
```

### Assign VLAN to Port Range (Examples)

```bash
configure terminal
interface range FastEthernet 0/1 , FastEthernet 0/5
switchport mode access
switchport access vlan 20
exit
```

```bash
configure terminal
interface range FastEthernet 0/1 - 5
switchport mode access
switchport access vlan 20
exit
```

---

## 🧰 Additional Useful Commands

Routing table:

```bash
show ip route
```

Device version & hardware info:

```bash
show version
```

Neighbor devices (CDP):

```bash
show cdp neighbors
```

MAC address table:

```bash
show mac address-table
```

Ping:

```bash
ping <destination-ip>
```

Traceroute:

```bash
traceroute <destination-ip>
```

---

## 🔍 Switchport Types

* **Access** – Dedicated to a single VLAN
* **Trunk** – Carries multiple VLANs
* **Dynamic Auto** – Negotiates trunking with the peer


```
interface vlan 30 
ip address 192.168.1.100 255.255.255.0
no shutdown
exit
```
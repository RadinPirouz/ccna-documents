# 🛠️ Cisco CLI Commands – Quick Reference Guide

A categorized reference for essential Cisco IOS commands.

---

## 📁 Categories

* [🔄 Device Reboot](#-device-reboot)
* [📝 Configuration Management](#-configuration-management)
* [🗃️ File & Memory Management](#-file--memory-management)
* [🌐 Interface & IP Info](#-interface--ip-info)
* [🔧 VLAN Management](#-vlan-management)
* [🔒 Console & Password Security](#-console--password-security)
* [📡 Trunking & Encapsulation](#-trunking--encapsulation)
* [🧰 Miscellaneous Useful Commands](#-miscellaneous-useful-commands)

---

## 🔄 Device Reboot

```bash
reload
```

---

## 📝 Configuration Management

### Show Configuration

```bash
show running-config
show startup-config
show running-config interface FastEthernet 0/1
```

### Set Hostname

```bash
hostname <new-hostname>
```

### Save Configuration

```bash
wr
copy running-config startup-config
copy running-config flash:
```

---

## 🗃️ File & Memory Management

```bash
more <file-name>
delete <file-name>
erase startup-config
format flash:
```

---

## 🌐 Interface & IP Info

### Interface Details

```bash
show interface status
show interface FastEthernet 0/1
show interfaces FastEthernet 0/1 switchport
```

### IP Interface Overview

```bash
show ip interface brief
```

### Assign IP to VLAN

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

---

## 🔧 VLAN Management

### Show VLAN Info

```bash
show vlan
show vlan brief
show vlan-switch
```

### Create/Delete VLANs

```bash
vlan 10
name MyVLAN
exit
no vlan 10
```

```bash
vlan 30,40
name MyVLAN
exit
```

### Assign VLAN to Interfaces

```bash
interface FastEthernet 0/1
switchport mode access
switchport access vlan 10
exit
```

```bash
interface range FastEthernet 0/1 , FastEthernet 0/5
switchport mode access
switchport access vlan 20
exit
```

```bash
interface range FastEthernet 0/1 - 5
switchport mode access
switchport access vlan 20
exit
```

```bash
interface FastEthernet 0/1
no switchport access vlan 10
exit
```

```bash
interface range FastEthernet 0/1-4
switchport mode access
switchport access vlan 10
switchport voice vlan 30
exit
```

---

## 🔒 Console & Password Security

### Basic Console Password

```bash
line console 0
password 123
login
```

### Encrypted Console Password

```bash
service password-encryption
line console 0
password 123
login
enable secret 123
```

### SHA-256 Encrypted Console + Enable Password

```bash
service password-encryption
line console 0
password 123
login
enable algorithm-type sha-256 secret 123
```

### Local User Authentication with SHA-256

```bash
service password-encryption
line console 0
login local
enable algorithm-type sha-256 secret 123
username radin algorithm-type sha-256 secret 123
```

---

## 📡 Trunking & Encapsulation

### Trunk Concepts

* **Trunk Modes**:

  * ISL (Inter Switch Link)
  * IEEE 802.1Q

**802.1Q Tag Fields (4 bytes)**:

* Type (16 bits): `0x8100`
* Priority (3 bits)
* Flag (1 bit)
* VLAN ID (12 bits)

### Trunk Configuration Examples

#### Basic Trunking

```bash
interface FastEthernet 0/1
switchport trunk encapsulation dot1q
switchport mode trunk
vtp mode off
exit
```

#### Allow Specific VLANs

```bash
interface FastEthernet 0/1
switchport trunk encapsulation dot1q
switchport mode trunk
switchport trunk allow vlan 10,20
vtp mode off
exit
```

#### Add VLAN to Trunk

```bash
interface FastEthernet 0/1
switchport trunk encapsulation dot1q
switchport mode trunk
switchport trunk allow vlan 10,20
switchport trunk allow vlan add 30
vtp mode off
exit
```

#### Exclude VLANs from Trunk

```bash
interface FastEthernet 0/1
switchport trunk encapsulation dot1q
switchport mode trunk
switchport trunk allow vlan except 10,20
vtp mode off
exit
```

### Show Trunk Info

```bash
show interfaces trunk
```

---

## 🧰 Miscellaneous Useful Commands

```bash
show ip route
show version
show cdp neighbors
show mac address-table
ping <destination-ip>
traceroute <destination-ip>
switchport nonegotiate
```

```
copy flash: tftp:
```

```
copy tftp: flash:
```

banner:
```
banner motd #
```

```
boot system tftp <ios-name> <tftp-server-ip>
```
```
boot system flash:<ios-name>
```

```
IP_ADDRESS=<ip>
IP_SUBNET_MASK=<subnet-ip>
DEFAULT_GATEWAY=<DEFAULT_GATEWAY>
TFTP_SERVER=<tftp-ip>
TFTP_FILE=<file-name>
Set
tftpdnld
```

reset password on switch
```
flash_init
dir flash:
rename flash:config.text flash:sematec.text
boot
```
reset password on router
config-register
0x2102 --> normal opration
0x2142 --> password recovery
```
confreg 0x2142
boot
copy startup-config running-config
wr
reload and break
confreg 0x2102
boot
```
# 📡 Trunking & Encapsulation

## Trunking Concepts

- **Trunk Modes**:
  - ISL (Inter-Switch Link)
  - IEEE 802.1Q

**802.1Q Tag Fields (4 bytes):**

- Type (16 bits): `0x8100`
- Priority (3 bits)
- Flag (1 bit)
- VLAN ID (12 bits)

## Trunk Configuration Examples

### Basic Trunking

```bash
interface FastEthernet 0/1
switchport trunk encapsulation dot1q
switchport mode trunk
vtp mode off
exit
````

### Allow Specific VLANs

```bash
interface FastEthernet 0/1
switchport trunk encapsulation dot1q
switchport mode trunk
switchport trunk allow vlan 10,20
vtp mode off
exit
```

### Add VLAN to Trunk

```bash
interface FastEthernet 0/1
switchport trunk encapsulation dot1q
switchport mode trunk
switchport trunk allow vlan 10,20
switchport trunk allow vlan add 30
vtp mode off
exit
```

### Exclude VLANs from Trunk

```bash
interface FastEthernet 0/1
switchport trunk encapsulation dot1q
switchport mode trunk
switchport trunk allow vlan except 10,20
vtp mode off
exit
```

## Show Trunk Info

```bash
show interfaces trunk
```

# 📡 Trunking & Encapsulation

## 🌐 Trunking Concepts

### 🔌 Trunk Modes

* **ISL (Inter-Switch Link)** – Cisco proprietary
* **IEEE 802.1Q** – Industry standard for VLAN tagging

### 🏷️ 802.1Q Tag Fields (4 Bytes)

| Field    | Size    | Description                                          |
| -------- | ------- | ---------------------------------------------------- |
| Type     | 16 bits | Always `0x8100`                                      |
| Priority | 3 bits  | Class of Service (CoS)                               |
| CFI/DEI  | 1 bit   | Canonical Format Indicator / Drop Eligible Indicator |
| VLAN ID  | 12 bits | Identifies VLAN (0–4095)                             |

---

## ⚙️ Trunk Configuration Examples

### 1️⃣ Basic Trunking

```bash
interface FastEthernet0/1
 switchport trunk encapsulation dot1q
 switchport mode trunk
 vtp mode off
exit
```

---

### 2️⃣ Allow Specific VLANs

```bash
interface FastEthernet0/1
 switchport trunk encapsulation dot1q
 switchport mode trunk
 switchport trunk allow vlan 10,20
 vtp mode off
exit
```

---

### 3️⃣ Add VLAN to Trunk

```bash
interface FastEthernet0/1
 switchport trunk encapsulation dot1q
 switchport mode trunk
 switchport trunk allow vlan 10,20
 switchport trunk allow vlan add 30
 vtp mode off
exit
```

---

### 4️⃣ Exclude VLANs from Trunk

```bash
interface FastEthernet0/1
 switchport trunk encapsulation dot1q
 switchport mode trunk
 switchport trunk allow vlan except 10,20
 vtp mode off
exit
```

---

### 5️⃣ Set Native VLAN

```bash
switchport trunk native vlan <vlan-number>
```

---

### 6️⃣ Disable DTP (Dynamic Trunking Protocol)

```bash
switchport nonegotiate
```

---

## 🔍 Show Commands

### View Trunk Interface Details

```bash
show interfaces trunk
```

### Show Switchport Settings

```bash
show interface FastEthernet0/1 switchport
```

### Show DTP Status

```bash
show dtp
```


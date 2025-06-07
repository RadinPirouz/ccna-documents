# 🌐 Spanning Tree Protocol Guard Features

This document outlines key Spanning Tree Protocol (STP) guard features used to enhance network stability and security by controlling how switches handle BPDUs (Bridge Protocol Data Units).

---

## 🔒 Root Guard

**Purpose:**
Prevents a designated port from becoming a root port if superior BPDUs are received unexpectedly, protecting the existing STP topology.

**Configuration Example:**

```bash
interface FastEthernet0/1
 spanning-tree guard root
exit
```

**Use Case:**
Deploy on designated ports leading to other switches where you do **not** expect the root bridge to appear.

---

## 🚫 BPDU Guard

**Purpose:**
Automatically disables a port (err-disabled) if BPDUs are received on a PortFast (edge) port. Prevents accidental or malicious STP participation.

**Configuration Example (Interface Level):**

```bash
interface FastEthernet0/1
 spanning-tree bpduguard enable
exit
```

### 🔧 Recovery and Monitoring Commands

Check disabled ports and enable automatic recovery:

```bash
show interface status err-disabled
errdisable recovery cause bpduguard
show errdisable recovery
errdisable recovery interval 600
```

### 🌍 Global Configuration Default (Optional)

Apply BPDU Guard to all edge (PortFast) ports globally:

```bash
spanning-tree portfast edge default
spanning-tree bpduguard default
```

---

## 🔁 Loop Guard

**Purpose:**
Prevents a non-designated port from transitioning to forwarding if it stops receiving BPDUs, which might otherwise cause loops.

**Global Configuration:**

```bash
spanning-tree loopguard default
```

**Use Case:**
Recommended on non-edge switch-to-switch links, especially in large or meshed topologies.

---

## ⚠️ BPDU Filter

**Purpose:**
Suppresses the sending or receiving of BPDUs. This can prevent participation in STP altogether but is **dangerous** if misused.

**Per-Interface Configuration:**

```bash
interface Ethernet0/1
 spanning-tree bpdufilter enable
```

**Global Default Configuration:**

```bash
spanning-tree portfast edge default
spanning-tree bpdufilter default
```

> ⚠️ **Warning:**
> Avoid enabling BPDU Filter on interfaces connected to other switches unless you're absolutely sure about the topology impact. It can lead to undetected loops if not used carefully.

---

## ✅ Summary Table

| Feature         | Purpose                                          | Recommended Use Case                 |
| --------------- | ------------------------------------------------ | ------------------------------------ |
| **Root Guard**  | Blocks a port from becoming root port            | Access/Distribution ports            |
| **BPDU Guard**  | Err-disables ports receiving BPDUs               | Edge/Access ports with PortFast      |
| **Loop Guard**  | Prevents loops from unidirectional link failures | Trunk ports, switch interconnections |
| **BPDU Filter** | Suppresses BPDU transmission and reception       | Rare, controlled environments only   |

---

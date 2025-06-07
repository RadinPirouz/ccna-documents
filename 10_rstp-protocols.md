Here's a cleaned-up, well-structured, and visually appealing Markdown document based on your notes. I’ve corrected spelling, grammar, formatting, and configuration errors where needed.

---

# 🌐 Rapid Spanning Tree Protocol (RSTP) Cheat Sheet

## 🔄 Spanning-Tree Mode Configuration

```bash
spanning-tree mode rapid-pvst
```

Enable Rapid-PVST+ mode on the switch.

---

## 🌱 Port States in RSTP

| State          | Description                              |
| -------------- | ---------------------------------------- |
| **Discarding** | Drops frames (similar to STP Listening)  |
| **Learning**   | Learns MAC addresses but doesn't forward |
| **Forwarding** | Forwards frames and learns MAC addresses |

---

## 🧭 Port Roles

| Role                | Description                                    |
| ------------------- | ---------------------------------------------- |
| **Root Port**       | Port closest to the root bridge (one per VLAN) |
| **Designated Port** | Forwarding port for a segment                  |
| **Alternate Port**  | Backup to the Root Port                        |
| **Backup Port**     | Backup to the Designated Port (same segment)   |

> ⚠️ Note: "Designated Port" should **not** be blocked; the **Alternate** and **Backup** roles are **blocking** roles.

---

## 🔌 Port Types

| Type               | Description                                                          |
| ------------------ | -------------------------------------------------------------------- |
| **Edge Port**      | Directly connects to end devices (e.g., PCs). Enabled with PortFast. |
| **Point-to-Point** | Connects RSTP-enabled switches (requires full duplex).               |
| **Root Port**      | As per RSTP, the port with the best path to the root bridge.         |

---


## 📨 BPDUs in RSTP

| Type               | Description                     |
| ------------------ | ------------------------------- |
| **Proposal BPDU**  | Used to propose a new port role |
| **Agreement BPDU** | Used to acknowledge a proposal  |

---


## ⚙️ Basic Configuration

### Set Root Bridge Priority

```bash
spanning-tree vlan 1-4094 priority 0
```

Makes this switch the root bridge by setting the lowest possible priority.

### Show Spanning-Tree Details

```bash
show spanning-tree detail
```

```bash
show spanning-tree interface <interface> detail
```

---

## ⚡ PortFast (Edge Port)

### Enable PortFast Globally

```bash
spanning-tree portfast edge default
```

### Enable PortFast on a Specific Interface

```bash
interface FastEthernet0/1
spanning-tree portfast edge
exit
```

---

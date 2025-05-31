# 🌲 Spanning Tree Protocol (STP) Overview

The **Spanning Tree Protocol (STP)** prevents Layer 2 network loops by creating a loop-free logical topology. It ensures only one active path exists between switches, blocking redundant paths until they are needed (e.g., during a failure).

---

## 🧬 STP Variants

| Protocol                | IEEE Standard | Description                                  |
| ----------------------- | ------------- | -------------------------------------------- |
| **STP (PVST+)**         | 802.1D        | Per-VLAN STP used in Cisco networks          |
| **Rapid STP (RSTP)**    | 802.1W        | Faster convergence than traditional STP      |
| **Multiple STP (MSTP)** | 802.1S        | Maps multiple VLANs to a single STP instance |

> 🔹 **Note**: PVST+ supports up to **128 STP instances** (1 per VLAN).

---

## 🏛 Root Bridge

* Serves as the **central reference point** in the STP topology.
* **Default Bridge Priority**: `32768`
* **Bridge ID** = Priority + MAC Address
  Example: `32768.AA:AA:AA:AA:AA:AA`
* Priority values must be **multiples of 4096**:
  `0, 4096, 8192, ..., 61440`
* **BPDU (Bridge Protocol Data Unit)** carries the Bridge ID.

> 📘 For VLANs, the bridge priority is:
> `32768 + VLAN ID`

---

## ⚙️ STP Path Cost by Bandwidth

| Bandwidth | Cost |
| --------- | ---- |
| 10 Gbps   | 2    |
| 1 Gbps    | 4    |
| 100 Mbps  | 19   |
| 10 Mbps   | 100  |

Path cost helps determine the best path to the root bridge.

---

## 🔌 STP Port Roles

* **Root Port (RP)**:
  The port on a non-root switch with the **lowest path cost** to the root bridge.

* **Designated Port (DP)**:
  One per segment; **forwards traffic** towards and from that segment.

* **Blocked Port**:
  Prevents loops by **not forwarding traffic**. It only listens for BPDUs.

---

## 🔍 Useful STP Commands (Cisco)

```bash
show spanning-tree
show spanning-tree summary
```

---

## 🔄 Path Cost Calculation Mode

To adjust how path cost is computed based on interface bandwidth:

```bash
spanning-tree pathcost method <short | long>
```

* `short`: Legacy method (up to 1 Gbps)
* `long`: Modern method (supports speeds above 1 Gbps)

---

## 🚦 STP Modes

```bash
spanning-tree mode <pvst | rapid-pvst | mst>
```

* `pvst`: Per VLAN Spanning Tree (Cisco proprietary)
* `rapid-pvst`: Rapid PVST (faster convergence)
* `mst`: Multiple Spanning Tree (groups VLANs into instances)

---

## ⏱ BPDU Timers

| Timer             | Default | Description                             |
| ----------------- | ------- | --------------------------------------- |
| **Hello Time**    | 2 sec   | Interval between BPDU transmissions     |
| **Forward Delay** | 15 sec  | Listening → Learning → Forwarding delay |
| **Max Age**       | 20 sec  | Time switch retains BPDU info           |

> 🧠 These values are set by the **Root Bridge** and advertised via BPDUs.

---

## 🔁 STP Port States

### Active Ports (Root & Designated)

* **Listening**: Receives BPDUs only (15 sec)
* **Learning**: Learns MAC addresses (15 sec)
* **Forwarding**: Sends/receives traffic and BPDUs

### Inactive Ports

* **Blocking**: Receives BPDUs, does **not** forward traffic

> ⌛ Total time before forwarding: **30 seconds** (15s Listening + 15s Learning)

---

## 🌀 Topology Changes

* **Direct Topology Change**:
  Caused by an immediate event (e.g., a link goes down).
  → Convergence time: **30 seconds**

* **Indirect Topology Change**:
  Caused by an upstream or multi-hop event.
  → Convergence time: **50 seconds**
  *(20s Max Age + 15s Listening + 15s Learning)*

---

## 🔔 Topology Change Notification (TCN)

* **TCN BPDU** is sent by a switch detecting a change.
* Propagates to the root bridge.
* Root bridge then sends configuration BPDUs with the **TCN flag** set.
* Triggers **MAC address table flush** to update forwarding.

---

## 📜 Summary of BPDU Timers & Port Behavior

| Role                | Port State Sequence               | Time to Forwarding |
| ------------------- | --------------------------------- | ------------------ |
| **Root Port**       | Listening → Learning → Forwarding | 30 seconds         |
| **Designated Port** | Listening → Learning → Forwarding | 30 seconds         |
| **Blocked Port**    | Blocking                          | N/A                |


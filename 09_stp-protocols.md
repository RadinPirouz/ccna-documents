# 🌲 Spanning Tree Protocol (STP) Overview

## 🧬 STP Variants

| Protocol                | IEEE Standard | Description                                  |
| ----------------------- | ------------- | -------------------------------------------- |
| **STP (PVST+)**         | 802.1D        | Per-VLAN STP used in Cisco networks          |
| **Rapid STP (RSTP)**    | 802.1W        | Faster convergence than traditional STP      |
| **Multiple STP (MSTP)** | 802.1S        | Maps multiple VLANs to a single STP instance |

> 🔹 **Limit**: Up to **128 STP instances** (1 STP instance per VLAN in PVST+)

---

## 🏛 Root Bridge

* Acts as the **central reference point** in an STP topology.
* **Default bridge priority**: `32768`.
* **Bridge ID** = Priority + MAC Address
  Example: `32768.AA:AA:AA:AA:AA:AA`
* Priority values must be **multiples of 4096**:
  `0, 4096, 8192, ..., 61440`
* **BPDU (Bridge Protocol Data Unit)** carries the Bridge ID.

> In VLANs, bridge priority is calculated as:
> `32768 + VLAN ID`

---

## ⚙️ STP Path Cost by Bandwidth

| Bandwidth | Cost |
| --------- | ---- |
| 10 Gbps   | 2    |
| 1 Gbps    | 4    |
| 100 Mbps  | 19   |
| 10 Mbps   | 100  |

---

## 🔌 STP Port Roles

* **Root Port**:
  Port on a non-root switch with the **lowest path cost** to the root bridge.

* **Designated Port**:
  One per segment; **forwards traffic** towards and from that segment.

* **Blocked Port**:
  Prevents loops by **not forwarding traffic**.

---

## 🔍 Useful STP Commands (Cisco)

```bash
show spanning-tree
show spanning-tree summary
```

---

## 🔄 Path Cost Calculation Mode

Sets how path cost is computed based on interface bandwidth:

```bash
spanning-tree pathcost method <short | long>
```

* `short`: Legacy method (max speed 1 Gbps)
* `long`: Modern method (supports speeds above 1 Gbps)

---

## 🚦 STP Modes

```bash
spanning-tree mode <pvst | rapid-pvst | mst>
```

* `pvst`: Per VLAN Spanning Tree (Cisco)
* `rapid-pvst`: Rapid PVST (faster convergence)
* `mst`: Multiple Spanning Tree (groups VLANs)

---

## ⏱ BPDU Timers

| Timer             | Value  | Description                             |
| ----------------- | ------ | --------------------------------------- |
| **Hello Time**    | 2 sec  | Time between BPDU transmissions         |
| **Forward Delay** | 15 sec | Listening → Learning → Forwarding delay |
| **Max Age**       | 20 sec | Time a switch stores BPDU info          |

---

## 🔁 STP Port States

### Root & Designated Ports

* **Listening**: Receives BPDUs only (15 sec)
* **Learning**: Learns MACs, still no forwarding (15 sec)
* **Forwarding**: Fully operational

### Blocked Port

* **Blocking**: Receives BPDUs, does not forward traffic

---

## 🌀 Topology Changes

* **Direct Topology Change**:
  Immediate changes, such as a directly connected link going down.

* **Indirect Topology Change**:
  Changes due to multiple hops or indirect link failure.

---

## 🔔 TCN (Topology Change Notification)

* TCN BPDU is sent to notify the root bridge of a topology change.
* Triggers MAC address table flush to ensure accurate forwarding.

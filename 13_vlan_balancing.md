# **🔀 VLAN Load Balancing with Spanning Tree Protocol (STP)**

## **🎯 Objective**

Implement VLAN load balancing by modifying Spanning Tree Protocol (STP) parameters to optimize traffic distribution across two uplink ports: **Ethernet 0/2** and **Ethernet 0/3**.

---

## **⚙️ Initial STP Configuration**

By default, on **all VLANs**:

* 🔵 **Ethernet 0/2** → **Root Port**
* 🟢 **Ethernet 0/3** → **Designated Port**

---

## **⚖️ Load Balancing Strategy**

### **📌 Method 1: Modifying STP Path Cost**

To shift root port roles for **VLANs 10 and 20**, configure the path cost on **Ethernet 0/3**:

```bash
interface ethernet 0/3
spanning-tree vlan 10,20 cost 90
```

### **🔄 Effect After Change:**

* **VLANs 10 and 20**:

  * 🟢 **Ethernet 0/3** → **Root Port**
  * 🔵 **Ethernet 0/2** → **Designated Port**

* **Other VLANs**:

  * 🔵 **Ethernet 0/2** → **Root Port**
  * 🟢 **Ethernet 0/3** → **Designated Port**

### **🛡️ Failover Behavior:**

If **Ethernet 0/3** is **shut down**:

* 🔄 **Ethernet 0/2** becomes the **Root Port for all VLANs** ✅

---

### **📌 Method 2: Modifying Port Priority**

Alternatively, you can lower the port priority on Ethernet 0/3:

```bash
interface ethernet 0/3
spanning-tree vlan 10,20 port-priority 64
```

💡 **Note:** A lower port priority increases the chance of a port becoming the Root Port.

---

## **📊 Summary**

By adjusting STP settings, you can:

* 🔁 Distribute VLAN traffic between ports for load balancing.
* 💡 Use **cost** or **priority** to control root port selection.
* ✅ Ensure high availability and failover protection.


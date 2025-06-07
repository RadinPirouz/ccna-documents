# 📡 Cisco Discovery Protocol (CDP) & UDLD Notes

---

## 🔍 Cisco Discovery Protocol (CDP)

CDP is a Layer 2 protocol used to discover information about directly connected Cisco devices.

### 🔧 Useful Command

```bash
show cdp neighbors
```

This command displays a list of directly connected Cisco devices and their interface information.

---

## 🔄 UDLD (Unidirectional Link Detection)

UDLD is used to detect and prevent unidirectional links, which can cause network issues like loops or black holes.

### 🕒 Behavior

* Sends UDLD messages **every 15 seconds**
* **Switch 1:** Sends
* **Switch 2:** Replies
* If no response after **3 attempts**, and action is **enabled**, a response is triggered.

### ⚙️ UDLD Modes

| Mode            | Action Taken                                                  |
| --------------- | ------------------------------------------------------------- |
| **Normal Mode** | Only logs to **Syslog**                                       |
| **Aggressive**  | Logs to **Syslog** and puts the port in **err-disable** state |

---

## 📘 UDLD Commands

### 🔍 Show UDLD Neighbors

```bash
show udld neighbor
```

### 📊 Show UDLD Status

```bash
show udld
```

### ♻️ Reset UDLD State

```bash
udld reset
```

### ⚡ Enable UDLD on Interface (Aggressive Mode)

```bash
interface ethernet 0/0
udld port aggressive
```


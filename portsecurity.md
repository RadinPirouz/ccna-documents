# 🔐 Port Security Configuration and Monitoring Commands

## 📊 Display Port Security Information

```bash
show port-security
```

🔎 Displays port security status and statistics for all switch ports.

```bash
show port-security-address
```

🔎 Shows the secure MAC addresses configured on the switch.

```bash
show port-security interface <type> <mod/num>
```

🔎 Displays port security information for a specific interface.
💡 *Example:*

```bash
show port-security interface gigabitEthernet 1/0/1
```

---

## ⚙️ Configure Port Security

```bash
switchport port-security
```

✅ Enables port security on the interface.

```bash
switchport port-security maximum 1
```

📏 Sets the **maximum number** of secure MAC addresses allowed on the interface.

```bash
switchport port-security mac-address <mac>
```

🔒 Manually configures a secure MAC address.
💡 *Example:*

```bash
switchport port-security mac-address 00A1.B2C3.D4E5
```

```bash
switchport port-security violation <mode>
```

🚨 Specifies the action to take when a security violation occurs.

**Available Modes:**

* 🛑 `shutdown` – Disables the port (err-disabled).
* 🚫 `restrict` – Drops packets & logs the violation.
* 🛡️ `protect` – Drops packets silently without logging.

```bash
switchport port-security mac-address sticky
```

📌 Enables **sticky MAC address learning**, so dynamically learned addresses become secure.

---

## 🧹 Clear Port Security Entries

```bash
clear port-security dynamic
```

🧼 Clears dynamically learned secure MAC addresses.

```bash
clear port-security static
```

🧼 Clears statically configured secure MAC addresses.


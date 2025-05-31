# 🧰 Miscellaneous Useful Commands

```bash
show ip route
show version
show cdp neighbors
show mac address-table
ping <destination-ip>
traceroute <destination-ip>
````

### File Transfer

```bash
copy flash: tftp:
copy tftp: flash:
```

### Banner Message

```bash
banner motd #
```

### Boot System

```bash
boot system tftp <ios-name> <tftp-server-ip>
boot system flash:<ios-name>
```

### Password Recovery - Switch

```bash
flash_init
dir flash:
rename flash:config.text flash:backup.text
boot
```

### Password Recovery - Router

```bash
confreg 0x2142
boot
copy startup-config running-config
wr
reload and break
confreg 0x2102
boot
```

### Subinterface Configuration (Router-on-a-stick)

```bash
interface fastEthernet 0/0.10
encapsulation dot1Q 10
ip address 192.168.10.1 255.255.255.0
exit
```

```bash
interface fastEthernet 0/0.50
encapsulation dot1Q 50 native
ip address 192.168.50.1 255.255.255.0
exit
```

# Cisco CLI Commands – Quick Reference

## Reboot the Switch or Router
Reload the device:
```bash
reload
```

## Show Configurations
View the current running configuration:
```bash
show running-config
```

View the saved startup configuration:
```bash
show startup-config
```

## Set Hostname
Change the device hostname:
```bash
hostname <new-name>
```

## Save Configuration
Save the running configuration to memory:
```bash
wr
```

Alternatively, copy the running config manually:
```bash
copy running-config startup-config
```

Copy the running config to flash storage:
```bash
copy running-config flash:
```

## Manage Files
Read file contents:
```bash
more <file-name>
```

Delete a file:
```bash
delete <file-name>
```

Erase the startup configuration:
```bash
erase startup-config
```

Format the flash memory:
```bash
format flash:
```

## Show Interface and IP Information
Show detailed interface status:
```bash
show interface status
```

Brief summary of IP interfaces:
```bash
show ip interface brief
```

Detailed information about a specific interface:
```bash
show interface <interface-name>
```

Show VLAN information:
```bash
show vlan brief
```

Show trunk ports:
```bash
show interfaces trunk
```

## Additional Useful Commands
Display the device's routing table:
```bash
show ip route
```

Show device's version and hardware details:
```bash
show version
```

Check connected neighbors (CDP):
```bash
show cdp neighbors
```

Check Layer 2 MAC address table:
```bash
show mac address-table
```

Ping a destination from the device:
```bash
ping <destination-ip>
```

Traceroute to a destination:
```bash
traceroute <destination-ip>
```

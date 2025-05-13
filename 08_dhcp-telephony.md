# 📞 DHCP & Telephony Configuration

## Exclude IP Ranges

```bash
ip dhcp exclude-address 192.168.10.1 192.168.10.5
ip dhcp exclude-address 192.168.20.1 192.168.20.5
````

## DHCP Pools

```bash
ip dhcp pool DATA10
network 192.168.10.0 255.255.255.0
default-router 192.168.10.1
exit
```

```bash
ip dhcp pool VOICE10
network 192.168.20.0 255.255.255.0
default-router 192.168.20.1
exit
```

## Telephony Service Configuration

```bash
telephony-service
max-ephone 3
max-dn 3
ip source-address 192.168.20.1 port 2000

ephone-dn 1 
number 10
ephone-dn 2
number 20
ephone-dn 3 
number 30

ephone 1 
type 7960
button 1:1

ephone 2
type 7960
button 1:2

ephone 3
type 7960
button 1:3
```


tanzo vmware
pinetlab 6 ubuntu 22 install  doc
crack pinettal 
ansible install iol
etherchannel ==>
1.PAGP only cisco
2.LACP IEEE 802.3ad
3.static (no protocol)

```
interface rannge
channel-protocol pagp
channel-group 20 mode desirable non-silent
```

```
show etherchannel summery
```

```
show etherchannel portchannel
```
```
show lacp counters
```
```
show lacp sys-id
```

```
interface rannge
channel-protocol lacp
channel-group 21 mode active
```


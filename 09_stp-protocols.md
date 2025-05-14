# 🌲 Spanning Tree Protocol (STP)

## STP Variants

- **STP (PVST+)** – IEEE 802.1d
- **Rapid STP (RSTP)** – IEEE 802.1w
- **Multiple STP (MSTP)** – IEEE 802.1s
- Max Limit 128 (1 STP Per Vlan)

## Root Bridge

- Central reference switch in STP.
- Default bridge priority: `32768`.
- Bridge ID = Priority + MAC address (e.g. 32768.AA:AA:AA:AA:AA:AA).
- Priorities must be multiples of 4096 (0, 4096, 8192, ..., 32768).
- BPDUs (Bridge Protocol Data Units) carry the bridge ID.

in vlans: priority always + vlan
32768 + vlan id


## STP Cost by Bandwidth

| Bandwidth | STP Cost |
|-----------|----------|
| 10 Gbps   | 2        |
| 1 Gbps    | 4        |
| 100 Mbps  | 19       |
| 10 Mbps   | 100      |


## Port Roles

- **Root Port**: Closest port (lowest cost) to the root bridge.
- **Designated Port**: Chosen for each network segment to forward traffic.
- **Blocked Port**: Prevents loops by not forwarding traffic.

```
show spanning-tree
```

```
show spanning-tree summery
```


modes:
short ==>
long ==>
```
spanning-tree pathcost method <mode>
```


modes:
mst 
pvst
rappid-pvst

```
spanning-tree mode <mode>
```


BPDU:
Hello = every 2s
Forward Delay = 15 Second
Max Age = 20 second


STP Port Roles: 
Root Port ==> 
Listenging Packets BPDU Forward Delay 15s
Learning Packets BPDU Forward Delay 15s
Forwarding --> working

Designated ==>
Listenging Packets BPDU Forward Delay 15s
Learning Packets BPDU Forward Delay 15s
Forwarding --> working


Block ==> 
Blocking


Directoru Topology Change ==>
Indirect Topology Change ==>




TCN ==> Topolofy Change NOtification BPDN



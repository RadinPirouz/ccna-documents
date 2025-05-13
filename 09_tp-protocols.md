# 🌲 Spanning Tree Protocol (STP)

## STP Variants

- **STP (PVST+)** – IEEE 802.1d
- **Rapid STP (RSTP)** – IEEE 802.1w
- **Multiple STP (MSTP)** – IEEE 802.1s

## Root Bridge

- Central reference switch in STP.
- Default bridge priority: `32768`.
- Bridge ID = Priority + MAC address (e.g. 32768.AA:AA:AA:AA:AA:AA).
- Priorities must be multiples of 4096 (0, 4096, 8192, ..., 32768).
- BPDUs (Bridge Protocol Data Units) carry the bridge ID.

## STP Cost by Bandwidth

| Bandwidth | STP Cost |
|-----------|----------|
| 10 Gbps   | 2        |
| 1 Gbps    | 4        |
| 100 Mbps | 19       |
| 10 Mbps   | 100      |

## Port Roles

- **Root Port**: Closest port (lowest cost) to the root bridge.
- **Designated Port**: Chosen for each network segment to forward traffic.
- **Blocked Port**: Prevents loops by not forwarding traffic.
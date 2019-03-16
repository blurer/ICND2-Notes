# Routing

``show ip route`` - what do you see?

Things to be considered.
* Next hop
* Route specificity
* Admin distance
* Metric

Lab Topology:
```
R1 -> S1 = 10.1.1.0/24
R1 -> R2 = 10.12.12.0/24
R1 -> R3 = 10.13.13.0/24
R2 -> R4 = 10.24.24.0/24
R3 -> R4 = 10.34.34.0/24
R4 -> S2 = 10.4.4.0/24

       +------+--------+-------+
       |  r4  |        |  s2   |
    +--+------+--+     +-------+
    |            |
    |            |
+---+--+      +--+---+
|  r2  |      |  r3  |
+-----++      ++-----+
      |        |
      |        |
      ++------++
       |  r1  |
       +--+---+
          |
          |
      +---+--+
      |  s1  |
      +------+
```

### Configs
Configurations are located here: https://github.com/blurer/ICND2-Notes/blob/master/configs/core-routing.md

### Connectivity
Run ``show cdp neighbor`` on each device to confirm you can see each device.

```
R1#show cdp n
Capability Codes: R - Router, T - Trans Bridge, B - Source Route Bridge
                  S - Switch, H - Host, I - IGMP, r - Repeater

Device ID        Local Intrfce     Holdtme    Capability  Platform  Port ID
R2               Gig 0/0            134           R       7206VXR   Gig 0/0
R3               Gig 1/0            161           R       7206VXR   Gig 1/0
S1               Gig 2/0            173           R       7206VXR   Gig 2/0
```

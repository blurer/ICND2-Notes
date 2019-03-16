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

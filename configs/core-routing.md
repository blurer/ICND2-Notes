# Core Routing Lab Configs

* All devices are c7200 images. 
* All passwords are cisco/cisco
* Telnet is enabled, no SSH (its a damn lab).

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

### Cabling

#### R1:
```
g0/0 -> g0/0 R2
g1/0 -> g1/0 R3
g2/0 -> g2/0 S1
```

#### R2:
```
g0/0 -> g0/0 R1
g1/0 -> g1/0 R4
```

#### R3: 
```
g1/0 -> g1/0 R1
g2/0 -> g2/0 R4
```

#### R4:
```
g0/0 -> g0/0 R5
g1/0 -> g1/0 R2
g2/0 -> g2/0 R3
```

## R1 Configuration

```
enable
conf t
hostname R1
int g0/0
ip address 10.12.12.1 255.255.255.0
no shut
des -> r2

int g1/0
ip addr 10.13.13.1 255.255.255.0
no shut
desc -> r3

int g2/0
ip addr 10.1.1.1 255.255.255.0
no shut
des -> s1
exit
enable secret cisco

line con 0
logging sync

line vty 0 15
password cisco
login
```

## R2 Configuration

```
enable
conf t
hostname R2
int g0/0
ip address 10.12.12.2 255.255.255.0
no shut
des -> r1

int g1/0
ip addr 10.24.24.1 255.255.255.0
no shut
desc -> r4

line con 0
logging sync

line vty 0 15
password cisco
login
```

## R3 Configuration

```
enable
conf t
hostname R3
int g1/0
ip address 10.13.13.3 255.255.255.0
no shut
des -> r1

int g2/0
ip addr 10.34.34.3 255.255.255.0
no shut
desc -> r4

line con 0
logging sync

line vty 0 15
password cisco
login
```

## R4 Configuration

```
enable
conf t
hostname R4
int g0/0
ip address 10.4.4.1 255.255.255.0
no shut
des -> s2

int g1/0
ip addr 10.24.24.4 255.255.255.0
no shut
desc -> r2

int g2/0
ip addr 10.34.34.4 255.255.255.0
no shut
des -> r3
exit
enable secret cisco

line con 0
logging sync

line vty 0 15
password cisco
login
```

## S1 Configuration

```
hostname S1
int g2/0
ip address 10.1.1.10 255.255.255.0
no shut
des -> r1
exit
enable secret cisco

line con 0
logging sync

line vty 0 15
password cisco
login
```

## S2 Configuration
```
hostname S2
int g0/0
ip address 10.4.4.10 255.255.255.0
no shut
des -> r4
exit
enable secret cisco

line con 0
logging sync

line vty 0 15
password cisco
login
```


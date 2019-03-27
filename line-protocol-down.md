# Serial Interfaces

R3->R4 Interface s6/1
* ip address 10.34.34.0/24
* r3: 10.34.34.3
* r4: 10.34.34.4

```
R3#show interfaces s6/1
Serial6/1 is up, line protocol is down 
  Hardware is M4T
  Internet address is 10.34.34.3/24
```

The interface is physically up, but no traffic will flow. Attempt to validate by pinging the local IP and remote IP - nothing will reply.

```
R3#ping 10.34.34.4
Type escape sequence to abort.
Sending 5, 100-byte ICMP Echos to 10.34.34.4, timeout is 2 seconds:
.....
Success rate is 0 percent (0/5)
```

How do we fix?
* What is our encapsulation set to - HDLC or PPP? HDLC is Cisco only, and default. Unless you configuered the far end to be PPP, it is most likely clocking that is the issue.
* Clock rate - Did you set it? 
* Are you running frame relay? 

If you have default encapsulation, not running frame relay, lets check the clock rate (and then bandwidth). On your DCE side of the cable set the clock rate with the following command: ``clock rate 19200`` with the number being your rate.
```
R3(config-if)#clock rate ?
  With the exception of the following standard values not subject to rounding,

	  1200 2400 4800 9600 14400 19200 28800 38400 
	  56000 64000 128000 2015232 

  accepted clockrates will be bestfitted (rounded) to the nearest value
  supportable by the hardware.

  <246-8064000>    DCE clock rate (bits per second)
```

A few moments later:
```
R3(config-if)#
*Mar 27 05:01:09.199: %LINEPROTO-5-UPDOWN: Line protocol on Interface Serial6/1, changed state to up
R3(config-if)#
*Mar 27 05:01:22.079: %DUAL-5-NBRCHANGE: EIGRP-IPv4 1: Neighbor 10.34.34.4 (Serial6/1) is up: new adjacency
```

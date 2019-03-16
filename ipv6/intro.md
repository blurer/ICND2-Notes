# IPv6 Intro

One of the key advantages of Ipv6 brings in the exponentially larger address space. The following will outline the baic address architecture of IPv6.

128 bit long addresses
Uses CIDR principles: prefix/prefix length
x:x:x:x:x:x:x:x:8, where x is a 16-bit hex field
The last 64 bits are used for the interface ID

2001:0DB8:C003:0001:0000:0000:0000:F00D = 2001:DB8:C003:1::F00D

aDDRESS TYPES ARE:
-Unicast: one to one (global, link local, unique local, compatible)
-Multicast: one to many (also replaces broadcast addresses)

Local link unicast: FE80::/10
Unique local unicast: FC00::/8 and FC00::/8
Multicast: FC00::/8
Broadcast: No long a thing in IPv6

Every IPv6 enabled interface must contain at least one loopback and one link local address.

Optionally, every interface can have multiple unique local and global addresses. 

When IPv6 is used over ethernet networks, the ethernet mac address can be used to generate the 64 bit interface id for the host. this is called the EUI64 address. Since mac addresses use 48 bits, additional bits must be inserted to the fill the 64 bits required. 


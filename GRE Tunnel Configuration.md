# GRE Tunnel Configuration



R1

\------

en

conf t

int fa 0/0

ip add 192.0.0.50 255.255.255.0

no shutdown

int fa 0/1

ip add 50.0.0.2 255.0.0.0

no shutdown



interface Tunnel0

tunnel destination 75.0.0.2

tunnel source fa 0/1

ip add 1.1.1.1 255.0.0.0

no shutdown



ip route 75.0.0.0 255.255.255.0 50.0.0.1



ip route 180.0.0.0 255.255.255.0 1.1.1.2 



syntax

\-----

ip route <remotelan> <subnetmask> ipofthetunnelend>



R2

\---

en

conf t

int fa 0/1

ip address 50.0.0.1 255.255.255.0

no shutdown

int Fa 0/0

ip address 75.0.0.1 255.255.255.0

no shutdown



R3

\---

en

conf t

interface Fa 0/0

ip add 75.0.0.2 255.255.255.0

no shutdown

int Fa 0/1

ip address 180.0.0.50 255.255.255.0

no shutdown



interface Tunnel0

tunnel destination 50.0.0.1

tunnel source fa 0/0

ip add 1.1.1.2 255.0.0.0



ip route 50.0.0.0 255.255.255.0 75.0.0.1



ip route 192.0.0.0 255.255.255.0 1.1.1.1 




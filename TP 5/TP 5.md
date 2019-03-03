# RENDU TP 5 #

## I. Préparation du lab 
Tout d'abbord nous allons crée les VM et les routers respectivement sur Virtual box et GNS3

![](https://github.com/AntoninDemaneche/CCNA/blob/master/TP%205/image/allvm.png?raw=true)

![](https://github.com/AntoninDemaneche/CCNA/blob/master/TP%205/image/vutotal.png?raw=true)

## II. Lancement et configuration du lab

Nous allons donner les ip correct et les noms de domaine à toute les machine et les routers virtuel :

### IP Router  :
``` R1# show ip interface brief
Interface                  IP-Address      OK? Method Status                Protocol
Ethernet0/0                unassigned      YES unset  administratively down down
Ethernet0/1                unassigned      YES unset  administratively down down
Ethernet0/2                unassigned      YES unset  administratively down down
Ethernet0/3                unas   
```
```R1# conf t
Enter configuration commands, one per line.  End with CNTL/Z.
R1(config)#
```
``` 
R1(config)# interface ethernet 0/0
R1(config-if)# ip address 10.5.1.254 255.255.255.0
R1(config-if)# no shut
R1(config-if)#
*Mar  1 00:25:08.003: %LINK-3-UPDOWN: Interface Ethernet0/0, changed state to up
*Mar  1 00:25:09.003: %LINEPROTO-5-UPDOWN: Line protocol on Interface Ethernet0/0, changed state to up
R1(config-if)# exit
R1(config)#exit
R1#
*Mar  1 00:25:28.631: %SYS-5-CONFIG_I: Configured from console by console
R1# show ip int br
Interface                  IP-Address      OK? Method Status                Protocol
Ethernet0/0                10.5.1.254      YES manual up 
```

Voila pour les routers maintenant passon au nom de domaine.

### Domaine 

```
R1#conf t
Enter configuration commands, one per line.  End with CNTL/Z.
R1(config)# hostname Router1.tp5
Router1.tp5(config)#exit
Router1.tp5#
*Mar  1 00:34:50.723: %SYS-5-CONFIG_I: Configured from console by console
Router1.tp5#show arp
Protocol  Address          Age (min)  Hardware Addr   Type   Interface
Internet  10.5.1.254              -   cc01.06a8.0000  ARPA   Ethernet0/0
Internet  10.5.3.253              -   cc01.06a8.0001  ARPA   Ethernet0/1
Router1.tp5#
```
Biensur tout est fait à l'identique sur le router 2.

### Routes : 

Il s'agira alors d'inclure les routes au différent router et machines virtuel.

#### Route Router :

Router 1 :

```
Router1.tp5#show ip route
Gateway of last resort is 10.5.3.254 to network 0.0.0.0

     10.0.0.0/24 is subnetted, 3 subnets
C       10.5.3.0 is directly connected, Ethernet0/1
S       10.5.2.0 [1/0] via 10.5.3.254
C       10.5.1.0 is directly connected, Ethernet0/0

```

Router 2 : 
```
Router2.tp5#show ip route
Gateway of last resort is 10.5.3.253 to network 0.0.0.0

     10.0.0.0/24 is subnetted, 3 subnets
C       10.5.3.0 is directly connected, Ethernet0/1
C       10.5.2.0 is directly connected, Ethernet0/0
S       10.5.1.0 [1/0] via 10.5.3.253
```

Server 1 : 
```
[user@server1 ~]$ ip route show
10.5.1.0/24 dev enp0s3 proto kernel scope link src 10.5.1.10 metric 100
10.5.2.0/24 via 10.5.1.254 dev enp0s3 proto static metric 100
10.5.3.254 dev enp0s3 proto static scope link metric 100
```

Client 1 :

```
[user@client1 etc]$ ip route show
10.0.0.0/8 dev enp0s3 proto kernel scope link src 10.5.2.10 metric 102
10.5.1.0/24 via 10.5.2.254 dev enp0s3 proto static metric 102
```

Client 2 :

```
[user@client2 network-scripts]$ ip route show
10.5.1.0/24 via 10.5.2.254 dev enp0s3 proto static metric 102
10.5.2.0/24 dev enp0s3 proto kernel scope link src 10.5.2.11 metric 102

```
Il s'agira alors de voirs si les routes fonctionnes.Pour cela nous allons réalisé diver Ping entre les client et les serveur :

### Le test : 
Ping servers 1 vers  client 1 et  client 2 : 
```
[user@server1 ~]$ ping client1
PING client1 (10.5.2.10) 56(84) bytes of data.
64 bytes from client1 (10.5.2.10): icmp_seq=1 ttl=62 time=42.6 ms
64 bytes from client1 (10.5.2.10): icmp_seq=2 ttl=62 time=39.5 ms
```
```
[user@server1 ~]$ ping client2
PING client2 (10.5.2.11) 56(84) bytes of data.
64 bytes from client2 (10.5.2.11): icmp_seq=1 ttl=62 time=34.0 ms
64 bytes from client2 (10.5.2.11): icmp_seq=2 ttl=62 time=41.5 ms
```
Ping  Client 1 vers server 1 :

```
[user@client1 ~]$ ping server1
PING server1 (10.5.1.10) 56(84) bytes of data.
64 bytes from server1 (10.5.1.10): icmp_seq=1 ttl=62 time=47.9 ms
64 bytes from server1 (10.5.1.10): icmp_seq=2 ttl=62 time=43.2 ms 

```

Ping client 2 vers server 1  :

```
[user@client2 ~]$ ping server1
PING server1 (10.5.1.10) 56(84) bytes of data.
64 bytes from server1 (10.5.1.10): icmp_seq=3 ttl=62 time=37.1 ms
64 bytes from server1 (10.5.1.10): icmp_seq=4 ttl=62 time=43.1 ms
```

## III. DHCP

Configuration d'abbord le client 2 comme nouveau serveur DHCP, puis commençons nos expérience :

![](https://github.com/AntoninDemaneche/CCNA/blob/master/TP%205/image/Dhcp.png?raw=true)

Petit Test : 
```
[user@client1 ~]$ sudo ifup enp0s3
Connexion activée (chemin D-Bus actif : /org/freedesktop/NetworkManager/ActiveConnection/27)
```

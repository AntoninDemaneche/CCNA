# TP 4 - Spéléologie réseau : descente dans les couches #

***

## 1 - Mise en place du lab

### 1- Créations des réseaux

Nous créons donc les différents réseaux et attribuons les ip correspondante aus VM.
````
Client 1 : 10.1.0.1

Server 1 : 10.2.0.1
````

### 2- Créations des VMs 

Une fois chose faite, nous créons les VMs.

![](https://github.com/AntoninDemaneche/CCNA/blob/master/TP%204/Image/opperationnel.png?raw=true)

Une fois les ips statiques et les noms de domaine réaliser nous réalisons les pings :

![](https://github.com/AntoninDemaneche/CCNA/blob/master/TP%204/Image/Ping%20client%20rooter.png?raw=true)

![](https://github.com/AntoninDemaneche/CCNA/blob/master/TP%204/Image/ping%20server%20rooter.png?raw=true)

Cela fonctionne nous pouvons continuer !

### 3- Mise en place du routage statique

Il faut maintenant Ping le server 1 avec le Client 1 en sommes ping une vm avec une autre vm en passant pour un router.

Nous ajoutons les routes au vms et obtenons ceci.

![](https://github.com/AntoninDemaneche/CCNA/blob/master/TP%204/Image/Ping%20entre%20vm.png?raw=true)

Chose réussite !

## 2 - Spéléologie Réseau 

### 1 - Arp 

#### A - Manip 1 : 
ARP Client 1 :
![](https://github.com/AntoninDemaneche/CCNA/blob/master/TP%204/Image/tablearpclien1.png?raw=true)
ARP Server 1 : 
![](https://github.com/AntoninDemaneche/CCNA/blob/master/TP%204/Image/tablearpclien2.png?raw=true)

L'ont peut voirs que certaine ligne sont en delay contrairement a d'autre qui sont en stale.

ARP Client 1 apres ping :
![](https://github.com/AntoninDemaneche/CCNA/blob/master/TP%204/Image/arppostpingCLIEN.png?raw=true)
ARP Server 1 : 
![](https://github.com/AntoninDemaneche/CCNA/blob/master/TP%204/Image/appostpingSERVER.png?raw=true)

#### B - Manip 2 : 

Nous vidons les tables ARP.

![](https://github.com/AntoninDemaneche/CCNA/blob/master/TP%204/Image/vidageroter.png?raw=true)
Nous pingons alors le server 1 avec client 1 et réobservons la table arp du router.
![](https://github.com/AntoninDemaneche/CCNA/blob/master/TP%204/Image/roterapresvidageetping.png?raw=true)


#### C - Manip 3 :

(pas fait mdrrr)

#### D - Manip 4 : 

( non plus mdr )

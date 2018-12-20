# TP 2 - Exploration du réseau d'un point de vue client #


## ETAPE I : EXPLORATION LOCAL EN SOLO :##

### 1- : Affichage d'informations sur la pile TCP/IP locale ###
Adresse mac Ethernet :

```
Carte Ethernet Ethernet :

   Statut du média. . . . . . . . . . . . : Média déconnecté
   Suffixe DNS propre à la connexion. . . :
   Description. . . . . . . . . . . . . . : Intel(R) Ethernet Connection (7) I219-LM
   Adresse physique . . . . . . . . . . . : E4-B9-7A-18-7E-D1
   DHCP activé. . . . . . . . . . . . . . : Oui
   Configuration automatique activée. . . : Oui

```

Adresse mac Wifi :

```

Carte réseau sans fil Wi-Fi :

   Suffixe DNS propre à la connexion. . . : auvence.co
   Description. . . . . . . . . . . . . . : Intel(R) Wireless-AC 9260
   Adresse physique . . . . . . . . . . . : 30-24-32-CA-8D-9D
   DHCP activé. . . . . . . . . . . . . . : Oui
   Configuration automatique activée. . . : Oui
   Adresse IPv6 de liaison locale. . . . .: fe80::6ccf:a44d:c8c3:f72%14(préféré)
   Adresse IPv4. . . . . . . . . . . . . .: 10.33.0.219(préféré)
   Masque de sous-réseau. . . . . . . . . : 255.255.252.0
   Bail obtenu. . . . . . . . . . . . . . : mardi 11 décembre 2018 09:06:45
   Bail expirant. . . . . . . . . . . . . : mardi 11 décembre 2018 12:05:02
   Passerelle par défaut. . . . . . . . . : 10.33.3.253
   Serveur DHCP . . . . . . . . . . . . . : 10.33.3.254
   IAID DHCPv6 . . . . . . . . . . . : 120595506
   DUID de client DHCPv6. . . . . . . . : 00-01-00-01-23-22-C5-47-E4-B9-7A-18-7E-D1
   Serveurs DNS. . .  . . . . . . . . . . : 10.0.10.20
                                       8.8.8.8
   NetBIOS sur Tcpip. . . . . . . . . . . : Activé 
  
 ```


L'adresse mac Ethernet est donc : E4-B9-7A-18-7E-D1
L'adresse mac Wifi est donc : 30-24-32-CA-8D-9D

Pour obtenir l'adresse réseaux et l'adresse Broadcast nous avons besoin de l'adresse IP et du masque de sous réseaux qui sont respectivement :
Adresse IP : 10.33.0.219/22
Masque de sous réseaux : 255.255.252.0
L'adresse réseaux que nous obtenons est donc : 10.33.0.0
L'adresse Broadcast que nous obtenons est donc : 10.33.3.255

Apres utilisations de la commande Ipconfig j'obtiens ça : 

```
Carte réseau sans fil Wi-Fi :

   Suffixe DNS propre à la connexion. . . : auvence.co
   Description. . . . . . . . . . . . . . : Intel(R) Wireless-AC 9260
   Adresse physique . . . . . . . . . . . : 30-24-32-CA-8D-9D
   DHCP activé. . . . . . . . . . . . . . : Oui
   Configuration automatique activée. . . : Oui
   Adresse IPv6 de liaison locale. . . . .: fe80::6ccf:a44d:c8c3:f72%14(préféré)
   Adresse IPv4. . . . . . . . . . . . . .: 10.33.0.219(préféré)
   Masque de sous-réseau. . . . . . . . . : 255.255.252.0
   Bail obtenu. . . . . . . . . . . . . . : mardi 11 décembre 2018 09:06:45
   Bail expirant. . . . . . . . . . . . . : mardi 11 décembre 2018 12:05:02
   Passerelle par défaut. . . . . . . . . : 10.33.3.253
   Serveur DHCP . . . . . . . . . . . . . : 10.33.3.254
   IAID DHCPv6 . . . . . . . . . . . : 120595506
   DUID de client DHCPv6. . . . . . . . : 00-01-00-01-23-22-C5-47-E4-B9-7A-18-7E-D1
   Serveurs DNS. . .  . . . . . . . . . . : 10.0.10.20
                                       8.8.8.8
   NetBIOS sur Tcpip. . . . . . . . . . . : Activé
   
   ```

Et j'obtiens ainsi obtenir mon ip de paserelle qui est : 10.33.3.253

Par la suite nous cherchons les mêmes informations mais à l'aide de l'OS, il nous suffit alors de nous rendre dans les paramétres réseaux et nous obtenons :
  
 ```
 SSID :	WiFi@YNOV
Protocole :	802.11ac
Type de sécurité :	WPA2 - Entreprise
Type d’informations de connexion :	Microsoft: PEAP (Protected EAP)
Bande passante réseau :	5 GHz
Canal réseau :	60
Adresse IPv4 :	10.33.0.219
Serveurs DNS IPv4 :	10.0.10.20
8.8.8.8
Suffixe DNS principal :	auvence.co
Fabricant :	Intel Corporation
Description :	Intel(R) Wireless-AC 9260
Version du pilote :	20.50.0.4
Adresse physique (MAC) :	30-24-32-CA-8D-9D
```

On à encore une fois toute les informations nécesaire :
Adressi ip : 10.33.0.219
Adresse Physique : 30-24-32-CA-8D-9D

La Gateways est l'adresse IP que tout les utilisateurs sur le réseaux ingésup on.

### 2- Modifications des informations ###

Premiére adresse : 10.33.0.1
Derniere adresse : 10.33.3.252 

Pour changer l'adresse IP je me rend dans le paneau de configurations puis je vais dans réseaux et partage est finit par accéder au propriter de ma wifi pour changer mon IPV4.

### B- Nmaps

Nous avons ouvert et découvert nmaps.

### C- Nmaps Modification d'adresse IP - pt. 2 ###


On change l'adresse l'IP, celle-ci ffonctione en modifiant.La Gateways la connections au réseaux est alors imposible


## Partie II : Explorations en Duo ##

Nous modifions notre adresse IP et obtenons :
Adresse IP ma machine : 10.33.3.18
Adresse IP machine voisine : 10.33.3.19
Masque réseaux : 255.255.255.0 

Nous nous pingons : 

```Envoi d’une requête 'Ping'  10.33.3.19 avec 32 octets de données :
Réponse de 10.33.3.19 : octets=32 temps<1ms TTL=128
Réponse de 10.33.3.19 : octets=32 temps<1ms TTL=128
Réponse de 10.33.3.19 : octets=32 temps<1ms TTL=128
Réponse de 10.33.3.19 : octets=32 temps<1ms TTL=128
```

Statistiques Ping pour 10.33.3.19:
    Paquets : envoyés = 4, reçus = 4, perdus = 0 (perte 0%),
Durée approximative des boucles en millisecondes :
    Minimum = 0ms, Maximum = 0ms, Moyenne = 0ms

Le Ping à réussit !


Adresse IP  ma machine : 12.33.9.18
Adresse IP machine voisine : 12.33.9.19
Masque réseaux : 255.255.255.0

Tent en /20 et /24 réussit, il suffit simplement de changer le troisiéme chiffre de l'ipv4

Nous effectuons un ping entre les deux machines cela fonctionne bien nous avons une réponse des deux machine :

```
Envoi d’une requête 'Ping'  12.33.9.19 avec 32 octets de données :
Réponse de 12.33.9.19 : octets=32 temps=1 ms TTL=128
Réponse de 12.33.9.19 : octets=32 temps<1ms TTL=128
Réponse de 12.33.9.19 : octets=32 temps<1ms TTL=128
Réponse de 12.33.9.19 : octets=32 temps<1ms TTL=128

Statistiques Ping pour 12.33.9.19:
    Paquets : envoyés = 4, reçus = 4, perdus = 0 (perte 0%),
Durée approximative des boucles en millisecondes :
    Minimum = 0ms, Maximum = 1ms, Moyenne = 0ms
  ```

Maintenant nous réalisons le ping 8.8.8.8 

```
PS C:\Users\Antonin> curl google.com


StatusCode        : 200
StatusDescription : OK
Content           : <!doctype html><html itemscope="" itemtype="http://schema.org/WebPage" lang="fr"><head><meta
                    content="text/html; charset=UTF-8" http-equiv="Content-Type"><meta
                    content="/images/branding/googleg/1x/goo...
RawContent        : HTTP/1.1 200 OK
                    X-XSS-Protection: 1; mode=block
                    X-Frame-Options: SAMEORIGIN
                    Cache-Control: private, max-age=0
                    Content-Type: text/html; charset=UTF-8
                    Date: Thu, 20 Dec 2018 09:43:26 GMT
                    Expires: ...
Forms             : {f}
Headers           : {[X-XSS-Protection, 1; mode=block], [X-Frame-Options, SAMEORIGIN], [Cache-Control, private,
                    max-age=0], [Content-Type, text/html; charset=UTF-8]...}
Images            : {@{innerHTML=; innerText=; outerHTML=<IMG id=hplogo onload=window.lol&amp;&amp;lol()
                    style="PADDING-BOTTOM: 14px; PADDING-TOP: 28px; PADDING-LEFT: 0px; PADDING-RIGHT: 0px" alt=Google
                    src="/images/branding/googlelogo/1x/googlelogo_white_background_color_272x92dp.png" width=272
                    height=92>; outerText=; tagName=IMG; id=hplogo; onload=window.lol&amp;&amp;lol();
                    style=PADDING-BOTTOM: 14px; PADDING-TOP: 28px; PADDING-LEFT: 0px; PADDING-RIGHT: 0px; alt=Google;
                    src=/images/branding/googlelogo/1x/googlelogo_white_background_color_272x92dp.png; width=272;
                    height=92}}
InputFields       : {@{innerHTML=; innerText=; outerHTML=<INPUT type=hidden value=fr name=hl>; outerText=;
                    tagName=INPUT; type=hidden; value=fr; name=hl}, @{innerHTML=; innerText=; outerHTML=<INPUT
                    type=hidden value=hp name=source>; outerText=; tagName=INPUT; type=hidden; value=hp; name=source},
                    @{innerHTML=; innerText=; outerHTML=<INPUT type=hidden name=biw>; outerText=; tagName=INPUT;
                    type=hidden; name=biw}, @{innerHTML=; innerText=; outerHTML=<INPUT type=hidden name=bih>;
                    outerText=; tagName=INPUT; type=hidden; name=bih}...}
Links             : {@{innerHTML=<SPAN class=gbtb2></SPAN><SPAN class=gbts>Recherche</SPAN>; innerText=Recherche;
                    outerHTML=<A onclick=gbar.logger.il(1,{t:1}); id=gb_1 class="gbzt gbz0l gbp1"
                    href="https://www.google.fr/we
```

### 1- Petit Chat Privé ###

Nous mettons alors en place le chat grâce à Netcat celui à réussit !

### 2- Wireshark ###

Avec un ping :

```http://prntscr.com/lxew6v```


Avec Netcat : J'ai repérer la ligne où on a utiliser le netcat grâce au port 8888. On clique droit dessus, puis Follow et TCP pour afficher les trames de ce que ont c'est envoyé : 

```http://prntscr.com/lxewpj```

Avec PC1 et PC2 :

### 3- Firewall ###

```http://prntscr.com/lxf28q```



    

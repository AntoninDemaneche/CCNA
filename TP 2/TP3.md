# TP-3 : 

## Partie 1 : Création et utilisation simples d'une VM centOS


###Etape 1 :
( Fait sensemble )

###Etape 2 : 
( Fait sensemble )

###Etape 3 :
( Fait sensemble )

###Etape 4 : 

Premiérement pronvons que nous avons accés à internet sur la VM, nous allons faire la commande 
```curl -SL google.com```
Si nous possédons internet un code HTML s'affichera cela symbolisera le fait que l'internet est bien sur la VM 
Maintenant nous allons pinger notre PC avec la VM.
Nous faisons donc : 
```192.168.127.1```
Comme cela fonctionne nous recevons cela :
```64 bytes fromm 192.168.127.1: icmp_seq=15 ttl=128 time=1.62 ms```
Maintenant faisons de même en pingant la VM avec notre PC :
```ping 192.168.127.10  ```
Cela fonctionne alors nous recevons cela :
```Réponse de 192.168.127.1 : octets=32 temps<1ms TTL=64```

Pour afficher la table de routage nous faisons :

``` netstat -rn```

Nous obtenons ceci : 
```http://prntscr.com/m7ib5h```

## Partie 2 : Notion de ports et SSH

Etape 3 : 
 A ) La connexion ne peut pas se faire, car notre VM n'écoute que le port 22
 B ) Il faut donc modifier les options du Firewall pour autoriser une connections sur le port 2222

Etape 4 : 

## Partie 3 : 


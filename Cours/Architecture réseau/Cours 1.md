modèles osi --> 7 couches !!!!

7 Application 
6 Présentation (format de nos données) 
5 Session ( creer une session de communication)
4 Transport Port 16 bits deux protocole principalement utiliser TCP (plus lourd) UDP (lettre simple rapide) (streaming) (important) Firewall
3 Réseau Adresse iPV4 32 bits iPV6 128 bits (important) (router)
2 liaison (switch) @mac 48bits 
1 Physique ( Câble fibres, ondes électromagnétique, hub) 


Masque sous réseau adresse IP  !!!!

IPv4 32 bits 4.3MM d'adresse 

masque subnet (masque de sous réseaux) 

classe A 256 réseaux = 2p8 | 2p24 = 16m machine 255.0.0.0 
classe B 2p16 = 65536 réseaux | 2p16 65536 machine 255.255.0.0
classe C 2p24 = 16m réseaux | 2p8 256 machine 255.255.255.0 

3 fonctions
 
et AND 1 et l'autre 1 1 = 1 | 0 1 = 0 

ou OR 1 ou l'autre 1 0 = 1 | 0 1 = 1 | 1 1 = 1 

non NOT 1 = 0 | 0 = 1

ou excusif  1 ou l'autre exclusivement 1 0 = 1 | 0 1 = 1 | 1 1 = 0 | 0 0 = 0 

clase less 

VLSM (variable length subtnet mask) masque de sous réseaux a taille variable ( les classes sont plus utilisés depuis plus de 20 ans) 

Pour les réseaux privés !!!!

classe A 10.0.0.0 subnet mask 255.0.0.0 8 bits 10.255.255.255 broadcast 
classe B 172.16.0.0 subnet mask 255.240.0.0 12 bits 172.31.255.255 broadcast 
classe C 192.168.0.0 subnet mask 255.255.0.0 16 bits 192.168.255.255 broadcast

COMMANDE PACKET TRACER !!!!!

Pour configurer un routeur 
no 
enter 
enable 
conf t
host (pour rename the router)
int gigabitethernet 
ip add 
no shut 
^Z
wr 

adresse mac 48 bits 
adresse ipv4 32 
ipv6 128

show vlan brief
int range 
sw ac vlan 

enable
host 
vlan 
name
int range 
sw ac vlan 
^z
wr


pour le trunk  TRUNK (pour les switch) !!!!

802.1q dot1q dans le cli 

int range gigabit 
sw mo tr
sw mo ac 
show int tr 

Création de sous interface dans le routeur pour les vlan !!!!

int G0/.10 
encapsluation (enc) dot1q numéro de la vlan 
ip add
exit 
^z
wr 

Ptotocole VTP diffusion de vlan a travers des liens TRUNK !!!!

creation d'un domaine et d'un mdp tout est precisant a notre switch qui a les vlan quil est serveur et les autres clients 

enable 
conf t
vtp mode server
vtp domain (nom du domaine)
vtp passaword (mdp du password)

POUR les switch client !!!!

enable
conf t
vtp mode client
vtp domaine (nom du domaine)
vtp password (mdp)

FAIRE UN DHCP DANS LE ROUTEUR CISCO !!!!

enable 
conf t 
ip dhcp pool (nom de la pool)
net (adresse ip subtnet mask)
default (gateway)

PLUS DE DETAILS SUR LE MODELE AUSSI ET SES DPU !!!!

la couche 4 (transport) du modele OSI assure la fiabilite le controle du flux et la correction des erreurs
la couche 2 (liaison de données) du modele OSI assure l'adressagz physique la topologie reseau et l'acces au media 
le role de la couche presentation (6) elle represente les donnes comme par exemple les languages de programation (HTML)
le role de la couche réseau (3) gere la connection entre les peripheriques 
la couche qui defeninit les spécifications électriques mécaniques procedurale et fonctionnelles est la couche 1 (physique)
la couche qui assure l'établissement, la gestion et la fermeture d'une session entre application est la couche 5 (session)
la couche qui fournit des services aux processus applicatifs est la couche 7 (application) 

Application    Donnée ;
Presentation   Donnée ; HTTP,DNS,FTP
Session        Donnée ;
Transport      Segment ; TCP,UDP
Réseau         Paquet ; IP
Liaison de données Trame ; Mac
Physique       Bit ; 01

ADRESSE IPV4 MULTIDIFFUSION ET MONODIFFUSION !!!!

Loopback commence toujours par 127.0.0.0 (toi meme) adresse utiliser par le systeme local 
Adresses link-local ou adresses APIPA (Adressage IP privé automatique) 169.254.0.0 /16 ou 169.254.0.1 à 169.254.255.254
Il existe également un bloc de multidiffusion de classe D composé de 224.0.0.0 à 239.0.0.0 et un bloc d'adresses expérimentales de classe E composé de 240.0.0.0 à 255.0.0.0.
IPv4 a réservé les adresses 224.0.0.0 à 239.255.255.255 comme plage de multidiffusion
Adresse IPV4 privés  192.168.0.0/24   172.16.0.0/16   10.0.0.0/8

La transmission monodiffusion fait référence à un périphérique qui envoie un message à un autre périphérique dans les communications un-à-un.
Un paquet monodiffusion à une adresse IP de destination qui est une adresse monodiffusion qui va à un seul destinataire. Une adresse IP source ne peut être qu'une adresse monodiffusion, car le paquet ne peut provenir que d'une seule source. Cela ne tient pas compte du fait que l'adresse IP de destination soit une monodiffusion, une diffusion ou une multidiffusion.

ADRESSAGE DYNAMIQUE DHCP !!!!

OFFRE DHCP : un serveur DHCP repondant a la demande d'un client 
DHCPACK : le serveur DHCP confirme que la caution d'adresse a été accepté 
DEMANDE DHCP : le client acceptant l'adresse IP fournie par le serveur DHCP 
DHCPDECOUVRIR : un client initiateur un message pour trouver un serveur DHCP 

l'adresse IPv4 de destination un client DHCPv4 utilise-t-il pour envoyer le paquet Découverte DHCP initial lorsqu'il recherche un serveur DHCP est 
255.255.255.255


NAT !!!!

 Grâce à la fonction NAT, le routeur sans fil est capable de traduire plusieurs adresses IPv4 internes en adresse publique unique.
 La traduction d'adresses réseau permet de convertir une adresse IPv4 source (locale) privée en adresse publique (globale)
 Le processus est inversé pour les paquets entrants 9

Quel est le principal avantage de l'utilisation du NAT ?

permet à un grand groupe d'utilisateurs de partager une ou plusieurs adresses IP publiques


PROCESSUS ARP !!!!

 L'adresse MAC de destination d'une diffusion Ethernet au format hexadécimal est : FFFF.FFFF.FFFF

 Lorsqu'un commutateur Ethernet reçoit une trame de diffusion, il va : Transférer la trame à tous les ports à l'exception du port entrant

 L'hôte A a une trame Ethernet à envoyer à l'hôte B sur le même réseau. L'hôte A connaît l'adresse IP de l'hôte B, mais pas son adresse MAC. Quel message l'hôte A envoie-t-il pour déterminer l'adresse MAC de l'hôte B? Demander ARP

Une requête ARP est envoyée en tant que: une diffusion, de sorte que tous les périphériques sur le même réseau la reçoivent.

L'hôte B reçoit une requête ARP. L'hôte B renvoie une réponse ARP si : L'adresse IP dans la demande ARP correspond à sa propre adresse IP.

L'hôte A envoie une demande ARP et reçoit une réponse ARP de l'hôte B. Quels éléments de la réponse ARP n'étaient pas connus de l'hôte A, et n'ont-ils pas besoin de communiquer avec l'hôte B ? Adresse MAC de l'hôte B


Adresse physique (adresse MAC) - Utilisée pour les communications entre cartes réseau situées sur le même réseau Ethernet.
Adresse logique (l'adresse IP) - Utilisée pour envoyer les paquets depuis le périphérique source vers le périphérique de destination. L'adresse IP de destination peut se trouver soit sur le même réseau IP que la source soit sur un réseau distant.

RESET UN SWITCH EN PHYSIQUE SUR PUTTY !!!!

Eteindre/Allumer 

APP->Mode<-15 sec appuyer 
attendre
flash_init
del flash:configue.text
del flash:vlan.dat
boot 

DANS LE CMD POUR REFAIRE UNE DEMANDE DHCP !!!!

ipconfig /release 
ipconfig /renew 

![[Pasted image 20241104132729.png]]


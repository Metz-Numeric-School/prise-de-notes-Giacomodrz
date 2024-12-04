#### rentrer dans les switch pour faire le protocole VTP:
dans le switch 1
CLI -> enable
	conf t
	vtp mode server
	vtp domain BSRC2
	vtp password MNS
	Hostname SW-1
	ctrl z
	wr

Maintenant go switch 2
CLI-> enable
	conf t
	vtp mode client
	vtp domain BSRC2
	vtp password MNS
	hostname sw-2
	ctrl z
	wr

Maintenant go switch 3
CLI -> enable
	conf t
	vtp mode client
	vtp domain BSRC2
	vtp password MNS
	Hostname sw-3
	ctrl z
	wr

#### Créer les vlan
aller dans le sw 1
	conf t
	vlan 10
	name (...)
	exit
la même chose pour les autres vlan tout en restant dans le sw 1

--> sh vlan brief , afin de vérifier si les vlan ont bien était créer

#### Faire les liens Trunk dans les switch
Grâce au liens trunk les vlan vont se transférer automatiquement sur tout les switch 
en conf t 
	int G0/2 (le cable branché vers l'autre sw)
	switchport mode trunk
faire la même chose dans les autres sw afin de faire passer les vlans dans tout les sw
	conf t
	int range G0/1-2
	sw mo tr
ceci est pour prendre tout d'un coup et les passer en trunk 

#### Mettre les vlan dans les ports ethernet que l'on veut
	int range f0/1-18
	sw mo ac
	sw ac vlan 10
Mettre les vlan que l'on souhaite pour  chaque rangé 
exemple apres j'ai fais dans le switch 1 toujours
	int range f0/19-24
	sw mo ac
	sw ac vlan 50
ne pas oublier de sauvegarder

#### Pas oublier de configurer ces PC, imprimantes serveurs etc...
Configurer les adresse ip en static en configurant bien les gateway et l'ipv4 static pour chaque machine

#### Configurer le router
Aller dans le CLI
	enable
	conf t
	hostname r-1
	int G0/0/1 
	no shut (ça c'est pour activer le router)

#### Création des sous interfaces dans le router
toujours dans le cli 
	int G0/0/1.10 (le dernier nombre c'est pour la vlan souhaité ici la vlan 10)
	encapsulation dot 10
	ip add 170.16.0.254 255.255.255.0 (mettre la passerelle de votre vlan)
répéter ça pour chaque sous interface
	int G0/0/01.20
	enc dot 20
	ip add 172.16.1.  255.255.255.
	exit
	
    int G0/0/01.30
	enc dot 30
	ip add 172.16.1.94  255.255.255.224
	
	intG0/0/01.40
	enc dot 40
	ip add 172.16.1.110  255.255.255.240
	
	int G0/0/01.50
	enc dot 50
	ip add 172.16.1.126  255.255.255.240
	exit
	
	int G0/0/01.60
	enc dot 60
	ip add 172.16.1.140  255.255.255.240
	exit
#### Vérifier si les machines ping entre elle
allez dans un pc et essayez de ping un pc d'un autre switch pour vérifier si ça marche

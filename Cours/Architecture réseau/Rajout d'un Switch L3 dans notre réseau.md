Une fois le réseau créer mettait un switch L3 (3650) entre les switch et le router.
Ensuite raccorder les switch avec le L3 en mode trunk puis lier le l3 avec le router (4331).
Mettait en route le L3 en mettant une alimentation dedans

#### Configuration du switch L3
Maintenant aller dans son CLI

	mettait no
	enable conf t
	hostname (...)
	
supprimer les cables pour forcer le mode tr
ensuite retourner dans le CLI du L3
	int range G1/0/1-6
	sw mo tr
	exit

	vtp mode client
	vtp domain BSRC2 
	vtp password MNS
ne pas oubliez de sauvegarder 

#### Créer une svi 
	enable
	conf t
	int vlan 10
	ip add (passerrelle de la vlan)
continuer la même étapes avec les autres vlan 
	ex: int vlan 20
	ip add ...
une fois fini sauvegarder 
Essayer maintenant de ping avec vos pc les passerelles de leur réseaux

#### Autoriser le routage 
Allé dans le CLI du L3
	conf t
	ip routing

#### Configurer le routeur avec le L3
aller dans le routeur
	enable
	conf t
	host r-1
	int g0/0/1
	ip add 10.10.10.1 255.255.255.252
	no shut

Maintenant aller dans le l3
	conf t 
	int g1/0/24
	no sw
	ip add 10.10.10.2 255.255.255.252

Dans le routeur faire les route de routage statique
	ip route 172.16.0.0 255.255.255.0 10.10.10.2
faire ca pour tout les masque des adresses ip des route de vos switch
	ex: 
![[Pasted image 20241105133200.png]]


# Lab 04 - Découverte et mise en place de VLANS

📅 Date de réalisation : Samedi 10 octobre 2026

## 🎯 Objectif

Comprendre ce qu'est un VLAN(Virtual Local Area Network) et essayer d'en mettre en place au sein d'une architecture réseau.

---

## 🏗️ Topologie proposé

Pour cette activité découverte j'ai choisit l'architecture réseau suivante:

- 4 ordinateurs fixes
- 1 Switch (2960 sur Cisco Pack Trac)
- des câbles

Voici la photo représentant mon architecture en fin d'activité :
![Architecture projet](<switch et vlan.png>)

---

## ⚙️ Étapes de réalisation

Avant toute chose, je me suis questionner puis renseigner à l'aide de recherche sur le web sur ce qu'est vraiment un VLAN.
Un Vlan privé est une configuration réseau qui permet de séparer les ports d'un switch en plusieurs réseau virtuelle totalement indépendants.
Pour comprendre ce concept, il faut garder à l'idée que c'est avant tout comme dans un immeuble. Si vous vous trouver à l'étage 2 et que vous souhaitez
communiquer avec quelqu'un se trouvant à l'étage 4, cela s’avère impossible. Ainsi, un ordinateur sur un vlan particulier ne peut pas communiquer avec un autre
ordinateur se trouvant sur un vlan différent.

### 1. Mise en place des appareils et connections

La première étape de l'activité consistait à mettre en place les différents appareils (ordinateurs) et de les connecter au Switch.
Le premier ordi est donc connecter au Switch sur le port Ethernet Fa1, le second sur le port Fa0/2 et ainsi de suite pour les deux dernier.
J'ai par la suite rentrais les adresses IPV4 et le masque manuellement pour chacun d'entre eux.
Ordinateur 1 : 192.168.10.1/24
Ordinateur 2 : 192.168.10.2/24
Ordinateur 3 : 192.168.20.1/24
Ordinateur 4 : 192.168.20.2/24


### 2. Création des VLANS

Grace au CLI de mon Switch j'ai pu rentrer des commandes afin de creer des VLANS. Mon principe étais de réunir le pc 1 et 2 sur le VLAN 10 et 
de réunir le pc 3 et 4 sur le VLAN 20.

Voici l'enchainement de commandes utilisés.

La commande enable permet de passer du mode utilisateur au mode privilégié et la commande configure terminal permet d'entrer en mode config.
Je créer mon premier virtual lan en tapant 'VLAN 10' et lui donne le nom 'ADMINISTRATION'. Je refait ce processus pour deux autre VLAN (SUPPORT et SERVEUR).


### 3. Affectation des ports aux VLANS

Les Vlans maintenant créer nous n'avons pas encore de ports affectés. La commande 'interface range fa0/1-2' sélectionne les ports Fa0/1 (relié à ordi1) et Fa0/2 (relié à ordi2). 
La commande 'Switchport mode access' configure les ports en mode accès et 'switchport access vlan 10' place ces ports dans le VLAN 10.


### 4. Verification des VLANS

Pour vérifier que mes VLANS étaient bien présent et bien associés à ce que je voulais, j'ai décider de faire 2 choses intéressante.
La première est qu'étant donné que nous sommes dans la console du Switch nous pouvons taper une commande pour vérifier l'ensemble: 'show vlan brief' qui nous donne un aperçu du tout.

Et la seconde manière de vérifier est de se rendre dans la console d'un des ordinateurs et d'essayer de ping l'ordinateur sur le même VLAN, si cette commande réussit alors nos VLANS 
sont bien configurés.

---

## 📚 Remarque

Cette activité m'a permis de découvrir un concept réseau que je n'avais jamais entendu parler auparavant, un concept robuste qui permet de nombreuse choses comme par exemple:
- une isolation des communications
- un contrôle d'accès plus précis
- une meilleur organisation du réseau

---

## ⭐ Niveau de difficulté : ⭐⭐☆☆☆

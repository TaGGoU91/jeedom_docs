# Vmware

## Présentation

Le but de ce plugin est de pouvoir obtenir des informations de vo(s)tre plateforme(s) Vmware et de pouvoir effectuer quelques actions sur vos VMS en cas de besoin.

Le plugin ne contient pas de dépendances.
Le pilotage des VMs sera effectué via SSH. 

![introduction01](../../images/vmware_icon.png)


## Prérequis 

Le seul prérequis est le suivant : 
* Autoriser l'accès SSH sur vo(s)tre serveur(s) ESXi


## Configuration

### Configuration générale

Il n'y a pas de paramètre particulier au niveau de la configuration du plugin.

### Ajouter un équipement de type serveur ESXi

* Cliquer sur le bouton Ajouter sur la page du plugin Vmware
* Saisir le nom de votre équipement
* Cliquer sur OK

Sur la page de l'équipement ESXi il faudra saisir les informations suivantes :

* Adresse IP de l'hôte ESXi
* Login  (Vous pouvez créer un compte dédié pour ce besoin en limitant les droits de ce compte si vous le souhaitez)
* Mot de passe
* Sauvegarder l'équipement ESXi -> 2 fois


## Informations

Lors de la sauvegarde de l'ESXi, l'ESXi va être interrogé pour créer un équipement par VM. Celà prend quelques dizaines de secondes selon la quantité de VMs configurées (constaté entre 10secondes pour 5 Vms  et 180 secondes pour 50 Vms).

Chaque VM aura les informations suivantes :
* Nombre de snapshot
* Liste des snapshots
* Statut des Vmware Tools
* Allumée ou éteinte ? 
* Système d'exploitation
* Quantité RAM Total
* Nombre de CPU
* Nombre de core par CPU


Chaque VM aura les commandes suivantes :
* Reboot OS
* Reboot Hard
* Stop OS
* Stop Hard
* Power On
* Prendre un snapshot
* Supprimer un snapshot

## Paramètres de la commande prendre un snapshot :

Le champ Nom - Description prend les paramètres suivants - **Attention pas d'espace dans le champ Description** :
* Nom=NomDeVotreSnapshot Description=Description_De_Votre_Snapshot


Si vous souhaitez utiliser des espaces dans le nom ou la description il faut saisir les informations comme ceci :
* Nom="Nom de votre snapshot" Description="Description de votre snapshot"

> **Attention** à respecter les majuscules pour Nom et Description ainsi que l'espace avant Description.


Le champ Memory permet de dire si vous souhaitez avoir l'état mémoire de la VM lors du snapshot, il prend le paramètre suivant :
* NON
* OUI

## Paramètre de la commande supprimer un snapshot :
Le champ Nom du snap est à remplir ainsi :
* Nom=NomDeVotreSnapshot

Si vous avez des espaces dans le nom du snapshot il peut l'être de la façon suivante : 
* Nom="Nom de votre snapshot"

## Idée de scénario
Envoyer une alerte sur le nombre de snapshot associé à une VM -> Trop de snapshots ça n'est pas bon
Envoyer une alerte sur présence de snapshot dans une VM depuis XX jours -> Conserver un snapshot trop longtemps n'est pas une bonne idée

Faire une interaction appelant le scénario suivant (C'est l'idée de base qui m'a poussé à créer ce plugin : faciliter les actions de mises à jour du core jeedom tout en sécurisant cette mise à jour) :
* Créer un snapshot
* Faire les mises à jours de votre jeedom via Jeelink
* Planifier un ASK pour suppression du snapshot dans X jours
* Supprimer ou non le snapshot en fonction de la réponse au ASK


## FAQ

> Rien à signaler à l'heure actuelle


## Troubleshooting

> Si vous avez un quelconque problème avec le plugin, passer le log en débug et communiquer le moi


## Changelog

[Voir la page dédiée](changelog.md).

# Vmware

## Présentation

Le but de ce plugin est de pouvoir obtenir des informations de vo(s)tre plateforme(s) Vmware et de pouvoir effectuer quelques actions sur vos VMS en cas de besoin.

Le plugin ne contient pas de dépendances.
Le pilotage des VMs sera effectué via SSH. 

![introduction01](../../../images/vmware/vmware_icon.png)


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
* Port SSH (22 sera utilisé si le champ est vide)
* Sauvegarder l'équipement ESXi


## Informations

Lors de la sauvegarde de l'ESXi, l'ESXi n'est pas interrogé directement.

> Il faut utiliser le bouton synchroniser ou la commande Refresh pour lancer l'interrogation de l'ESXi et récupérer les informations de l'ESXI et de ses VMs. Celà prend quelques dizaines de secondes selon la quantité de VMs configurées (constaté entre 10 secondes pour 5 Vms  et 180 secondes pour 50 Vms).

Chaque VM aura les informations suivantes :
* Nombre de snapshot
* Liste des snapshots
* Statut des Vmware Tools : Démarré ![introduction01](../../../images/vmware/coche_verte.png) / Pas Démarré ![introduction01](../../../images/vmware/coche_orange.png) / Pas à jour ![introduction01](../../../images/vmware/roue_crantee_orange.png) / Pas Installé ![introduction01](../../../images/vmware/croix_rouge.png)
* Etat de la VM : Allumée ![introduction01](../../../images/vmware/coche_verte.png) / Eteinte ![introduction01](../../../images/vmware/croix_rouge.png)
* Système d'exploitation
* Quantité de RAM totale
* Nombre de CPU
* Nombre de core par CPU
* Uptime en secondes (0 si éteinte)
* Uptime de la VM, pas de l'OS, affiché au format Years / Months / Days / Hours / Minutes / Seconds 
* Utilisation Processeur (MHz) permet de suivre via le cron5 l'utilisation CPU de chaque VMs
* Utilisation Mémoire (GB) permet de suivre via le cron5 l'utilisation mémoire de chaque VMs
* Ajout sur les VMs d'une commande VM Présente afin de savoir si la VM est encore présente sur VMWARE. Attention, les VMs doivent avoir le même nom entre Jeedom et VMWARE, bien respecter la casse


Chaque VM aura les commandes action suivantes :
* Reboot OS -> Equivalent VMWARE : Restart -  Vmware Tools requis
* Reboot Hard -> Equivalent VMWARE : Reset
* Stop OS -> Equivalent VMWARE : ShutDown - Vmware Tools requis
* Stop Hard -> Equivalent VMWARE : PowerOff
* Power On -> Equivalent VMWARE : PowerOn
* Prendre un snapshot -> Plus de détails en dessous sur les options de la commande
* Supprimer un snapshot -> Plus de détails en dessous sur les options de la commande

Chaque ESXi aura les informations suivantes : 
* Nombre de VM
* Liste des VMs
* Mise à jour de la version de l'ESXi disponible ? (Actualisation 1 fois par jour via le CronDaily)
* Système d'exploitation
* Quantité de RAM totale
* Nombre de CPU
* Nombre de core par CPU
* Uptime en secondes
* Uptime affiché au format Years / Months / Days / Hours / Minutes / Seconds 
* Utilisation Processeur (MHz) permet de suivre via le cron5 l'utilisation CPU du serveur
* Utilisation Mémoire (GB) permet de suivre via le cron5 l'utilisation Mémoire du serveur
* Température disque X ou X démarre à 1 et s'incrémente en fonction du nombre de disque dur connecté sur l'ESXi
* Online prennant les valeurs Oui/Non en fonction du fait que le plugin arrive ou non à initier une connexion SSH sur votre serveur ESXi
* Load average 1
* Load average 5
* Load average 15
* Etat du mode maintenance

Chaque ESXi aura les commandes action suivantes : 
* Mise en maintenance
* Sortie de maintenance
* Stop (10 secondes de délai)
* Reboot (10 secondes de délai)


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

##### Scénario 1
Envoyer une alerte sur le nombre de snapshot associé à une VM -> Trop de snapshots ça n'est pas bon

##### Scénario 2
Envoyer une alerte sur présence de snapshot dans une VM depuis XX jours -> Conserver un snapshot trop longtemps n'est pas une bonne idée

##### Scénario 3
Faire une interaction appelant le scénario suivant (C'est l'idée de base qui m'a poussé à créer ce plugin : faciliter les actions de mises à jour du core jeedom tout en sécurisant cette mise à jour) :
* Créer un snapshot
* Faire les mises à jours de votre jeedom via Jeelink
* Planifier un ASK pour suppression du snapshot dans X jours
* Supprimer ou non le snapshot en fonction de la réponse au ASK

##### Scénario 4
Envoyer une alerte si la commande Mise à jour disponible sur l'ESXi nous informe de la présence d'une mise à jour afin de pouvoir prévoir de le mettre à jour

##### Scénario 5 
Surveiller si une VM s'éteint, surveiller si une VM n'a plus ses VMWARE Tools fonctionnel, etc...

## Cron

Le plugin s'appuie sur trois crons
* cron5 -> met à jour les informations sur les loadAverage CPU/ RAM / etc et température du/des disque(s)
* cronHourly -> met à jour toutes les heures les informations sur vo(s)tre ESXi(s) et les VMs
* cronDaily -> met à jour une fois par jour la présence ou non de mise à jour pour vo(s)tre ESXi(s)

> Cela est désactivable dans la page de configuration du plugin vmware
<p align="center">
  <img src="https://github.com/TaGGoU91/jeedom_docs/blob/master/images/vmware/cron_plugin.png?raw=true" alt="Liste des Crons"/>
</p>


## FAQ

> Si vous avez un statut sans icone pour les vmwares Tools, merci de me l'indiquer afin que je puisse le rajouter

> Si vous ajoutez un deuxième disque (HDD/SSD) et que la commande température ne se créée pas automatiquement, supprimer la commande existante et attendre le cron5

> L'accès au menu de gauche (disponible en V3) est possible en cliquant sur l'icone en forme de maison située à gauche du texte : Mes équipements VMWARE

> Si vous souhaitez afficher complétement le contenu pré rempli des commandes de créations et suppression de snapshot il faut ajouter ce qui suit en personnalisation avancée CSS de jeedom : <br/> [data-eqtype="vmware"] [data-subtype="message"] {width:346px !important;}


## Troubleshooting

> Si vous avez un quelconque problème avec le plugin, passer le log en débug et communiquez le sur [Community](https://community.jeedom.com/) en créant un sujet et en taggant le plugin si vous n'avez pas trouvé une réponse existante corrigeant votre problème.


## Changelog

[Voir la page dédiée](../changelog.md).

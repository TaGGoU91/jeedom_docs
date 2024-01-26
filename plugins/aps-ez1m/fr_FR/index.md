# APS EZ1M

## Présentation

Le but de ce plugin est de pouvoir obtenir des informations de vo(s)tre micro-onduleur(s) APSystems modèle EZ1-M et de pouvoir limiter la puissance et/ou de le ou les éteindre en cas de besoin.

Le pilotage et la récupération des informations est fait via une API locale activable sur le micro-onduleur. 

![introduction01](../../../images/vmware/vmware_icon.pngg)


## Prérequis 

Il faudra les prérequis suivants afin de pouvoir faire fonctionner correctement le plugin : 
* Python 3.8 minimum, testé sur python 3.11 uniquement pour l'instant
* Module python 
* Activer le mode local sur votre/vos micro-onduleur(s)

## Configuration

### Configuration générale

Il n'y a pas de paramètre particulier au niveau de la configuration du plugin.

### Ajouter un micro-onduleur

* Cliquer sur le bouton Ajouter sur la page du plugin
* Saisir le nom de votre équipement
* Cliquer sur OK

Sur la page de l'équipement il faudra saisir les informations suivantes :

* Adresse IP de votre micro-onduleur
* Sauvegarder l'équipement

########## TO BE COMPLETED ###########

## Informations

Lors de la sauvegarde du micro-onduleur, le micro-onduleur n'est pas interrogé directement.

> A compléter ou supprimer.


Chaque micro-onduleur aura les informations suivantes : 
* A completer 
* A commpleter

Chaque micro-onduleur aura les commandes action suivantes : 
* A completer 
* A commpleter


## Cron

Le plugin s'appuie sur trois crons
* cron -> met à jour toutes les informations tous les minutes

> Cela est désactivable dans la page de configuration du plugin vmware
<p align="center">
  <img src="https://github.com/TaGGoU91/jeedom_docs/blob/master/images/vmware/cron_plugin.png?raw=true" alt="Liste des Crons"/>
</p>


## FAQ

## Troubleshooting

## Changelog

[Voir la page dédiée](../changelog.md).

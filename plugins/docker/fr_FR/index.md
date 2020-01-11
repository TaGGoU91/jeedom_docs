# Docker

## Présentation

Le but de ce plugin est de pouvoir obtenir des informations de vo(s)tre plateforme(s) Docker et de pouvoir effectuer quelques actions sur vos container en cas de besoin.

Le plugin ne contient pas de dépendances.
Le pilotage et l'interrogation du docker et des containers seront effectués via SSH. 

![introduction01](../../../images/docker/docker_icon.png)


## Prérequis 

Voici ce dont le plugin a besoin : 
* Créer un compte dédié avec un mot de passe assez compliqué (en évitant le caractère  (vous pouvez utiliser un compte existant bien entendu) sur le système hébergeant votre docker
* Rajouter l'utilisateur dans le groupe administrateur (pour faire du SSH) si vous êtes sur un synology
* Modifier le fichier sudoers pour autoriser le compte nouvellement créé à utiliser la commande docker, il faut ajouter ceci tout en bas du fichier sudoers (il faut être en root pour faire cette modification) (sudo -i sur un synology)
VOTRE_USER  ALL=(ALL) NOPASSWD: /usr/local/bin/docker

## Configuration

### Configuration générale

Il n'y a pas de paramètre particulier au niveau de la configuration du plugin.

### Ajouter un équipement de type DOCKER

* Cliquer sur le bouton Ajouter sur la page du plugin Vmware
* Saisir le nom de votre équipement
* Cliquer sur OK

Sur la page de l'équipement DOCKER il faudra saisir les informations suivantes :

* Adresse IP de l'hôte hébergeant votre DOCKER
* Login  (Vous pouvez créer un compte dédié pour ce besoin en limitant les droits de ce compte si vous le souhaitez comme expliqué en prérequis)
* Mot de passe
* Port SSH (22 sera utilisé si le champ est vide)
* Sauvegarder l'équipement DOCKER


## Informations

Lors de la sauvegarde du DOCKER, le DOCKER n'est pas interrogé directement.

> Il faut utiliser le bouton synchroniser ou la commande Refresh pour lancer l'interrogation du DOCKER et récupérer les informations du DOCKER et des containers. Celà prend quelques secondes selon la quantité de containers déployés.

Chaque container aura les informations suivantes :
* ID du container
* Nom
* Statut du container
* Image source
* Dernier démarrage


Chaque VM aura les commandes suivantes :
* Start
* Reboot
* Stop
* Kill


Un DOCKER aura les informations suivantes : 
* Nombre de Containers
* Nombre de Containers allumés
* Nombre de Containers en pauses
* Nombre de Containers éteints
* Nombre d'image disponible
* Version du docker

## Cron

Le plugin s'appuie sur 1 cron
* cron5 -> met à jour toutes les 5 minutes les informations de vo(s)tre DOCKER(s) et des containers associés

> Cela est désactivable dans la page de configuration du plugin docker
<p align="center">
  <img src="https://github.com/TaGGoU91/jeedom_docs/blob/master/images/docker/cron_plugin.png?raw=true" alt="Liste des Crons"/>
</p>


## FAQ

> Si l'accès SSH est non fonctionnel, vérifiez que vous avez bien configuré l'accès en utilisant putty par exemple et en entrant une commande de test


## Troubleshooting

> Si vous avez un quelconque problème avec le plugin, passer le log en débug et communiquez le moi via un [Message Privé](https://www.jeedom.com/forum/ucp.php?i=pm&mode=compose) sur le forum Jeedom à mon attention : TaG


## Changelog

[Voir la page dédiée](../changelog.md).

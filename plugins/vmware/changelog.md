# Changelog

Information : Si une mise à jour est disponible et que le changelog n'indique rien c'est que les modifications apportées sont mineures (modification de la doc, ajout/suppression de commentaires, etc). Il n'y a donc pas lieu de s'inquiéter.

## Septembre 2019
### 05/09/2019 
Correction : le bouton synchroniser à gauche d'un ESXI, met à jour toutes les informations, il en manquait certaines qui n'étaient synchro que via le cron hourly ou un refresh sur chacune des VMs
Début de l'ajout des traductions

### 04/09/2019 
Correction d'un bug : Lorque l'on change le nom de l'équipement de type ESXi dans jeedom, la configuration n'était pas mise à jour sur l'équipement ESXi et les équipements VM du plugin. Après une synchronisation l'information est bien mise à jour.

### 03/09/2019 
Suppression du widget spécifique -> Passage sur les widgets intégrés au core de Jeedom.<br/>
Remise en ligne de la coche pour afficher ou non une commande.<br/>
Ordre des commandes définies dans le code (pour la première création des VMs/ESXi) ensuite vous êtes libre de modifier l'ordre bien entendu.<br/>
Il faut supprimer l'ESXi et les VMs si vous souhaitez profiter de l'ordre de commandes lors de la création des équipements.

### 02/09/2019 
Mise en ligne de la version stable suite à la validation de l'équipe Jeedom.<br/>
Correction du rechargement de la page après avoir cliqué sur Synchroniser (pour la V3 de Jeedom).

### 01/09/2019 
Mise en ligne du plugin sur le market Jeedom - Attente validation du plugin par l'équipe Jeedom

## Aout 2019
### 15/08/2019 
Partage avec des beta-testeurs pour validation et remontée d'information - V 1.0

# Changelog

Information : Si une mise à jour est disponible et que le changelog n'indique rien c'est que les modifications apportées sont mineures (modification de la doc, ajout/suppression de commentaires, etc). Il n'y a donc pas lieu de s'inquiéter.

## Septembre 2019
24/09/2019
Ajout de la traduction en Anglais

### 17/09/2019
Ajout commande Utilisation Mémoire sur VM et ESXi afin de suivre l'usage Mémoire des VMs et du serveur ESXi. Mise à jour toutes les 5 minutes via le CRON5. 
Cliquer sur Synchroniser afin de créer la commande sur les VMs et l'ESXi.

### 16/09/2019
Ajout commande Utilisation Processeur sur VM et ESXi afin de suivre l'usage CPU des VMs et du serveur ESXi. Mise à jour toutes les 5 minutes via le CRON5. 
Cliquer sur Synchroniser afin de créer la commande sur les VMs et l'ESXi.

### 13/09/2019
Ajout dans la modal Santé de l'uptime des VMs

### 12/09/2019 
Renommage commande uptime en uptime (secondes)
Ajout des commandes uptime (convertie au format Years/Months/Days/Hours/Minutes/Secondes) sur les équipements de type VM et ESXi (Cliquer sur Save pour la créer sur l'ESXi, une erreur apparait, mais ça fonctionne comme attendu). Ensuite cliquer sur synchroniser pour créer la commande sur les VMs et mettre à jour la valeur sur les VMs et l'ESXi.
Correction d'un bug qui apparait si on a deux vms contenant la même trame genre : monjeedom et une autre jeedom. Selon l'ordre de création dans l'ESXi, une action sur la VM nommée jeedom sera faite sur la VM nommée monjeedom. Ce bug n'est plus d'actualité.

### 11/09/2019 
Ajout des commandes uptime (valeur en secondes) sur les équipements de type VM et ESXi (Cliquer sur Save pour la créer sur l'ESXi). Ensuite cliquer sur synchroniser pour créer la commande sur les VMs et mettre à jour la valeur sur les VMs et l'ESXi.

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

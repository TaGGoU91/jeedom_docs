# Changelog VMWARE

Information : Si une mise à jour est disponible et que le changelog n'indique rien c'est que les modifications apportées sont mineures (modification de la doc, ajout/suppression de commentaires, etc). Il n'y a donc pas lieu de s'inquiéter.

## Mai 2020
### 24/05/2020
Modification de la partie Température Disque dur de vos ESXi. La commande nommée Température disque X peut être supprimée une fois le cron5 passé.<br/>
Les commandes de remplacement débutent par un NEW afin de les identifier facilement. Ceci pour corriger un bug en cas de présence de plusieurs disque dur du même fabricant et modèle.<br/>

### 23/05/2020
ATTENTION : Les mises à jours faites en beta et stable à partir du 23 Mai 2020 implique un big bang au niveau du nom logique des VMs, celà va dupliquer vos VMs. Ceci est un mal nécessaire. <br/>
Plus d'information disponible ici : https://community.jeedom.com/t/plugin-tiers-plugin-vmware/3032/67?u=tag
ATTENTION <br/>

Modification du contenu de la commande create snapshot afin d'indiquer comment remplir ce champ
Afin de voir le contenu entier, il faut ajouter ceci dans la personnalisation avancée de Jeedom : <br/>
[data-eqtype="vmware"] [data-subtype="message"] {width:346px !important;}


## Janvier 2020
### 23/01/2020
Modification de l'icone située à gauche du texte : Mes équipements VMWARE<br/>
L'accès au menu de gauche (disponible en V3) est possible en cliquant sur l'icone en forme de maison située à gauche du texte : Mes équipements VMWARE


### 13/01/2020
Modification de l'icone du plugin (ajout de l'espace sous l'icone pour être à jour des règles graphique<br/>
Modification du code pour que le rendu dans la page du plugin soit cohérent pour les VMs (conservation de l'icone sans espace en dessous).


## Décembre 2019
### 11/12/2019
Ajout du nombre de snapshots associés à une VM dans la page équipement de chaque VM

### 09/12/2019
Ajout d'un message dans le centre de message en cas de connexion SSH impossible pour indiquer de vérifier si le protocole SSH est actif sur le serveur ESXi.<br/>
Modification de l'application des templates sur les commandes numériques de type info. Le template "line" était forcé par défaut et écrasait le template sélectionné manuellement.

## Novembre 2019
### 01/11/2019
Modification du sous type de certaines commandes en sous type numeric au lieu du sous type autres. Et sur ces mêmes commandes, applications du widget Line pour plus de lisibilité.<br/>
Suppression d'une mauvaise unité sur les commandes load average 1/5/15 qui étaient avec Mhz en unité sur l'ESXi.<br/>
Ajout de l'unité °C sur la commande température disque de l'ESXi.

## Octobre 2019
### 31/10/2019
Ajout des commandes Load average 1/5/15 permettant d'obtenir le load average à 1min/5min/15min toutes les 5 minutes de l'ESXi.<br/>
Pensez à sauvegarder votre équipement ESXi si vous souhaitez les voir apparaitre rapidement.

### 29/10/2019
Ajout de la commande Online sur l'ESXi afin de savoir si l'ESXi est joignable ou non en SSH, les valeurs sont Oui/Non.<br/>
Ajout du paramètre Port SSH dans l'ESXi afin de spécifier un port **Le port 22 sera utilisé par défaut si aucun port n'est définit**


## Septembre 2019
### 27/09/2019
Ajout de la commande Température disque X ou X débute à 1 et s'incrémente à chaque disque dur trouvé sur l'ESXI. Cela permettant d'avoir une valeur toutes les 5 minutes sur l'ESXi. Cette commande est historisée par défaut.

### 24/09/2019
Ajout de la traduction en Anglais.

### 17/09/2019
Ajout commande Utilisation Mémoire sur VM et ESXi afin de suivre l'usage Mémoire des VMs et du serveur ESXi. Mise à jour toutes les 5 minutes via le CRON5. <br/>
Cliquer sur Synchroniser afin de créer la commande sur les VMs et l'ESXi.

### 16/09/2019
Ajout commande Utilisation Processeur sur VM et ESXi afin de suivre l'usage CPU des VMs et du serveur ESXi. Mise à jour toutes les 5 minutes via le CRON5. <br/>
Cliquer sur Synchroniser afin de créer la commande sur les VMs et l'ESXi.

### 13/09/2019
Ajout dans la modal Santé de l'uptime des VMs.

### 12/09/2019 
Renommage commande uptime en uptime (secondes)
Ajout des commandes uptime (convertie au format Years/Months/Days/Hours/Minutes/Secondes) sur les équipements de type VM et ESXi (Cliquer sur Save pour la créer sur l'ESXi, une erreur apparait, mais ça fonctionne comme attendu). Ensuite cliquer sur synchroniser pour créer la commande sur les VMs et mettre à jour la valeur sur les VMs et l'ESXi.<br/>
Correction d'un bug qui apparait si on a deux vms contenant la même trame genre : monjeedom et une autre jeedom. Selon l'ordre de création dans l'ESXi, une action sur la VM nommée jeedom sera faite sur la VM nommée monjeedom. Ce bug n'est plus d'actualité.

### 11/09/2019 
Ajout des commandes uptime (valeur en secondes) sur les équipements de type VM et ESXi (Cliquer sur Save pour la créer sur l'ESXi). Ensuite cliquer sur synchroniser pour créer la commande sur les VMs et mettre à jour la valeur sur les VMs et l'ESXi.

### 05/09/2019 
Correction : le bouton synchroniser à gauche d'un ESXI, met à jour toutes les informations, il en manquait certaines qui n'étaient synchro que via le cron hourly ou un refresh sur chacune des VMs.<br/>
Début de l'ajout des traductions.

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
Mise en ligne du plugin sur le market Jeedom - Attente validation du plugin par l'équipe Jeedom.

## Aout 2019
### 15/08/2019 
Partage avec des beta-testeurs pour validation et remontée d'information - V 1.0.

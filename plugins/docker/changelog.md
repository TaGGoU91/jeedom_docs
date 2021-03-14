# Changelog Docker

Information : Si une mise à jour est disponible et que le changelog n'indique rien c'est que les modifications apportées sont mineures (modification de la doc, ajout/suppression de commentaires, etc). Il n'y a donc pas lieu de s'inquiéter.

## Mars 2021
Modification de la récupération des informations pour les commandes Uptime (S) / Dernier Démarrage.

## Décembre 2020

### 30/12/2020
Modification choix objet parents - compatible v3/v4/v4.1 cf : https://doc.jeedom.com/fr_FR/dev/core4.1

### 12/12/2020
Ajout du champ pour la compatibilité V4 lors d'une migration V3->V4, ceci afin d'éviter d'avoir un message d'alerte.

## Janvier 2020
### 29/01/2020
Ajout d'une liste déroulante pour choisir le type d'hôte docker (Linux / Synology). ATTENTION à bien choisir votre type d'hôte une fois la mise à jour effectuée<br />
Modification des appels en fonction du type d'hote<br />
Ménage dans les logs

### 26/01/2020
Correction de bug : Non affichage dans la page équipement d'un container du nom du docker parent

### 23/01/2020
Ajout de la commande Santé qui permet d'avoir l'état de santé d'un container<br/>
Modification de l'icone située à gauche du texte : Mes équipements Docker<br/>
L'accès au menu de gauche (disponible en V3) est possible en cliquant sur l'icone Docker située à gauche du texte : Mes équipements Docker

### 22/01/2020
Remplacement de la commande reboot par la commande restart. Il faut supprimer la commande reboot manuellement.<br/>
Ajout de la commande uptime (s) (pour avoir un uptime en secondes)<br/>
Ajout de la commande Online sur les containers (format binaire)<br/>
Modification de la commande online sur le(s) DOCKER(s) (passage en binaire au lieu de string)<br/>
Docker Parent (pour connaitre le parent d'un container afin de gagner en lisibilité)<br/>

### 21/01/2020
Ajout des commandes info Mémoire utilisée et CPU utilisé. Commandes qui se mettent à jour toutes les 5 minutes via le cron5 et/ou via un clic sur refresh sur chaque container par exemple.

### 12/01/2020
Version 1.0 du plugin docker

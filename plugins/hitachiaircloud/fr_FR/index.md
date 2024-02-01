# HITACHI AirCloud

## Présentation

Le but de ce plugin est de pouvoir obtenir des informations de votre PAC Hitachi pilotée par l'application Hitachi AirCloud GO. Il permet également de gérer l'allumage, l'extinction et le changement des paramètres.

L'icône n'est pas la plus jolie, je cherche une inspiration pour la remplacer, n'hésitez pas si vous avez une idée pour l'icône ;)

## Compatabilité
Liste des PAC validées :
* RAK-DJ50PHAE

## Prérequis 

A compléter


## Configuration

### Configuration générale

Il faudra saisir votre login et mot de passe utilisés sur l'application Hitachi AirCloud GO. Attention, le login doit être au format e-mail, pas au format numéro de téléphone.
Il ne vous reste plus qu'à sauvegarder, les différentes PAC que vous possédez vont être ajoutées automatiquement. 


## Informations

L'API répond assez lentement et afin de ne pas l'attaquer trop souvent, j'ai mis en place le cron15 par défaut. L'action Rafraîchir permet bien entendu de rafraîchir au besoin les informations depuis un scénario. Mais il est ocnseillé de ne pas en abuser.


Chaque PAC aura les informations suivantes : 
* A compléter 

Chaque PAC aura les commandes action suivantes : 
* A compléter
* Rafraîchir

## Cron

Le plugin utilise la fonctionnalité cron15, donc nous avons un rafraichissement toutes les 15 minutes des informations.
> Cela est désactivable dans la page de configuration du plugin
<p align="center">
  <img src="https://github.com/TaGGoU91/jeedom_docs/blob/master/images/aps-ez1m/cron_plugin.png?raw=true" alt="Liste des Crons"/>
</p>


## FAQ

* Connexion impossible : Merci de vérifier votre login/mot de passe. Pour rappel, le compte utilisé doit être avec un identifiant au format e-mail, mais au format numéro de téléphone.

## Troubleshooting

Si vous n'arrivez pas à obtenir les informations de votre PAC, merci de mettre le log en débug et de poster sur community

## Changelog

[Voir la page dédiée](../changelog.md).

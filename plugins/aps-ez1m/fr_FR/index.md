# APS EZ1M

## Présentation

Le but de ce plugin est de pouvoir obtenir des informations de votre micro-onduleur APSystems modèle EZ1-M. Il permet également de limiter la puissance et/ou de l'éteindre en cas de besoin.

Le pilotage et la récupération des informations est fait via une API locale activable sur le micro-onduleur. Une fois cette API locale activée, la communication avec le cloud est interrompue. C'est pour l'instant ainsi que ça fonctionne, peut-être qu'APS changera ce fonctionement à l'avenir en conservant le cloud et l'API locale.

Plusieurs micro-onduleurs sont ajoutables et gérables indépendamment les uns des autres.

## Prérequis 

Il faudra le prérequi suivant afin de pouvoir faire fonctionner correctement le plugin : 
* Activer le mode local sur votre micro-onduleur

Afin d'activer le mode local, merci de suivre la procédure ci-dessous depuis l'application AP EasyPower :
 * Déconnecter vous de votre compte cloud pour revenir à la page de connexion, puis choisir Direct Connection
 * Cliquer sur Connect New Device ou sur votre appareil s'il est déjà présent dans la liste
 * Cliquer en haut à droite sur l'icône des paramètres
 * Cliquer sur Local Mode
 * Choisir l'option Continious
 * Vous avez terminé, votre micro-onduleur est joignable localement


## Configuration

### Configuration générale

Il n'y a pas de paramètre particulier au niveau de la configuration du plugin.

### Ajouter un micro-onduleur

* Cliquer sur le bouton Ajouter sur la page du plugin
* Saisir le nom de votre équipement
* Cliquer sur OK

Sur la page de l'équipement il faudra saisir les informations suivantes :

* Adresse IP de votre micro-onduleur
* Port -> Optionnel c'est pour le cas ou le port viendrait à changer à l'avenir
* Sauvegarder l'équipement

## Informations

L'API n'est joignable qu'en journée. La nuit les valeurs ne seront donc pas mises à jour si vous faites votre première configuration de nuit. Il y a donc une vérification de la disponibilité de l'API. Si injoignable, on conserve les dernières valeurs connues.

Lors de la sauvegarde du micro-onduleur, le micro-onduleur n'est pas interrogé directement. Vous pouvez soit :
* Attendre le prochain cron, dans moins d'1 minute
* Cliquer sur le bouton Synchroniser
* Appeler l'action Rafraîchir depuis la liste des commandes


Chaque micro-onduleur aura les informations suivantes : 
* Power status : 0=On / 1=Off
* Max Power : Donne la valeur maximum autorisée en sortie AC du micro-onduleur. Entre 30W et 800W
* Total prod lifetime : Production totale depuis la mise en service du micro-onduleur des 2 entrées en Wh
* Total prod lifetime I1 : Production totale depuis la mise en service du micro-onduleur de l'entrée 1 en Wh
* Total prod lifetime I2 : Production totale depuis la mise en service du micro-onduleur de l'entrée 1 en Wh
* Total prod today : Production totale du jour des 2 entrées du micro-onduleur en Wh
* Total prod today I1 : Production totale du jour de l'entrée 1 du micro-onduleur en Wh
* Total prod today I2 : Production totale du jour de l'entrée 1 du micro-onduleur en Wh
* Total power : Puissance instantanée produite par les 2 entrées à l'instant T en W
* Power Input 1 : Puissance instantanée produite par l'entrée 1 à l'instant T en W
* Power Input 2 : Puissance instantanée produite par l'entrée 2 à l'instant T en W
* Device ID : ID du micro-onduleur, pratique si on a plusieurs micro-onduleurs
* Device Version : Version du firmware
* Alarm AC Output : au format X - Y -> Ou X est un binaire (0 = Normal / 1 = Alarm) et Y contient le message d'erreur
* Alarm input 1 : 0 = Normal / 1 = Alarm
* Alarm input 2 : 0 = Normal / 1 = Alarm
* Online : 0 = APi non joignable / 1 = Api joignable

Chaque micro-onduleur aura les commandes action suivantes : 
* Power Off EZ1M : Permet d'éteindre le micro-onduleur
* Power On EZ1M : Permet d'allumer le micro-onduleur
* Max Output Power : Permet de régler la valeur maximum de sortie du micro-onduleur entre 30W et 800W
* Rafraîchir

## Cron

Le plugin utilise la fonctionnalité cron, donc nous avons un rafraichissement toutes les minutes des informations.
> Cela est désactivable dans la page de configuration du plugin
<p align="center">
  <img src="https://github.com/TaGGoU91/jeedom_docs/blob/master/images/aps-ez1m/cron_plugin.png?raw=true" alt="Liste des Crons"/>
</p>


## FAQ

* Connexion directe impossible : Il faut que le micro-onduleur produise, donc ça ne peut être fait qu'en journée

## Troubleshooting

Si vous n'arrivez pas à obtenir les informations de votre micro-onduleur, merci de mettre le log en débug et de poster sur community

## Changelog

[Voir la page dédiée](../changelog.md).

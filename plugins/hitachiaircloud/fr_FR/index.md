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
Il ne vous reste plus qu'à sauvegarder, fermer la fenêtre de configuration puis cliquer sur le bouton synchroniser, les différentes PAC que vous possédez vont être ajoutées automatiquement. 


## Informations

L'API répond assez lentement et afin de ne pas l'attaquer trop souvent, j'ai mis en place le cronHourly par défaut. L'action Rafraîchir permet bien entendu de rafraîchir au besoin les informations depuis un scénario. **Il est conseillé de ne pas en abuser**.


Chaque PAC aura les informations suivantes : 
* Room temperature : Témpérature de la pièce
* Target temperature : Température de consigne / Température demandée
* Mode : Mode de la PAC -> CHAUFFAGE / CLIMATISATION / VENTILATION / DRY / AUTO
* Humidity : Je n'ai pas de capteur d'humidité sur la mienne, si vous avez des choses incohérentes, remontez le moi
* Power status : Etat de la PAC -> ON/OFF
* Fan speed : Vitesse de la ventilation -> 1/2/3/4/5/AUTO
* Fan swing : Balayage -> OFF/VERTICAL      Je n'ai que le balayage vertical, n'hésitez pas si vous avez l'horizontal à me donner l'information en fonction de ce que le plugin affiche
* Last update : Date de dernière mise à jour des informations
* Last update - Timestamp : Date de dernière mise à jour des informations au format timestamp
* Last power on : Date de dernier allumage
* Last power on - Timestamp : Date de dernier allumage au format timestamp
* Error : Erreur trouvée, n'en n'ayant pas encore eu, je n'ai pas trop d'information pour pouvoir les intercepter/traduire. N'hésitez pas à m'en remonter en fonction de ce que le plugin affiche

Chaque PAC aura les commandes action suivantes : 
* Power Off : Récupère les informations en live puis envoi l'ordre d'extinction, aucun paramètre requis
* Power On : Permet d'allumer la PAC en définissant des paramètres, voir encart dédié plus bas

## Paramètres de la commande Power On :

L'idée est la suivante : 
power on <mode> <temp> <fanspeed> <fanswing>

L'appel à la commande à la commande Power On doit s'effectuer ainsi dans un scénario :
mode=HEATING temp=19 fanspeed=LV1 fanswing=OFF

Voici quelques exemples d'appels possible :
<p align="center">
  <img src="https://github.com/TaGGoU91/jeedom_docs/blob/master/images/hitachiaircloud/scenario_exemples.png?raw=true" alt="Exemple d'appels dans un scénario"/>
</p>

Liste des options
* mode : HEATING / COOLING / FAN / DRY / AUTO    -> HEATING=Chauffage / COOLING=Froid / FAN=Ventilation / DRY=Déshumidification / AUTO=Auto
* temp : XX / XX.X                               -> Exemple 20=20°C / 20.5=20.5°C de température de consigne
* fanspeed : LV1 / LV2 / LV3 / LV4 / LV5 / AUTO  -> LV1=Vitesse1 / LV2=Vitesse2 / LVX = vitesse X / Auto = Automatique
* fanswing : VERTICAL/OFF                              -> Balayage VERTICAL=On / Balayage Off

> [!IMPORTANT]
> La température n'est pas utilisée dans l'application en mode FAN/Ventilation, mais pour simplifier, c'est géré dans le code comme ça vous pouvez copier/coller vos commandes et ajuster les paramètres. Mais en ventilation la température ne sert à rien, ce qui est assez logique. Je préfère juste le préciser ici.

## Cron

Le plugin utilise la fonctionnalité cronHourly, donc nous avons un rafraichissement toutes les heures des informations.
> Cela est désactivable dans la page de configuration du plugin
<p align="center">
  <img src="https://github.com/TaGGoU91/jeedom_docs/blob/master/images/hitachiaircloud/cron_plugin.png?raw=true" alt="Liste des Crons"/>
</p>


## FAQ

* Connexion impossible : Merci de vérifier votre login/mot de passe. **Pour rappel, le compte utilisé doit être avec un identifiant au format e-mail, mais au format numéro de téléphone**.

## Troubleshooting

Si vous n'arrivez pas à obtenir les informations de votre PAC, merci de mettre le log en débug et de poster sur community en ouvrant un sujet.

## Changelog

[Voir la page dédiée](../changelog.md).

# Vmware

## Présentation

Le but de ce plugin est de pouvoir obtenir des informations de vo(s)tre plateforme(s) Vmware et de pouvoir effectuer quelques actions sur vos VMS.

Le plugin installe en tant que dépendances powershell et le module powercli de chez Vmware pour obtenir les informations. Ces dépendances sont installées lors de l'installation du plugin.
Le pilotage des VMs sera effectué via SSH. 
La suppression de la partie powershell est à l'étude.


## Prérequis 

Les prérequis sont les suivants : 
* Débian 8 minimum
* Version d'ESXi : 6.5 minimum

## Configuration

### Configuration générale

Il n'y a pas de paramètre particulier au niveau de la configuration du plugin, il faut juste patienter le temps que les dépendances soient installées. Durée approximative pour cette étape 4 minutes.

### Configuration d'un équipement

#### Utilisation de Powercli

Un équipement ESXi à besoin des paramètres suivants lors de l'utilisation de l'option PowerCli :

* Adresse IP de l'hôte ESXi sur votre réseau
* Login
* Mot de passe


## Informations

Lors de la sauvegarde de l'ESXi, l'ESXi va être intérrogé pour créer 1 équipement par VM. Celà prend quelques dizaines de secondes selon la quantité de VMs configurées.

Chaque VM aura les informations suivantes :
* Quantité RAM Total
* Quantité RAM utilisée (sur le dernier mois lissée toutes les 5 minutes)
* Espace disque total
* Espace disque restant
* Espace disque utilisé
* Nombre de CPU
* Nombre de core par CPU
* Nombre de snapshot
* Liste des snapshots
* Allumée ?

Chaque VM aura les commandes suivantes :
* Reboot OS
* Reboot Hard
* Stop OS
* Stop Hard
* Power On
* Prendre un snapshot
* Supprimer un snapshot

Paramètre de la commande prendre un snapshot :
Le champ Nom - Description prend les paramètres suivants :
* Nom=NomDeVotreSnapshot Description=Description_De_Votre_Snapshot
/*\ Attention à respecter les majuscules pour Nom et Description ainsi que l'espace avant Description. Pas d'espace dans le champ Description /*\

Le champ Memory permet de dire si vous souhaitez avoir l'état mémoire de la VM lors du snapshot, il prend le paramètre suivant :
* NON
ou
* OUI

Paramètre de la commande supprimer un snapshot :
Le champ Nom du snap est à remplir ainsi :
* Nom=NomDeVotreSnapshot

## Exemple d'idée de scénario
Envoyer une alerte sur nombre de snapshot associé à une VM
Envoyer une alerte sur présence de snapshot dans une VM

Faire une interaction appelant le scénario suivant (l'idée de base de ce plugin, faciliter les actions de mises à jour du core jeedom tout en sécurisant cette mise à jour ) :
* Créer un snapshot
* Faire les mises à jours de votre jeedom via Jeelink
* Planifier un ASK pour suppression du snapshot dans X jours
* Supprimer ou non le snapshot en fonction de la réponse au ASK


## FAQ

> Les dépendances mettent du temps à s'installer.

L'installation dure environ 4 minutes, merci de patienter.


## Troubleshooting

> Les dépendances ne s'installent pas.

Mettre le plugin en mode debug et relancer l'installation des dépendances. Transmettre celà sur la page dédiée au plugin sur le forum : To Be Completed



## Changelog

[Voir la page dédiée](changelog.md).

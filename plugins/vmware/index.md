# Vmware

## Présentation

Le but de ce plugin est de pouvoir obtenir des informations de vo(s)tre plateforme(s) Vmware et de pouvoir piloter quelques actions sur vos VMS.

Le plugin installe en tant que dépendances powershell et le module powercli de chez Vmware pour obtenir les informations et piloter vos VMs. Ces dépendances sont installées lors de l'installation du plugin.
Une version utilisant les lignes de commandes Esxcli est également à l'étude, mais n'est pas fonctionnelle pour le moment.


## Prérequis 

Les prérequis sont les suivants : 
* Débian 8 minimum
* Version d'ESXi : 6.5 minimum

## Configuration

###Configuration générale

Il n'y a pas de paramètre particulier au niveau de la configuration du plugin, il faut juste patienter le temps que les dépendances soient installées. Durée approximative pour cette étape 3 minutes.

### Configuration d'un équipement

#### Utilisation de Powercli

Un équipement ESXi à besoin des paramètres lors de l'utilisation de l'option PowerCli :

* Adresse IP de l'hôte ESXi sur votre réseau
* Login
* Mot de passe




## FAQ

> Les dépendances mettent du temps à s'installer.

L'installation dure environ 4 minutes, il faut être patient.


## Troubleshooting

> Les dépendances ne s'installent pas.

Mettre le plugin en mode debug et relancer l'installation des dépendances. Transmettre celà sur la page dédiée au plugin sur le forum : 



## Changelog

[Voir la page dédiée](changelog.md).

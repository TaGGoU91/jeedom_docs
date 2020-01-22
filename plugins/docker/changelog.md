# Changelog Docker

Information : Si une mise à jour est disponible et que le changelog n'indique rien c'est que les modifications apportées sont mineures (modification de la doc, ajout/suppression de commentaires, etc). Il n'y a donc pas lieu de s'inquiéter.

## Janvier 2020
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

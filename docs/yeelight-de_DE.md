# Yeelight Wifi

## Création des équipements

Un bouton de scan permet de créer automatiquement toutes les lampes répondant au protocole Yeelight disponibles sur le réseau (uniquement celles qui n'existent pas déjà dans Jeedom, bien sûr).

## Yeelight Lampe Konfiguration

Une présentation complète de la gamme est disponible ici : [Article de présentation](https://lunarok-domotique.com/plugins-jeedom/xiaomi-home-jeedom/yeelight-xiaomi-wifi-lamp/).

Dans l'application Yeelight vous devez activer l'option de contrôle sur réseau local. C'est un switch à activer dans les options de chaque ampoule/bandeau.

## Commandes des équipements compatibles

Les lampes compatibles proposent les commandes suivantes par défaut : on / off / toggle / luminosité / enchainement

Certaines lampes ajoutent des commandes :

* Yeelight Blanc : pas d'autres commandes

* Desklamp : couleur de blanc

* Yeelight RGB : couleur RGB, couleur de blanc, mode jour, mode nuit, couleurs HSV

* Bandeau RGB : couleur RGB, couleur de blanc, mode jour, mode nuit, couleurs HSV

* Lampe de Chevet (socle doré) : couleur RGB, couleur de blanc, mode jour, mode nuit, couleurs HSV

* Yeelight Ceiling : couleur blanc, mode jour, mode nuit

### Commande enchainement des Yeelight

Pour les Yeelight, une commande spéciale est créée. Elle a vocation à être utilisée en scénario seulement, car on doit envoyer un contenu précis à la commande.

Voici un exemple commentée de cette commande message :

> 3 recover rgb,255,0,0,500,100-wait,400-rgb,255,255,0,500,100

* 3 : c'est un chiffre représentant le nombre de fois que la suite d'effets doit être appliquée avant de s'arrêter (0 veut dire illimité)

* recover : une des 3 options possibles pour la fin de l'enchaînement (recover = revient à l'état précédant l'enchaînement, off = s'éteint, stay = reste au statut de la fin de l'enchaînement)

* le troisième élément est la suite des états avec leur transition, il y en a 4 possibles (attention : il ne faut pas mettre d'espace) :

  * hsv : paramètres (hue,saturation,duration=300,brightness=100)

  * rgb : paramètres (red,green,blue,duration=300,brightness=100)

  * temp : paramètres (degrees,duration=300,brightness=100)

  * wait(duration=300)

Il faut bien entrer l'enchainement avec des - entre chaque effet. Pour un enchainement, il doit y avoir son nom et tous les paramètres séparés par des virgules
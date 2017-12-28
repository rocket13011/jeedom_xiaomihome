# Aplliances Wifi Xiaomi

## Création des équipements Wifi

Pour les équipements Wifi supplémentaires, il faut faire un ajout manuel.

Il faut renseigner pour tous les équipements supportés : adresse IP et sélectionner le type dans le ménu déroulant.

Il vous faut également le token. Pour obtenir le token, il suffit de cliquer sur le bouton bleu "Récupérer les infos", dans le cas où le token récupéré est une suite de 0 seulement ou de f seulement, il faut alors le récupérer manuellement à l'aide de la procédure ci-dessous.

### Récupérer le token d'un équipement manuellement

Pour le robot, entre autres, il est nécessaire de récupérer le token manuellement avant son intégration dans Jeedom.

Trois méthodes existent, la première avec l'outil [Mi Toolkit](https://github.com/ultrara1n/MiToolkit) qui va récupérer tous les token dans votre application Mi Home. Cela nécessite un Android avec le mode Debug USB activable.

Les deux autres sont basées sur une récupération de la base de données de Mi Home, une pour Android, une pour iPhone.

#### 1ère méthode : MiToolkit

Pour le télécharger : [https://github.com/ultrara1n/MiToolkit/releases](https://github.com/ultrara1n/MiToolkit/releases)

* Activez ADB sur votre téléphone (dans les options développeur)
* Lancez le fichier exe MiToolkit en tant qu'admin
* Passez l'application en anglais via le menu avec le drapeau allemand. L'application se ferme, il faut la relancer
* Choisissez "Extract Token"
* Choisissez "Extract Token", le laisser faire la sauvegarde sur le PC et ne pas mettre de mot de passe
* Les tokens apparaissent dans la fenêtre

#### 2ème méthode (Android) : aSQLiteManager

Via aSQLiteManager, on peut ouvrir la base de Mi Home. Attention, un téléphone rooté peut être nécessaire (merci _Gouzou_ pour la technique).

Les tokens sont dans la table devicerecord dans /data/data/com.xiaomi.smarthome./databases/miio2.db

Ce fichier, si il est transférable sur PC, devrait pouvoir être édité avec d'autres logiciels aussi.

#### 3ème méthode (iPhone)

Merci _pierre_ pour cette technique :

* Faites une sauvegarde de l'iPhone avec iTunes
* Ouvrez la sauvegarde avec [iPhoneBackup Viewer](http://www.imactools.com/iphonebackupviewer/) (si votre sauvegarde est cryptée, il faudra passer par la version payante)
* Dans Raw Data/com.xiaomi.mihome il y a plusieurs fichiers .sqllite, il faut extraire votreuserid_mihome.sqlite
* Ouvrez le fichier sqlite avec un viewer sqlite, par exemple DB Browser http://sqlitebrowser.org
* Cliquez sur "Ouvrir une base de données" puis " Parcourir les données" et enfin choisissez la table ZDEVICE
* Tout à droite, il doit y avoir une colonne ZTOKEN avec tous les tokens de vos périphériques Xiaomi

## Konfiguration von Wifi-Geräten

Cette section traite des équipements Wifi additionnels. Il n'est pas question de Yeelight ou de la gateway Aqara.

* *Xiaomi Mi Robot Vacuum* : online, statut, batterie, aspiration (force + slider, attention au delà de 77 vous dépasser le mode turbo), surface nettoyée, durée nettoyage, état des erreurs, puissance aspiration, démarrer, arrêter, pause, retour socle, fonction spot, "où es-tu ?", rafraîchir

* *Xiaomi Smart Mi Air Purifier* : statut, qualité d'air, humidité, température, filtre, vitesse, buzzer (on/off), led (action dessus aussi), démarrer/arrêter (avec les différents modes disponibles)

* *Xiaomi Smart Ultrasonic Humidifier* : statut, mode, humidité, humidité cible (+slider de set), température, buzzer (statut + activation), led (statut + activation), démarrer/arrêter (avec les différents modes disponibles)

* *Xiaomi Smart Air Quality Monitor PM2.5 Detector* : qualité d'air, batterie, rafraîchir

* *Xiaomi Mi Power Strip Wifi* : on, off, statut, température, Intensité, puissance, rafraîchir

* *Xiaomi Mi Power Plug Wifi* : on, off, statut, utilisation, voltage, charge voltage, charge puissance, puissance consommée, rafraîchir

* *Xiaomi Philips Eyecare Smart Lamp* : statut, on/off, luminosité (+slider), eyecare (statut, scenes + différents modes disponibles)

* *Xiaomi Philips Ceiling* : statut, on/off, luminosité (+slider), couleur de blanc (info+cmd), Auto CCT (statut+cmd), scènes (statut + activation scenes)

* *Xiaomi Philips E27* : statut, on/off, luminosité (+slider), couleur de blanc (info+cmd), Auto CCT (statut+cmd), scènes (statut + activation scènes)

* *Xiaomi Mi Electric Rice Cooker* : non implémenté en l'état

* *Ventilateur* : statut, température, humidité, buzzer (statut + activation), led (statut + activation), démarrer/arrêter (avec les différents modes disponibles), info vitesse et vitesse naturelle, rotation (et les commandes pour la paramétrer, tourner)
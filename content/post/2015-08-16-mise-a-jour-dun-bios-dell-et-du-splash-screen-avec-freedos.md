---
title: Mise à jour d’un bios Dell et du splash screen avec freeDos
author: JMAX
layout: post
date: 2015-08-16
categories:
  - Non classé
---
# Mise à jour du bios

Les programmes de mise de Dell tourne sous Dos, il existe un DOS libre le projet FreeDos, et un gentil gars qui met à disposition une image de freeDos préparée pour réaliser une clé bootable :

<!--more-->

http://www.chtaube.eu/computers/freedos/bootable-usb/

  * suivre sa procédure.
  * copier le programme de mise à jour dans la clé
  * booter avec la clé
  * sous freedos exécuter la mise à jour

&nbsp;

# Changer le splash screen

Le splash screen et l&rsquo;image charger à l&rsquo;allumage du PC. Dell fournit un soft pour le modifier :http://www.dell.com/support/home/us/en/19/drivers/driversdetails?c=us&l=en&s=dhs&driverid=R35826

Ce programme fonctionne sous windows, et à besoin d&rsquo;un lecteur de disquette:

  * Création d&rsquo;une disquette virtuelle :
  *       ~ $  fallocate -l 1474560 myimage.vf
  *       ~ $  head -c 1474560 /dev/zero > myimage.vf
  * Sous virtual box , assigner le fichier myimage.vf à un lecteur de disquette de winXp
  * sous WinXp exécuter le programme
  * copier les données de la disquette sur la clé FreeDos
  * booter sur la clé FreeDos
  * exécuter splash nom_image.bmp
  * et redémarrer <img src="http://www.labx.fr/wp-includes/images/smilies/simple-smile.png" alt=":)" class="wp-smiley" style="height: 1em; max-height: 1em;" />

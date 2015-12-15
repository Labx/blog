---
title: Création d’une nouvelle librairie ardino
author: JMAX
layout: post
date: 2012-08-07
categories:
  - Non classé
---
J&rsquo;ai le plaisir de vous annoncer une nouvelle librairie qui permet de modifier des variables global pendant l’exécution du programme.

les sources sont disponibles ici :
  
[git arduinoParam][1]

La syntaxe des commandes de l&rsquo;arduinoParam est inspirée des commandes AT

il existe trois type de commandes
  
* commande d&rsquo;écriture : Cmd=.
  
* commande de lecture : Cmd?
  
* commande d&rsquo;action : Cmd.

il y a trois caractères réservés
  
le . qui termine une commande d&rsquo;écriture ou d&rsquo;action
  
le ? qui termine une commande de lecture
  
le = qui permet de définir la valeur

une commande d’écriture accepte qu&rsquo;une seule valeur et cette valeur est entière non signé sur 16bit

la syntaxe a été pensée pour être utilisée sur des téléphones de base avec la liaison bluetooth

 [1]: https://github.com/jmax33/ArduinoParam

---
title: 'Arduino : initiation'
author: Julien D.
layout: post
date: 2011-06-02
Temper Level:
  - Low
categories:
  - Ressources
---
Pour faire suite à l&rsquo;initiation / présentation de l&rsquo;Arduino faite hier, il me semblait opportun de publier un post synthétisant ce qui a été dit. Vous trouverez également des liens / ressources références.

**I &#8211; Arduino &#8211; la carte**

[<img class="alignnone size-full wp-image-46" title="arduino_uno_test" src="http://www.labx.fr/wp-content/uploads/2011/06/arduino_uno_test.jpg" alt="" width="410" height="410" />][1]

Donc voici l&rsquo;Arduino.

L&rsquo;Arduino est un microcontroleur (un élément de commande) programmable. Elle a été pensée pour faciliter l&rsquo;usage de l&rsquo;électronique. Avec elle, on peut arriver très rapidement à réaliser des circuits et de commande sans avoir une connaissance poussée de l&rsquo;électronique.

LES DIFFÉRRENTS MODÈLES

Selon les usages, il y a plusieurs types d&rsquo;Arduino.

<!--more-->

• Arduino Uno (remplace les anciens modèles Duomilanove et Diecemilla) : c&rsquo;est la carte de base, celle qui est en photo ci-dessus, celle que je conseille aux débutants. La puce centrale est une ATMega 328. Le &laquo;&nbsp;328&nbsp;&raquo; indique sa mémoire.

<img class="alignnone" src="http://arduino.cc/en/uploads/Main/ArduinoMega.jpg" alt="" width="480" height="250" />

• Arduino Mega : c&rsquo;est la carte de base avec plus de mémoire. La puce centrale est une ATMega 1280. Elle possède plus d&rsquo;entrées / sorties (54). Et plus chère.

<img class="alignnone" src="http://arduino.cc/en/uploads/Main/ArduinoMega2650Front.jpg" alt="" width="509" height="284" />

• Arduino Mega 2650 : La puce centrale est donc une ATMega 2650.

<img class="alignnone" src="http://arduino.cc/en/uploads/Main/arduino_mini.jpg" alt="" width="400" height="299" />

• Arduino Nano / Arduino Mini : pour les projets aboutis, à construire. Sa taille permet de l&rsquo;implanter plus facilment dans un objet. Je le déconseille pour le prototypage / essai : le câblage s&rsquo;en trouve énormément compliqué.

<img class="alignnone" src="http://arduino.cc/en/uploads/Main/ArduinoBT400.jpg" alt="" width="400" height="300" />

• Arduino BT : BT pour BlueTooth. Permet à l&rsquo;Arduino de communiquer sans fil. Plus chère que l&rsquo;Arduino de base mais peut se révéler très pratique à la longue. Ça évite d&rsquo;occuper des entrées/sorties avec un module annexe.

<img class="alignnone" src="http://arduino.cc/en/uploads/Main/LilyPad_3.jpg" alt="" width="250" height="250" />

• Lylipad Arduino : conçu pour la mode interactive. Sa taille et son ergonomie sont pensées pour être facilement cousue sur du textile.

<img class="alignnone" src="http://arduino.cc/en/uploads/Main/fio_pin_headers.jpg" alt="" width="209" height="300" />

• Arduino Fio : pour les utilisateurs avancés. Cet Arduino est programmable sans passer par le logiciel Arduino dédié.

<img class="alignnone" src="http://arduino.cc/en/uploads/Main/ArduinoPro.jpg" alt="" width="426" height="448" />

• Arduino Pro : pour les utilisateurs avancés. Carte Arduino avec le minimum de composants installés. Carte moins chère, donc, mais moins intuitive.

LES SHIELDS

Les shields sont des cartes électroniques qui se branchent directement les entrées/sorties de l&rsquo;Arduino sur l&rsquo;Arduino. Ce sont des modules possédant des fonctions spécifiques. Ils simplifient considérablement la programmation, le cablage, l&rsquo;ergonomie et la fabrication. On peut trouver une liste complète à cette adresse : <http://shieldlist.org/>.

Quelques exemples :

<img class="alignnone" src="http://shieldlist.org/images/143/4d.jpg" alt="" width="320" height="283" />

• 4D Systems 4Display Shield 128 : un shield facilitant le cablage d&rsquo;un écran LCD

&nbsp;

<img class="alignnone" src="http://shieldlist.org/images/7/xport.jpg" alt="" width="320" height="280" />

• Adafruit Industries Ethernet Shield : pour brancher l&rsquo;Arduino sur un réseau ethernet

&nbsp;

<img class="alignnone" src="http://shieldlist.org/images/11/gps.jpg" alt="" width="320" height="236" />

• Adafruit Industries GPS Shield : pour les applications GPS

## 

## <img class="alignnone" src="http://shieldlist.org/images/515/gameduino.jpg" alt="" width="320" height="237" />

• Excamera Labs Gameduino Shield : pour faire tourner des jeux 8-bits à partir de l&rsquo;Arduino. Possède une sortie VGA.

&nbsp;

&nbsp;

**II &#8211; Arduino &#8211; le logiciel**

**<img class="alignnone" src="http://arduino.cc/en/uploads/Guide/Arduino0018Blink.png" alt="" width="573" height="716" />
  
** 

La carte Arduino fonctionne avec un logiciel dédié qui facilite le transfert de programme vers sa ROM. Il est téléchargeable à [cette adresse][2].

INSTALLATION

L&rsquo;installation se passe en 2 temps. La première est l&rsquo;installation du driver de la carte, la deuxième, l&rsquo;installation du logiciel à proprement parler. Un redémarrage de l&rsquo;ordinateur est nécessaire.

<p style="padding-left: 30px;">
  <a href="http://arduino.cc/en/Guide/MacOSX">Pour les Mac</a>
</p>

<p style="padding-left: 30px;">
  <a href="http://arduino.cc/en/Guide/Windows">Pour Windows</a>
</p>

<p style="padding-left: 30px;">
  <a href="http://www.arduino.cc/playground/Learning/Linux">Pour Linux</a>
</p>

&nbsp;

**III &#8211; Montage &#8211; Exemples simples**

COMMANDER UNE SORTIE ARDUINO : _blinking led_

La _Blinking Led_ est le _Hello World_ de l&rsquo;Arduino. Commençons donc par cet exemple. Cet exemple se retrouve de manière plus détaillée [ici][3], en anglais.

Le code (à copier/coller dans le logiciel) :

    /* Blink Turns on an LED on for one second, then off for one second, repeatedly. This example code is in the public domain. */ void setup() { // initialize the digital pin as an output. // Pin 13 has an LED connected on most Arduino boards: pinMode(13, OUTPUT); } void loop() { digitalWrite(13, HIGH);   // set the LED on delay(1000);              // wait for a second digitalWrite(13, LOW);    // set the LED off delay(1000);              // wait for a second }

Le cablage :

<img class="alignnone" src="http://arduino.cc/en/uploads/Tutorial/ExampleCircuit_bb.png" alt="" width="473" height="498" />

COMMANDER UNE SORTIE ARDUINO PAR UNE DE SES ENTRÉES : _blinking led commandée par potentiomètre_

Plus de détails [ici][4].

Le code :

    /* Analog Input Demonstrates analog input by reading an analog sensor on analog pin 0 and turning on and off a light emitting diode(LED) connected to digital pin 13. The amount of time the LED will be on and off depends on the value obtained by analogRead(). The circuit: * Potentiometer attached to analog input 0 * center pin of the potentiometer to the analog pin * one side pin (either one) to ground * the other side pin to +5V * LED anode (long leg) attached to digital output 13 * LED cathode (short leg) attached to ground * Note: because most Arduinos have a built-in LED attached to pin 13 on the board, the LED is optional. Created by David Cuartielles Modified 4 Sep 2010 By Tom Igoe This example code is in the public domain. http://arduino.cc/en/Tutorial/AnalogInput */ int sensorPin = A0; // select the input pin for the potentiometer int ledPin = 13; // select the pin for the LED int sensorValue = 0; // variable to store the value coming from the sensor void setup() { // declare the ledPin as an OUTPUT: pinMode(ledPin, OUTPUT); } void loop() { // read the value from the sensor: sensorValue = analogRead(sensorPin); // turn the ledPin on digitalWrite(ledPin, HIGH); // stop the program for milliseconds: delay(sensorValue); // turn the ledPin off: digitalWrite(ledPin, LOW); // stop the program for for milliseconds: delay(sensorValue); } 

Le cablage (le cablage de la led est le même que le précédent) :

<img class="alignnone" src="http://arduino.cc/en/uploads/Tutorial/graph-circuit3.png" alt="" width="594" height="537" />

Je vous invite à essayer les différents exemples du [site Arduino][5] (rubrique _Learning_). Ils constituent d&rsquo;excellents points de départ.

**IV &#8211; Quelques réalisations (pour donner des idées)**

ARDUINO + WIIMOTE

<http://www.youtube.com/watch?v=DjC2Y9suWSI>

<http://www.youtube.com/watch?v=UK5YHQJR26k&feature=related>

DRONE

<http://diydrones.com/profiles/blogs/aeroquadan-arduinopowered> (pour le fabriquer : [www.aeroquadstore.com][6])

**V &#8211;  Ressources**

<span style="color: #000000;">LIVRES / MAGAZINES</span>

<img class="alignnone" src="http://makezine.com/images/covers/26.gif" alt="" width="148" height="204" />

**[Make Magazine][7]** : le magazine pour le Do it Yourself éléctronique / Hack. Le n°25 est consacré à l&rsquo;Arduino.

**[Blog Make][8]** : le blog attaché à Makezine. Plein d&rsquo;idées et de tuyaux.

<img class="alignnone" src="http://covers.oreilly.com/images/9780596510510/cat.gif" alt="" width="180" height="219" />

**Making Things Talk** : LA bible des projets sérieux à base d&rsquo;Arduino. Très pédagogique, très didactique, de nombreuses annexes pour expliquer les protocoles, bref, à mes yeux : incontournable.

-> [le site du livre][9] où on retrouve les codes et les erratum du livre (quelques erreurs existent dans le livre selon l&rsquo;édition)

-> [Amazon][10]

<img class="alignnone" src="http://blog.makezine.com/wp-content/uploads/2011/05/0636920010371-2.jpg" alt="Amazon : http://www.amazon.com/Make-Embedded-Projects-Hardware-Discovery/dp/1449389716/ref=sr_1_1?ie=UTF8&s=books&qid=1306930851&sr=8-1" width="207" height="252" />

**Arduino : bots and gadgets** : pour construire des robots à base d&rsquo;Arduino

-> [Amazon][11]

<img class="alignnone" src="http://covers.oreilly.com/images/9780596153755/cat.gif" alt="" width="180" height="219" />

**Make : electronics (learning by discovery)** : pour les débutants en électronique (et pour ceux qui veulent se rafraichir la mémoire) : bien illustré et clair.

-> [Amazon][12]

<img class="alignnone" src="http://covers.oreilly.com/images/9780596802486/cat.gif" alt="" width="180" height="236" />

**Arduino Cookbook** : très bon guide avec des exemples intéressants basiques mais qui peuvent se customiser et répondre à pas mal de besoins.

-> [Amazon][13]

<img class="alignnone" src="http://www.practicalarduino.com/sitebuilder/buy/knowledge/asset/medium/1/practical-arduino-cover-small.jpg" alt="" width="181" height="240" />

**Practical Arduino** : Un bon exemple de _speech synthetizer_ dans ce livre.

-> [le site du livre][14]

-> [Amazon][15]

<img class="alignnone" src="http://covers.oreilly.com/images/9780596807740/cat.gif" alt="" width="180" height="236" />

**Building Wireless Sensor Networks Processing** : comme son titre l&rsquo;indique, pour les solutions sans fil.

-> [Amazon][16]

&nbsp;

SITES INTERNET

**[Arduino.cc][17]** : site de référence de l&rsquo;Arduino. Impossible de ne pas y passer.

**[Youtube][18]** : on peut trouver des video didactiques claires. En constante évolution.

**[Vimeo][19]** : les video sont plus propres et pointues sur Vimeo.

**[Github][20]** : site collaboratif de partage de code

**[Google Code][21]** : site collaboratif de partage de code

• Acheter arduino

**[Arduino.cc][22]** : le site recense les revendeurs par pays et continent. Le Snootlab de Toulouse en vend, contrairement à ce que j&rsquo;avais dit.

**[Ebay][23]** : on peut y trouver les vieux modèles (et mêmes les nouveaux) à moins cher.

• Logiciels :

**[Fritzing][24]** : logiciel intuitif pour dessiner les cablages / montages avec l&rsquo;Arduino

**[Arduino][2]**

• Commande matériel électronique

**[Pour faire suite à l&rsquo;initiation / présentation de l&rsquo;Arduino faite hier, il me semblait opportun de publier un post synthétisant ce qui a été dit. Vous trouverez également des liens / ressources références.

**I &#8211; Arduino &#8211; la carte**

[<img class="alignnone size-full wp-image-46" title="arduino_uno_test" src="http://www.labx.fr/wp-content/uploads/2011/06/arduino_uno_test.jpg" alt="" width="410" height="410" />][1]

Donc voici l&rsquo;Arduino.

L&rsquo;Arduino est un microcontroleur (un élément de commande) programmable. Elle a été pensée pour faciliter l&rsquo;usage de l&rsquo;électronique. Avec elle, on peut arriver très rapidement à réaliser des circuits et de commande sans avoir une connaissance poussée de l&rsquo;électronique.

LES DIFFÉRRENTS MODÈLES

Selon les usages, il y a plusieurs types d&rsquo;Arduino.

<!--more-->

• Arduino Uno (remplace les anciens modèles Duomilanove et Diecemilla) : c&rsquo;est la carte de base, celle qui est en photo ci-dessus, celle que je conseille aux débutants. La puce centrale est une ATMega 328. Le &laquo;&nbsp;328&nbsp;&raquo; indique sa mémoire.

<img class="alignnone" src="http://arduino.cc/en/uploads/Main/ArduinoMega.jpg" alt="" width="480" height="250" />

• Arduino Mega : c&rsquo;est la carte de base avec plus de mémoire. La puce centrale est une ATMega 1280. Elle possède plus d&rsquo;entrées / sorties (54). Et plus chère.

<img class="alignnone" src="http://arduino.cc/en/uploads/Main/ArduinoMega2650Front.jpg" alt="" width="509" height="284" />

• Arduino Mega 2650 : La puce centrale est donc une ATMega 2650.

<img class="alignnone" src="http://arduino.cc/en/uploads/Main/arduino_mini.jpg" alt="" width="400" height="299" />

• Arduino Nano / Arduino Mini : pour les projets aboutis, à construire. Sa taille permet de l&rsquo;implanter plus facilment dans un objet. Je le déconseille pour le prototypage / essai : le câblage s&rsquo;en trouve énormément compliqué.

<img class="alignnone" src="http://arduino.cc/en/uploads/Main/ArduinoBT400.jpg" alt="" width="400" height="300" />

• Arduino BT : BT pour BlueTooth. Permet à l&rsquo;Arduino de communiquer sans fil. Plus chère que l&rsquo;Arduino de base mais peut se révéler très pratique à la longue. Ça évite d&rsquo;occuper des entrées/sorties avec un module annexe.

<img class="alignnone" src="http://arduino.cc/en/uploads/Main/LilyPad_3.jpg" alt="" width="250" height="250" />

• Lylipad Arduino : conçu pour la mode interactive. Sa taille et son ergonomie sont pensées pour être facilement cousue sur du textile.

<img class="alignnone" src="http://arduino.cc/en/uploads/Main/fio_pin_headers.jpg" alt="" width="209" height="300" />

• Arduino Fio : pour les utilisateurs avancés. Cet Arduino est programmable sans passer par le logiciel Arduino dédié.

<img class="alignnone" src="http://arduino.cc/en/uploads/Main/ArduinoPro.jpg" alt="" width="426" height="448" />

• Arduino Pro : pour les utilisateurs avancés. Carte Arduino avec le minimum de composants installés. Carte moins chère, donc, mais moins intuitive.

LES SHIELDS

Les shields sont des cartes électroniques qui se branchent directement les entrées/sorties de l&rsquo;Arduino sur l&rsquo;Arduino. Ce sont des modules possédant des fonctions spécifiques. Ils simplifient considérablement la programmation, le cablage, l&rsquo;ergonomie et la fabrication. On peut trouver une liste complète à cette adresse : <http://shieldlist.org/>.

Quelques exemples :

<img class="alignnone" src="http://shieldlist.org/images/143/4d.jpg" alt="" width="320" height="283" />

• 4D Systems 4Display Shield 128 : un shield facilitant le cablage d&rsquo;un écran LCD

&nbsp;

<img class="alignnone" src="http://shieldlist.org/images/7/xport.jpg" alt="" width="320" height="280" />

• Adafruit Industries Ethernet Shield : pour brancher l&rsquo;Arduino sur un réseau ethernet

&nbsp;

<img class="alignnone" src="http://shieldlist.org/images/11/gps.jpg" alt="" width="320" height="236" />

• Adafruit Industries GPS Shield : pour les applications GPS

## 

## <img class="alignnone" src="http://shieldlist.org/images/515/gameduino.jpg" alt="" width="320" height="237" />

• Excamera Labs Gameduino Shield : pour faire tourner des jeux 8-bits à partir de l&rsquo;Arduino. Possède une sortie VGA.

&nbsp;

&nbsp;

**II &#8211; Arduino &#8211; le logiciel**

**<img class="alignnone" src="http://arduino.cc/en/uploads/Guide/Arduino0018Blink.png" alt="" width="573" height="716" />
  
** 

La carte Arduino fonctionne avec un logiciel dédié qui facilite le transfert de programme vers sa ROM. Il est téléchargeable à [cette adresse][2].

INSTALLATION

L&rsquo;installation se passe en 2 temps. La première est l&rsquo;installation du driver de la carte, la deuxième, l&rsquo;installation du logiciel à proprement parler. Un redémarrage de l&rsquo;ordinateur est nécessaire.

<p style="padding-left: 30px;">
  <a href="http://arduino.cc/en/Guide/MacOSX">Pour les Mac</a>
</p>

<p style="padding-left: 30px;">
  <a href="http://arduino.cc/en/Guide/Windows">Pour Windows</a>
</p>

<p style="padding-left: 30px;">
  <a href="http://www.arduino.cc/playground/Learning/Linux">Pour Linux</a>
</p>

&nbsp;

**III &#8211; Montage &#8211; Exemples simples**

COMMANDER UNE SORTIE ARDUINO : _blinking led_

La _Blinking Led_ est le _Hello World_ de l&rsquo;Arduino. Commençons donc par cet exemple. Cet exemple se retrouve de manière plus détaillée [ici][3], en anglais.

Le code (à copier/coller dans le logiciel) :

    /* Blink Turns on an LED on for one second, then off for one second, repeatedly. This example code is in the public domain. */ void setup() { // initialize the digital pin as an output. // Pin 13 has an LED connected on most Arduino boards: pinMode(13, OUTPUT); } void loop() { digitalWrite(13, HIGH);   // set the LED on delay(1000);              // wait for a second digitalWrite(13, LOW);    // set the LED off delay(1000);              // wait for a second }

Le cablage :

<img class="alignnone" src="http://arduino.cc/en/uploads/Tutorial/ExampleCircuit_bb.png" alt="" width="473" height="498" />

COMMANDER UNE SORTIE ARDUINO PAR UNE DE SES ENTRÉES : _blinking led commandée par potentiomètre_

Plus de détails [ici][4].

Le code :

    /* Analog Input Demonstrates analog input by reading an analog sensor on analog pin 0 and turning on and off a light emitting diode(LED) connected to digital pin 13. The amount of time the LED will be on and off depends on the value obtained by analogRead(). The circuit: * Potentiometer attached to analog input 0 * center pin of the potentiometer to the analog pin * one side pin (either one) to ground * the other side pin to +5V * LED anode (long leg) attached to digital output 13 * LED cathode (short leg) attached to ground * Note: because most Arduinos have a built-in LED attached to pin 13 on the board, the LED is optional. Created by David Cuartielles Modified 4 Sep 2010 By Tom Igoe This example code is in the public domain. http://arduino.cc/en/Tutorial/AnalogInput */ int sensorPin = A0; // select the input pin for the potentiometer int ledPin = 13; // select the pin for the LED int sensorValue = 0; // variable to store the value coming from the sensor void setup() { // declare the ledPin as an OUTPUT: pinMode(ledPin, OUTPUT); } void loop() { // read the value from the sensor: sensorValue = analogRead(sensorPin); // turn the ledPin on digitalWrite(ledPin, HIGH); // stop the program for milliseconds: delay(sensorValue); // turn the ledPin off: digitalWrite(ledPin, LOW); // stop the program for for milliseconds: delay(sensorValue); } 

Le cablage (le cablage de la led est le même que le précédent) :

<img class="alignnone" src="http://arduino.cc/en/uploads/Tutorial/graph-circuit3.png" alt="" width="594" height="537" />

Je vous invite à essayer les différents exemples du [site Arduino][5] (rubrique _Learning_). Ils constituent d&rsquo;excellents points de départ.

**IV &#8211; Quelques réalisations (pour donner des idées)**

ARDUINO + WIIMOTE

<http://www.youtube.com/watch?v=DjC2Y9suWSI>

<http://www.youtube.com/watch?v=UK5YHQJR26k&feature=related>

DRONE

<http://diydrones.com/profiles/blogs/aeroquadan-arduinopowered> (pour le fabriquer : [www.aeroquadstore.com][6])

**V &#8211;  Ressources**

<span style="color: #000000;">LIVRES / MAGAZINES</span>

<img class="alignnone" src="http://makezine.com/images/covers/26.gif" alt="" width="148" height="204" />

**[Make Magazine][7]** : le magazine pour le Do it Yourself éléctronique / Hack. Le n°25 est consacré à l&rsquo;Arduino.

**[Blog Make][8]** : le blog attaché à Makezine. Plein d&rsquo;idées et de tuyaux.

<img class="alignnone" src="http://covers.oreilly.com/images/9780596510510/cat.gif" alt="" width="180" height="219" />

**Making Things Talk** : LA bible des projets sérieux à base d&rsquo;Arduino. Très pédagogique, très didactique, de nombreuses annexes pour expliquer les protocoles, bref, à mes yeux : incontournable.

-> [le site du livre][9] où on retrouve les codes et les erratum du livre (quelques erreurs existent dans le livre selon l&rsquo;édition)

-> [Amazon][10]

<img class="alignnone" src="http://blog.makezine.com/wp-content/uploads/2011/05/0636920010371-2.jpg" alt="Amazon : http://www.amazon.com/Make-Embedded-Projects-Hardware-Discovery/dp/1449389716/ref=sr_1_1?ie=UTF8&s=books&qid=1306930851&sr=8-1" width="207" height="252" />

**Arduino : bots and gadgets** : pour construire des robots à base d&rsquo;Arduino

-> [Amazon][11]

<img class="alignnone" src="http://covers.oreilly.com/images/9780596153755/cat.gif" alt="" width="180" height="219" />

**Make : electronics (learning by discovery)** : pour les débutants en électronique (et pour ceux qui veulent se rafraichir la mémoire) : bien illustré et clair.

-> [Amazon][12]

<img class="alignnone" src="http://covers.oreilly.com/images/9780596802486/cat.gif" alt="" width="180" height="236" />

**Arduino Cookbook** : très bon guide avec des exemples intéressants basiques mais qui peuvent se customiser et répondre à pas mal de besoins.

-> [Amazon][13]

<img class="alignnone" src="http://www.practicalarduino.com/sitebuilder/buy/knowledge/asset/medium/1/practical-arduino-cover-small.jpg" alt="" width="181" height="240" />

**Practical Arduino** : Un bon exemple de _speech synthetizer_ dans ce livre.

-> [le site du livre][14]

-> [Amazon][15]

<img class="alignnone" src="http://covers.oreilly.com/images/9780596807740/cat.gif" alt="" width="180" height="236" />

**Building Wireless Sensor Networks Processing** : comme son titre l&rsquo;indique, pour les solutions sans fil.

-> [Amazon][16]

&nbsp;

SITES INTERNET

**[Arduino.cc][17]** : site de référence de l&rsquo;Arduino. Impossible de ne pas y passer.

**[Youtube][18]** : on peut trouver des video didactiques claires. En constante évolution.

**[Vimeo][19]** : les video sont plus propres et pointues sur Vimeo.

**[Github][20]** : site collaboratif de partage de code

**[Google Code][21]** : site collaboratif de partage de code

• Acheter arduino

**[Arduino.cc][22]** : le site recense les revendeurs par pays et continent. Le Snootlab de Toulouse en vend, contrairement à ce que j&rsquo;avais dit.

**[Ebay][23]** : on peut y trouver les vieux modèles (et mêmes les nouveaux) à moins cher.

• Logiciels :

**[Fritzing][24]** : logiciel intuitif pour dessiner les cablages / montages avec l&rsquo;Arduino

**[Arduino][2]**

• Commande matériel électronique

**][25]** : le premier site de vente à s&rsquo;être intéressé à l&rsquo;Arduino aux États Unis. bonne rubrique de tutoriaux.

**[Sparkfun][26]** :LE site où on trouve tout ce qu&rsquo;on veut, à pas (très) cher. Très didactique, très complet.

**[Snootlab][27]** : Spécialisés en shield pour Arduino. Leur volonté est de faire un sparkfun à la française. Je les ai rencontrés, très motivés, disponibles et passionnés.

Pour les commandes électroniques de composants de base :

**[Conrad][28]** : le plus grand public des sites de vente en ligne de composants électroniques.

**[Radiospares][29]** : cher, mais pro.

**[Ebay][30]** : très bon moyen d&rsquo;acheter par lots. Certains composants exotiques se trouvent facilement sur ebay en achetant direct à Hong Kong auprès des fabricants, et donc prix réduits.

 [1]: http://www.labx.fr/wp-content/uploads/2011/06/arduino_uno_test.jpg
 [2]: http://arduino.cc/en/Main/Software
 [3]: http://arduino.cc/en/Tutorial/Blink
 [4]: http://arduino.cc/en/Tutorial/AnalogInput
 [5]: http://arduino.cc/en/Tutorial/HomePage
 [6]: https://www.aeroquadstore.com/?main_page=product_info&cPath=2&products_id=19&zenid=h7askaj33ds4tkd1u7r111bo60
 [7]: http://makezine.com/
 [8]: http://blog.makezine.com
 [9]: http://www.makingthingstalk.com/
 [10]: http://www.amazon.com/Making-Things-Talk-Practical-Connecting/dp/0596510519/ref=sr_1_1?ie=UTF8&qid=1306931358&sr=8-1
 [11]: http://www.amazon.com/Make-Embedded-Projects-Hardware-Discovery/dp/1449389716/ref=sr_1_1?ie=UTF8&s=books&qid=1306930851&sr=8-1
 [12]: http://www.amazon.com/Make-Electronics-Discovery-Charles-Platt/dp/0596153740/ref=pd_bxgy_b_img_b
 [13]: http://www.amazon.com/Arduino-Cookbook-Michael-Margolis/dp/0596802471/ref=pd_bxgy_b_img_b
 [14]: http://www.practicalarduino.com/
 [15]: http://www.amazon.com/Practical-Arduino-Projects-Hardware-Technology/dp/1430224770/ref=sr_1_1?ie=UTF8&qid=1307027614&sr=8-1
 [16]: http://www.amazon.com/Building-Wireless-Sensor-Networks-Processing/dp/0596807732/ref=pd_sim_b_5
 [17]: http://www.arduino.cc
 [18]: http://www.youtube.com
 [19]: http://www.vimeo.com
 [20]: https://github.com/
 [21]: http://code.google.com/hosting/
 [22]: http://arduino.cc/en/Main/Buy
 [23]: http://shop.ebay.com/i.html?_trkparms=65%253A12%257C66%253A2%257C39%253A1%257C72%253A4730&rt=nc&_nkw=arduino&_trksid=p3286.c0.m14.l1513&_pgn=4
 [24]: http://fritzing.org/
 [25]: http://www.adafruit.com
 [26]: http://www.sparkfun.com/
 [27]: http://shop.snootlab.com/
 [28]: http://www.conrad.fr/
 [29]: http://radiospares-fr.rs-online.com/web/
 [30]: http://www.ebay.com/

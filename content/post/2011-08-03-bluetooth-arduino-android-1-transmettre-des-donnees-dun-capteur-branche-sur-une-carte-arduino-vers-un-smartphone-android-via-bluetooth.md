---
title: 'Bluetooth + Arduino + Android – 1 : Transmettre des données d’un capteur branché sur une carte Arduino vers un Smartphone Android via bluetooth'
author: Julien D.
layout: post
date: 2011-08-03
Miles Walked:
  - 10-19
Temper Level:
  - Low
Favorite Fruits:
  - orange
  - grape
categories:
  - Non classé
---
[Arduino + Bluetooth + Android][1] from [Labx Hacklab][2] on [Vimeo][3].

Le but de cet exemple est de faire tourner un carré sur l&rsquo;écran du smartphone android grâce à un potentiomètre (ou tout autre capteur analogique relié à la borne A0 de la carte Arduino).

Ce montage et code est testé avec :
  
_Matériel :_
  
 _Arduino Diecemila avec un ATMega 328_
  
 _Module Bluetooth BlueSmirf Silver_
  
 _Cable USB_

Configuration utilisée :
  
_Mac OSX 10.6.8_
  
 _Logiciel Arduino v.0022_
  
 _Logiciel Processing v.1.5.1_
  
 _HTC Desire Android 2.2_

Pré-requis :

<!--more-->

_Relier une carte Arduino à un ordinateur_
  
 _Charger du code sur une carte Arduino_
  
 _Connaitre l&rsquo;adresse Mac pour le Bluetooth du BlueSmirf_
  
 _Connaissance du logiciel Processing_
  
 _Logiciel Processing installé_
  
 _Avoir télécharger le dernier SDK Android ([voir le wiki processing/android][4])_

**I &#8211; Le schéma de travail**

<a href="http://www.labx.fr/?attachment_id=150" rel="attachment wp-att-150"><img class="size-full wp-image-150 aligncenter" title="schéma" src="http://www.labx.fr/wp-content/uploads/2011/08/schéma1.jpg" alt="" width="605" height="559" /></a>

Nous allons utiliser le logiciel Processing pour créer une appli android qui permettra de communiquer via bluetooth avec une carte Arduino via le module bluetooth bluesmirf.

&nbsp;

**Étape 1 &#8211; Créer une application Android avec le logiciel Processing**

1 &#8211; Télécharger la bibliothèque sweetBT <https://github.com/1scale1/sweetbt/zipball/master> et l&rsquo;installer dans processing (copier le dossier &laquo;&nbsp;sweetbt_processing&nbsp;&raquo; dans le dossier &laquo;&nbsp;libraires&nbsp;&raquo; de processing)

2 &#8211; Ouvrir l&rsquo;exemple &laquo;&nbsp;analogRead&nbsp;&raquo;. Voici le code :

<pre><span style="color: #666666;">/** </span>
<span style="color: #666666;"> * SweetBlue - Analog Read</span>
<span style="color: #666666;"> * by Andreas Göransson. </span>
<span style="color: #666666;"> * </span>
<span style="color: #666666;"> * This sketch connects to ArduinoBT and rotates a rectangle on the</span>
<span style="color: #666666;"> * processing sketch depending on the value read from an analog</span>
<span style="color: #666666;"> * sensor on the ArduinoBT. Rotation is between 0 and 45 degrees.</span>
<span style="color: #666666;"> * </span>
<span style="color: #666666;"> * Note: Make sure to enable the BLUETOOTH and BLUETOOTH_ADMIN Sketch</span>
<span style="color: #666666;"> * Permissions.</span>
<span style="color: #666666;"> */</span>

<span style="color: #627516;">import</span> se.onescaleone.sweetblue.*;

<span style="color: #666666;">/* Library obj. */</span>
SweetBlue bt;

<span style="color: #666666;">/* Related to the communication */</span>
<span style="color: #627516;">boolean</span> initiated = <span style="color: #627516;">false</span>;
<span style="color: #627516;">long</span> timer = 0;
<span style="color: #627516;">long</span> timerdelay = 100; <span style="color: #666666;">// minimum amount of milliseconds between each reading</span>

<span style="color: #666666;">/* Pin where the sensor is connected */</span>
<span style="color: #627516;">int</span> PIN = 0;

<span style="color: #666666;">/* Variable to store read-values in (it has to be int array!) */</span>
<span style="color: #627516;">int</span>[] val = <span style="color: #627516;">new</span> <span style="color: #627516;">int</span>[1];

<span style="color: #627516;">void</span> <span style="color: #627516;"><strong>setup</strong></span>() {
  <span style="color: #666666;">/* Connect to the ArduinoBT */</span>
  <span style="color: #627516;">if</span> ( bt == <span style="color: #627516;">null</span> ) {
    bt = <span style="color: #627516;">new</span> SweetBlue( <span style="color: #627516;">this</span> );
    bt.connect(<span style="color: #336598;">"/*mettre l'adresse mac du bluetooth arduino*/"</span>);
  }

  <span style="color: #666666;">/* Lock PORTRAIT view */</span>
  orientation( PORTRAIT );

  <span style="color: #666666;">/* Simplifies position and rotation */</span>
  <span style="color: #627516;">rectMode</span>( <span style="color: #336598;">CENTER</span> );

  <span style="color: #666666;">/* Enable debug messages? */</span>
  <span style="color: #666666;">//SweetBlue.DEBUG = true;</span>

  timer = <span style="color: #627516;">millis</span>();
}

<span style="color: #627516;">void</span> <span style="color: #627516;"><strong>draw</strong></span>() {
  <span style="color: #627516;">if</span> ( bt.isConnected() && !initiated ) {
    <span style="color: #666666;">/* Once the board has established a connection, set the pin modes... */</span>
    bt.pinMode( PIN, SweetBlue.INPUT );
    <span style="color: #666666;">/* ...but only do it once! */</span>
    initiated = <span style="color: #627516;">true</span>;
  }

  <span style="color: #666666;">/* Draw background */</span>
  <span style="color: #627516;">background</span>( 126 );

  <span style="color: #666666;">/* Draw interface */</span>
  <span style="color: #627516;">pushMatrix</span>();
    <span style="color: #627516;">translate</span>( <span style="color: #336598;">screenWidth</span>/2, <span style="color: #336598;">screenHeight</span>/2 );
    <span style="color: #627516;">rotate</span>( <span style="color: #627516;">map</span>(val[0], 0, 1023, <span style="color: #336598;">HALF_PI</span> / 2, 0) );
    <span style="color: #627516;">fill</span>( 255, 0, 0 );
    <span style="color: #627516;">rect</span>( 0, 0, 400, 400 );
  <span style="color: #627516;">popMatrix</span>();

  <span style="color: #666666;">/* Read value from ArduinoBT every "timerdelay" milliseconds */</span>
  <span style="color: #627516;">if</span> ( bt.isConnected() && (<span style="color: #627516;">millis</span>() - timer &gt;= timerdelay) ) {
    <span style="color: #666666;">/* Read the digital pin, PIN, from the bluetooth board */</span>
    bt.analogRead( PIN, val );
    <span style="color: #666666;">/* Reset the timer */</span>
    timer = <span style="color: #627516;">millis</span>();
  }
}

<span style="color: #666666;">/* When processing stops, send the disconnect command to ArduinoBT */</span>
<span style="color: #627516;">void</span> stop() {
  bt.<span style="color: #627516;">close</span>();
}</pre>

&nbsp;

Intégrer la bibliothèque SweetBT : Menu Skecth> Add File. Choisir le dossier SweetBt / Library.

3- Basculer processing en mode Android. Bouton &laquo;&nbsp;Standard / Android&nbsp;&raquo;. L&rsquo;interface devient verte quand c&rsquo;est ok.

4 &#8211; Dans le code, repérer la ligne &laquo;&nbsp;bt.connect(&nbsp;&raquo; &laquo;&nbsp;);&nbsp;&raquo; (ligne 34 du code). Entre les guillemets, entrer l&rsquo;adresse mac  du module Bluesmirf. Ça ressemble à 01:01:01:01:01:01

5 &#8211; S&rsquo;assurer que les bonnes permissions sont autorisés pour l&rsquo;application android. L&rsquo;application Android, une fois installée sur le téléphone communique avec des capteurs et protocoles, il faut donc donner des autorisations. Pour ce faire : Menu Android > Sketch Permissions. Dans la boîte de dialogue cocher &laquo;&nbsp;BLUETOOTH&nbsp;&raquo; et &laquo;&nbsp;BLUETOOTH_ADMIN&nbsp;&raquo;

5 &#8211; Compiler l&rsquo;appli Android : Menu File > Export Android Project

6 &#8211; Dans le dossier du sketch processing (Menu Sketch > Show Sketch Folder pour le trouver). Dans le dossier android >bin se trouve  &laquo;&nbsp;analogRead-debug.apk&nbsp;&raquo;, soit notre appli android.

&nbsp;

**Installer une appli Android sur son smartphone Android**

1 &#8211; Passer le smartphone en mode debug. Paramètres > Applications > développement > débogage USB (activer)

2 &#8211; Transférer l&rsquo;appli sur le smartphone, l&rsquo;installer et l&rsquo;ouvrir.

3 &#8211; Si tout marche bien, voici ce qui s&rsquo;affiche sur l&rsquo;écran du smartphone :

<a href="http://www.labx.fr/?attachment_id=151" rel="attachment wp-att-151"><img class="alignnone size-full wp-image-151 aligncenter" title="ecran_smartphone" src="http://www.labx.fr/wp-content/uploads/2011/08/ecran_smartphone.gif" alt="" width="120" height="200" /></a>

&nbsp;

4- avant que la carte Arduino et le smartphone puisse dialoguer, il faut les jumeler :

sur le smartphone : Paramètres > Sans Fil et réseaux >Paramètres Bluetooth > Rechercher les périphériques

Quand le smartphone et le bluesmirf sont connectés, la led du bluesmirf passe du rouge au vert.

**Étape 2 &#8211; Le code à charger sur la carte Arduino**

1- télécharger la bibliothèque NewSoftSerial pour Arduino [NewSoftSerial10c.zip][5]. Des explications et exemples plus détaillés concernant cette bibliothèque sur cette page (<http://arduiniana.org/libraries/newsoftserial/>).

2 &#8211; installer cette bibliothèque dans le logiciel Arduino :

• Repérer l&rsquo;emplacement du dossier sketchbook d&rsquo;arduino. Sur Mac, pour savoir où il se trouve : Menu Arduino > Préférences.

• à l&rsquo;intérieur de ce dossier, créer un dossier &laquo;&nbsp;libraires&nbsp;&raquo; s&rsquo;il n&rsquo;existe pas.

• à l&rsquo;intérieur du dossier &laquo;&nbsp;libraires&nbsp;&raquo;, placer le dossier dézippé &laquo;&nbsp;NewSoftSerial&nbsp;&raquo;

• Quitter le logiciel Arduino

• Relancer le logiciel Arduino

3 &#8211; voici le code à transférer sur la carte arduino :

<pre><span style="color: #7e7e7e;">/*</span>
<span style="color: #7e7e7e;"> * Glue protocol for Arduino BT to talk to Android phones</span>
<span style="color: #7e7e7e;"> *</span>
<span style="color: #7e7e7e;"> * this Arduino sketch will make Arduino talk using the so called Glue</span>
<span style="color: #7e7e7e;"> * protocol as designed by 1scale1. This protocol encapsulates data to</span>
<span style="color: #7e7e7e;"> * allow error detection when sending data over the air to another device</span>
<span style="color: #7e7e7e;"> *</span>
<span style="color: #7e7e7e;"> * the protocol has been customized to support the four basic Arduino</span>
<span style="color: #7e7e7e;"> * commands: digitalRead/Write, analogRead/Write</span>
<span style="color: #7e7e7e;"> *</span>
<span style="color: #7e7e7e;"> * this is not designed for power efficiency but for prototyping, therefore</span>
<span style="color: #7e7e7e;"> * the protocol tries to keep the BT connection opened by sending ping</span>
<span style="color: #7e7e7e;"> * over the air to the other device. If there was a series of NACKs to</span>
<span style="color: #7e7e7e;"> * that message, the processor would reset the BT chipset</span>
<span style="color: #7e7e7e;"> *</span>
<span style="color: #7e7e7e;"> * (c) 2011 D. Cuartielles & A. Goransson, 1scale1.com</span>
<span style="color: #7e7e7e;"> *</span>
<span style="color: #7e7e7e;"> * This code is free software and is licensed under GPLv3.0, for more</span>
<span style="color: #7e7e7e;"> * information about this license, please visit:</span>
<span style="color: #7e7e7e;"> * http://www.gnu.org/licenses/gpl-3.0.txt</span>
<span style="color: #7e7e7e;"> *</span>
<span style="color: #7e7e7e;"> */</span>

<span style="color: #7e7e7e;">// LOAD LIBRARIES</span>
#include &lt;<span style="color: #cc6600;">NewSoftSerial</span>.h&gt;
<span style="color: #cc6600;">NewSoftSerial</span> mySerial(2, 4); <span style="color: #7e7e7e;">// these pins aren't used by the tinkerkit</span>
#define SERDEBUG 0

<span style="color: #7e7e7e;">// COMMAND RELATED INFO</span>
<span style="color: #7e7e7e;">// commands for the overall loop</span>
#define VERSION      0x00
#define TEST         0x01
#define GENERIC      0x02
#define ECHO         0x03
#define SYNCH        0x08
#define BT_STOP      0x05

<span style="color: #7e7e7e;">// BT state machine</span>
#define BT_TIMEOUT      5000  <span style="color: #7e7e7e;">// time for BT reset</span>
#define BT_ERROR_MAX    3     <span style="color: #7e7e7e;">// amount of errors to be accounted before BT reset </span>
#define BT_RESET_PIN    7
#define BT_ST_DISCOVERABLE  0
#define BT_ST_RUNNING       1
<span style="color: #cc6600;">byte</span> btErrors = 0;
<span style="color: #cc6600;">unsigned</span> <span style="color: #cc6600;">long</span> timer = 0;
<span style="color: #cc6600;">byte</span> btStatus = BT_ST_DISCOVERABLE;

<span style="color: #7e7e7e;">// Arduino commands</span>
#define PINMODE      0x01
#define DIGITALREAD  0x02
#define DIGITALWRITE 0x03
#define ANALOGREAD   0x04
#define ANALOGWRITE  0x05

<span style="color: #7e7e7e;">// LEDs for debugging purposes</span>
#define O0   3
#define O1   5
#define O2   6
#define O3   9
#define O4   10
#define O5   11

<span style="color: #7e7e7e;">// we define different pins to act as information LED pins depending on the board we use</span>
<span style="color: #cc6600;">int</span> ledPin = O3;
<span style="color: #cc6600;">int</span> gndPin = 0;

<span style="color: #cc6600;">boolean</span> <span style="color: #cc6600;">status</span> = <span style="color: #cc6600;">false</span>;
<span style="color: #cc6600;">boolean</span> blueStatus = <span style="color: #cc6600;">false</span>;

<span style="color: #7e7e7e;">// error message</span>
#define MSG_ERROR        0xFF    <span style="color: #7e7e7e;">// value to report errors back to the phone</span>
#define MSG_SYNCH        0x01    <span style="color: #7e7e7e;">// value to send a synch request command to phones</span>

<span style="color: #cc6600;">byte</span> theData[] = {4, 3, 0};

<span style="color: #cc6600;">void</span> sendByte(<span style="color: #cc6600;">byte</span> data) {
  <span style="color: #cc6600;"><strong>Serial</strong></span>.<span style="color: #cc6600;">print</span>(data, <span style="color: #006699;">BYTE</span>);
<span style="color: #7e7e7e;">//  delayMicroseconds(10);</span>
}

<span style="color: #7e7e7e;">// this function is used when calling to low level commands on the Arduino BT board, considering it will not</span>
<span style="color: #7e7e7e;">// be used in any other way, we need to disable access to pins 0, 1, 7 (RX/TX and BT reset)</span>
<span style="color: #7e7e7e;">// we will always answer back using the format 0xFF 0xFF 0x02 0x04 AA PP XX YY CC, where</span>
<span style="color: #7e7e7e;">// - AA: Arduino command</span>
<span style="color: #7e7e7e;">// - PP: pin number</span>
<span style="color: #7e7e7e;">// - XX: 2 MSb result from a reading, 0xFF if error</span>
<span style="color: #7e7e7e;">// - YY: 8 LSb result from a reading, 0 otherwise</span>
<span style="color: #7e7e7e;">// - CC: checksum</span>
<span style="color: #cc6600;">byte</span> processArduinoCMD(<span style="color: #cc6600;">int</span> length, <span style="color: #cc6600;">byte</span> *Data)
{
  <span style="color: #cc6600;">int</span> val = 0;
  <span style="color: #cc6600;">int</span> reading = 0;
  <span style="color: #cc6600;">int</span> lowB = 0;
  <span style="color: #cc6600;">int</span> highB = 0;

  <span style="color: #cc6600;">if</span>(SERDEBUG) {
    mySerial.<span style="color: #cc6600;">print</span>(<span style="color: #006699;">"Arduino Command sent: "</span>);
    mySerial.<span style="color: #cc6600;">println</span>((<span style="color: #cc6600;">char</span>)Data[0]+48);
    mySerial.<span style="color: #cc6600;">print</span>(<span style="color: #006699;">"Pin: "</span>);
    mySerial.<span style="color: #cc6600;">println</span>((<span style="color: #cc6600;">char</span>)Data[1]+48);
    mySerial.<span style="color: #cc6600;">print</span>(<span style="color: #006699;">"Initial value: "</span>);
    mySerial.<span style="color: #cc6600;">println</span>((<span style="color: #cc6600;">char</span>)Data[2]+48);
  }

  <span style="color: #cc6600;">switch</span> (Data[0]) {
    <span style="color: #7e7e7e;">// pinMode</span>
  <span style="color: #cc6600;">case</span> PINMODE:
    <span style="color: #cc6600;">if</span> (Data[2]) val = <span style="color: #006699;">INPUT</span>;
    <span style="color: #cc6600;">else</span> val = <span style="color: #006699;">OUTPUT</span>;
    <span style="color: #cc6600;">if</span> (Data[1] != 7 && Data[1] != 0 && Data[1] != 1) <span style="color: #cc6600;">pinMode</span>(Data[1], val);
    <span style="color: #cc6600;">else</span> val = 0xFF00;
    <span style="color: #cc6600;">break</span>;

    <span style="color: #7e7e7e;">// digitalRead</span>
  <span style="color: #cc6600;">case</span> DIGITALREAD:
    <span style="color: #cc6600;">if</span> (Data[1] != 7 && Data[1] != 0 && Data[1] != 1) val = <span style="color: #cc6600;">digitalRead</span>(Data[1]);
    <span style="color: #cc6600;">else</span> val = 0xFF00;
    <span style="color: #cc6600;">break</span>;

    <span style="color: #7e7e7e;">// digitalWrite</span>
  <span style="color: #cc6600;">case</span> DIGITALWRITE:
    <span style="color: #cc6600;">if</span> (Data[1] != 7 && Data[1] != 0 && Data[1] != 1) <span style="color: #cc6600;">digitalWrite</span>(Data[1], Data[2]);
    <span style="color: #cc6600;">else</span> val = 0xFF00;
    <span style="color: #cc6600;">break</span>;

    <span style="color: #7e7e7e;">// analogRead</span>
  <span style="color: #cc6600;">case</span> ANALOGREAD:
  <span style="color: #cc6600;">analogReference</span>(<span style="color: #006699;">DEFAULT</span>);
    <span style="color: #cc6600;">if</span> (Data[1] &lt;= 5) {
<span style="color: #7e7e7e;">//  toggleLed();</span>
<span style="color: #7e7e7e;">//XXX analog readings are failing, we don't know why ... this needs to be researched further</span>
      reading = <span style="color: #cc6600;">analogRead</span>(Data[1]);
 mySerial.<span style="color: #cc6600;">println</span>(reading);
      lowB = reading & 0x007F;
      highB = reading &gt;&gt; 7;
      val = highB * 256 + lowB;
    }
    <span style="color: #cc6600;">else</span> val = 0xFF00;
    <span style="color: #cc6600;">break</span>;

    <span style="color: #7e7e7e;">// analogWrite</span>
  <span style="color: #cc6600;">case</span> ANALOGWRITE:
    <span style="color: #cc6600;">if</span> (Data[1] != 7 && Data[1] != 0 && Data[1] != 1) <span style="color: #cc6600;">analogWrite</span>(Data[1], Data[2]);
    <span style="color: #cc6600;">else</span> val = 0xFF00;
    <span style="color: #cc6600;">break</span>;

  }

  <span style="color: #7e7e7e;">// send the information back to the other device</span>
  <span style="color: #7e7e7e;">// the headers</span>
  sendByte(0xFF); sendByte(0xFF); sendByte(GENERIC); sendByte(0x04);
  <span style="color: #7e7e7e;">// the values</span>
  sendByte(Data[0]); sendByte(Data[1]); sendByte((val &gt;&gt; 8) & 0xFF); sendByte(val & 0xFF); 
  <span style="color: #7e7e7e;">// the checksum</span>
  sendByte(Data[0] ^ Data[1] ^ ((val &gt;&gt; 8) & 0xFF) ^ (val & 0xFF) ^ GENERIC ^ 0x04);

  <span style="color: #cc6600;">if</span>(SERDEBUG) {
    mySerial.<span style="color: #cc6600;">print</span>(<span style="color: #006699;">"Result sent: "</span>);
    mySerial.<span style="color: #cc6600;">println</span>(reading);
    mySerial.<span style="color: #cc6600;">print</span>(<span style="color: #006699;">"Result decomposed: "</span>);
    mySerial.<span style="color: #cc6600;">print</span>((val &gt;&gt; 8 ) & 0xFF);
    mySerial.<span style="color: #cc6600;">print</span>(<span style="color: #006699;">" - "</span>);
    mySerial.<span style="color: #cc6600;">println</span>(val & 0xFF);
  }

  <span style="color: #cc6600;">return</span> 0;
}

<span style="color: #cc6600;">void</span> sendSynch() {
  <span style="color: #7e7e7e;">// send synch information back to the other device</span>
  <span style="color: #7e7e7e;">// the headers</span>
  sendByte(0xFF); sendByte(0xFF); sendByte(SYNCH); sendByte(0x04);
  <span style="color: #7e7e7e;">// the values</span>
  sendByte(MSG_SYNCH); sendByte(0); sendByte(0); sendByte(0); 
  <span style="color: #7e7e7e;">// the checksum</span>
  sendByte(MSG_SYNCH ^ SYNCH ^ 0x04);
}

<span style="color: #7e7e7e;">// function to process commands coming from the port</span>
<span style="color: #cc6600;">byte</span> ProcessCommand(<span style="color: #cc6600;">byte</span> *Data)
{
  <span style="color: #cc6600;">byte</span> length = 0;
  <span style="color: #cc6600;">byte</span> checksum = 0;
  <span style="color: #cc6600;">byte</span> Command = 0;

  waitForMessage(); <span style="color: #7e7e7e;">// Receive the header byte: should be 0xFF</span>
  Command = GetByte(); <span style="color: #7e7e7e;">// Receive the command</span>

  <span style="color: #7e7e7e;">// here we are assuming that we are getting the command to take data and push it to the TLCs</span>
  <span style="color: #7e7e7e;">// it is possible to implement other commands with no problem and then we should just discriminate</span>
  <span style="color: #7e7e7e;">// according to their code. Let's say that pushing data to the TLC is command #1 (0x01)</span>

  length = GetByte(); <span style="color: #7e7e7e;">// Receive the amount of data being sent (in this case how many motors to control)</span>

  checksum = length ^ Command;
  <span style="color: #7e7e7e;">// get all the data</span>
  <span style="color: #cc6600;">for</span> (<span style="color: #cc6600;">int</span> i=0; i&lt;length; ++i)
  {
    Data[i] = GetByte();
  }

  <span style="color: #cc6600;">byte</span> recChecksum = GetByte();

  <span style="color: #7e7e7e;">// clean the data from the inversion bit</span>
  <span style="color: #7e7e7e;">// this means to substract 128 to the odd indexes in the </span>
  <span style="color: #7e7e7e;">// data chain and respect the even ones</span>

  <span style="color: #7e7e7e;">// calculate checksum based on received data</span>
  <span style="color: #cc6600;">for</span> (<span style="color: #cc6600;">int</span> i=0; i&lt;length; ++i)
  {
    checksum ^= Data[i];
  }

  <span style="color: #cc6600;">if</span> (checksum != recChecksum)
  {

<span style="color: #7e7e7e;">//    Serial.print(checksum, HEX);</span>

    <span style="color: #cc6600;">return</span> 0; <span style="color: #7e7e7e;">// checksum failure!</span>
  }

  <span style="color: #cc6600;">if</span>(SERDEBUG) {
    mySerial.<span style="color: #cc6600;">print</span>(<span style="color: #006699;">"Command sent: "</span>);
    mySerial.<span style="color: #cc6600;">println</span>((<span style="color: #cc6600;">char</span>)Command+48);
  }

  <span style="color: #cc6600;">switch</span> (Command)
  {
    <span style="color: #cc6600;">case</span> GENERIC:
      processArduinoCMD(length, Data);
      btStatus = BT_ST_RUNNING;
      timer = <span style="color: #cc6600;">millis</span>();
      btErrors = 0;
      <span style="color: #cc6600;">break</span>;

    <span style="color: #cc6600;">case</span> SYNCH:
      timer = <span style="color: #cc6600;">millis</span>();
      btErrors = 0;
      btStatus = BT_ST_RUNNING;
     <span style="color: #cc6600;">break</span>;

    <span style="color: #cc6600;">case</span> BT_STOP:
      timer = <span style="color: #cc6600;">millis</span>();
      btErrors = 0;
      btReset();
      <span style="color: #cc6600;">break</span>;

    <span style="color: #cc6600;">default</span>:
      <span style="color: #cc6600;">break</span>;
  }

  <span style="color: #cc6600;">return</span> 1;
}

<span style="color: #cc6600;">void</span> blinkLed(<span style="color: #cc6600;">int</span> ledPin, <span style="color: #cc6600;">int</span> time)
{
  <span style="color: #cc6600;">digitalWrite</span>(ledPin, <span style="color: #006699;">HIGH</span>);
  <span style="color: #cc6600;">delay</span>(time);
  <span style="color: #cc6600;">digitalWrite</span>(ledPin, <span style="color: #006699;">LOW</span>);
  <span style="color: #cc6600;">delay</span>(time);
}

<span style="color: #cc6600;">void</span> toggleLed()
{
  <span style="color: #cc6600;">digitalWrite</span>(ledPin, <span style="color: #cc6600;">status</span>);
  <span style="color: #cc6600;">status</span> = !<span style="color: #cc6600;">status</span>;
}

<span style="color: #cc6600;">void</span> toggleBlueLed()
{
  <span style="color: #cc6600;">digitalWrite</span>(O2, blueStatus);
  blueStatus = !blueStatus;
}

<span style="color: #cc6600;">byte</span> GetByte() <span style="color: #7e7e7e;">// helper function to read a byte from serial</span>
{
  <span style="color: #cc6600;">while</span> (!<span style="color: #cc6600;"><strong>Serial</strong></span>.<span style="color: #cc6600;">available</span>());
  <span style="color: #cc6600;">byte</span> theByte = <span style="color: #cc6600;"><strong>Serial</strong></span>.<span style="color: #cc6600;">read</span>();

  <span style="color: #cc6600;">return</span> theByte;
}

<span style="color: #cc6600;">byte</span> waitForMessage() <span style="color: #7e7e7e;">// waits until it gets 0xFF from the serial port</span>
{
  <span style="color: #cc6600;">int</span> count = 0;
  <span style="color: #cc6600;">byte</span> serdata = 0;
  <span style="color: #cc6600;">while</span> ( count &lt; 2 )
  {
    serdata = GetByte();
    <span style="color: #7e7e7e;">// increase the counter only if we get the marker 0xFF</span>
    <span style="color: #7e7e7e;">// if we got one marker and then something else, we were in</span>
    <span style="color: #7e7e7e;">// the middle of a string</span>
    <span style="color: #cc6600;">if</span> (serdata == 0xFF) count++;
    <span style="color: #cc6600;">else</span> count = 0;
  }

  <span style="color: #cc6600;">return</span> serdata;
}

<span style="color: #cc6600;">void</span> btReset() {
  <span style="color: #cc6600;">digitalWrite</span>(BT_RESET_PIN, <span style="color: #006699;">HIGH</span>);
  <span style="color: #cc6600;">delay</span>(200);
  <span style="color: #cc6600;">digitalWrite</span>(BT_RESET_PIN, <span style="color: #006699;">LOW</span>);
  btStatus = BT_ST_DISCOVERABLE;
}

<span style="color: #cc6600;">void</span> <span style="color: #cc6600;"><strong>setup</strong></span>() {
  <span style="color: #7e7e7e;">// preconfigure the BT reset pin</span>
  <span style="color: #cc6600;">pinMode</span>(BT_RESET_PIN, <span style="color: #006699;">OUTPUT</span>);
  <span style="color: #cc6600;">digitalWrite</span>(BT_RESET_PIN, <span style="color: #006699;">LOW</span>);

  <span style="color: #cc6600;">pinMode</span>(ledPin, <span style="color: #006699;">OUTPUT</span>);

  <span style="color: #7e7e7e;">// initialize the timer for the state machine</span>
  timer = <span style="color: #cc6600;">millis</span>();

  <span style="color: #cc6600;"><strong>Serial</strong></span>.<span style="color: #cc6600;">begin</span>(115200);

  <span style="color: #cc6600;">if</span>(SERDEBUG) {
    <span style="color: #7e7e7e;">// set the data rate for the NewSoftSerial port</span>
    mySerial.<span style="color: #cc6600;">begin</span>(4800);
    mySerial.<span style="color: #cc6600;">println</span>(<span style="color: #006699;">"Debug Monitor V0.1"</span>);
  }

}

<span style="color: #cc6600;">void</span> <span style="color: #cc6600;"><strong>loop</strong></span>() {
  <span style="color: #7e7e7e;">// check commands if there is data available on Serial</span>
  <span style="color: #cc6600;">if</span> (<span style="color: #cc6600;"><strong>Serial</strong></span>.<span style="color: #cc6600;">available</span>() &gt; 0)
    <span style="color: #cc6600;">if</span> (ProcessCommand(theData)) {
    <span style="color: #7e7e7e;">// toggleBlueLed();</span>
    }

  <span style="color: #7e7e7e;">// decide when to reset based on the amount of timeouts</span>
  <span style="color: #cc6600;">if</span> (btStatus == BT_ST_RUNNING) {
    <span style="color: #cc6600;">if</span> (<span style="color: #cc6600;">millis</span>() - timer &gt;= BT_TIMEOUT) {
      btErrors++;
      <span style="color: #cc6600;">if</span> (btErrors &gt; BT_ERROR_MAX) {
        btReset();
      } <span style="color: #cc6600;">else</span> {
        sendSynch();
        timer = <span style="color: #cc6600;">millis</span>();
      }
    }
  } <span style="color: #cc6600;">else</span> {
    btErrors = 0;
    timer = <span style="color: #cc6600;">millis</span>();
  }
}</pre>

4- Avant que la carte Arduino et le smartphone puissent dialoguer, il faut les jumeler :

sur le smartphone : Paramètres > Sans Fil et réseaux >Paramètres Bluetooth > Rechercher les périphériques

Quand le smartphone et le bluesmirf sont connectés, la led du bluesmirf passe du rouge au vert.

&nbsp;

**Le cablage de l&rsquo;Arduino + BlueSmirf**

Avant de transférer du code vers la carte Arduino, couper l&rsquo;alimentation du blueSmirf (en débranchant le câble la reliant à GND par exemple), sinon le transfert échouera.
  
<a href="http://www.labx.fr/?attachment_id=169" rel="attachment wp-att-169"><img class="aligncenter size-thumbnail wp-image-169" title="sweetBT_Arduino_android_bluetooth_bb" src="http://www.labx.fr/wp-content/uploads/2011/08/sweetBT_Arduino_android_bluetooth_bb-310x150.png" alt="" width="310" height="150" /></a>

 [1]: http://vimeo.com/27245610
 [2]: http://vimeo.com/user7989997
 [3]: http://vimeo.com
 [4]: http://wiki.processing.org/w/Android
 [5]: http://arduiniana.org/NewSoftSerial/NewSoftSerial10c.zip

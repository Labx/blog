---
title: 'Kinect & Processing'
author: Julien D.
layout: post
date: 2012-04-10
categories:
  - Documentation
  - Ressources
---
**Qu&rsquo;est que la Kinect ?
  
** 
  
[<img class="alignnone size-medium wp-image-117002" title="kinect" src="http://docilestudio.fr/ESA/wp-content/uploads/2012/03/kinect-470x293.png" alt="" width="470" height="293" />][1]

[La kinect][2] est un périphérique destiné à la console de jeux vidéo Xbox 360 permettant de contrôler des jeux vidéo sans utiliser de manette.

On peut cependant l&rsquo;utiliser sans la xbox360.

Avantages : la kinect est constituée d&rsquo;un ensemble de capteurs (capteur de distance, de profondeur, une webcam classique, une webcam infra-rouge pour detecter dans le noir, detection de squelette(s) ) qui sont moins onéreux est plus rapides à mettre en place qu&rsquo;en réalisant un protoype electronique DIY.

<!--more-->

Elle nécessite une alimentation secteur et se branche sur l&rsquo;ordinateur par prise USB.

<div id="attachment_123238" style="width: 480px" class="wp-caption alignnone">
  <a href="http://docilestudio.fr/ESA/wp-content/uploads/2012/03/Kinect-face.png"><img class="size-medium wp-image-123238" title="Kinect-face" src="http://docilestudio.fr/ESA/wp-content/uploads/2012/03/Kinect-face-470x318.png" alt="" width="470" height="318" /></a>
  
  <p class="wp-caption-text">
    Détails et emplacements des différents capteurs de la Kinect
  </p>
</div>

Caractéristiques techniques :

<ol style="padding-left: 30px;">
  <li>
    Capteur : <ol>
      <li>
        Lentilles détectant la couleur et la profondeur
      </li>
      <li>
        Micro à reconnaissance vocale
      </li>
      <li>
        Capteur motorisé pour suivre les déplacements
      </li>
    </ol>
  </li>
  
  <li>
    Champ de vision : <ol>
      <li>
        Champ de vision horizontal : 57 degrés
      </li>
      <li>
        Champ de vision vertical : 43 degrés
      </li>
      <li>
        Marge de déplacement du capteur : ± 27 degrés
      </li>
      <li>
        Portée du capteur : 1,2 m – 3,5 m (à partir de 50 cm pour la version Kinect for Windows)
      </li>
    </ol>
  </li>
  
  <li>
    Flux de données : <ol>
      <li>
        320×240 en couleur 16 bits à 30 images/sec
      </li>
      <li>
        640×480 en couleur 32 bits à 30 images/sec
      </li>
      <li>
        Audio 16 bits à 16 kHz
      </li>
    </ol>
  </li>
  
  <li>
    Système de reconnaissance physique : <ol>
      <li>
        Jusqu’à 6 personnes et 2 joueurs actifs (4 joueurs actifs avec le SDK 1.0)
      </li>
      <li>
        20 articulations par squelette
      </li>
      <li>
        Application des mouvements des joueurs sur leurs avatars Xbox Live
      </li>
    </ol>
  </li>
  
  <li>
    Audio : <ol>
      <li>
        Chat vocal Xbox Live et chat vocal dans les jeux (nécessite un compte Xbox Live Gold)
      </li>
      <li>
        Suppression de l’écho
      </li>
      <li>
        Reconnaissance vocale multilingue (pour les français, cette fonction est disponible depuis le 06 décembre 2011 via une MàJ de la Xbox ).
      </li>
    </ol>
  </li>
</ol>

**Kinect & Processing**
  
3 bibliothèques externes existent pour relier la Kinect à Processing :

<p style="padding-left: 30px;">
  — <em>openKinect</em>
</p>

<p style="padding-left: 60px;">
</p>

<p style="padding-left: 60px;">
  Bibliothèque simple mais limitée. L&rsquo;exemple le plus intéressant est<em> RGB_depth </em>.
</p>

<p style="padding-left: 60px;">
  <a href="http://www.shiffman.net/p5/libraries/openkinect/openkinect.zip">Télécharger OpenKinect</a>
</p>

<p style="padding-left: 30px;">
   — <em>dLibs</em>
</p>

<p style="padding-left: 60px;">
  Bibliothèque puissante, mais qui ne fonctionne que sur Windows.
</p>

<p style="padding-left: 60px;">
  <strong>Installation de dLibs</strong>
</p>

<p style="padding-left: 60px;">
  I &#8211;<br /> télécharger la bibliothèque : <a href="https://github.com/diwi/dLibs">https://github.com/diwi/dLibs</a><br /> ou<br /> <a href="http://www.thomasdiewald.com/processing/libraries/dLibs_freenect/">http://www.thomasdiewald.com/processing/libraries/dLibs_freenect/</a>
</p>

<p style="padding-left: 60px;">
  II &#8211;<br /> dézipper et déplacer le dossier <em>dLibs_freenect</em> dans le dossier <em>libraries</em> de Processing.<br /> pour plus d&rsquo;info : <a href="http://wiki.processing.org/w/How_to_Install_a_Contributed_Library">http://wiki.processing.org/w/How_to_Install_a_Contributed_Library</a>
</p>

<p style="padding-left: 60px;">
  III &#8211;<br /> brancher la kinect à l&rsquo;ordinateur
</p>

<p style="padding-left: 60px;">
  IV &#8211;<br /> installer les pilotes :<br /> (&#8230; présents dans le dossier : <em>dLibs_freenect/library/kinect_driver_windows/</em>&#8230;)
</p>

<p style="padding-left: 30px;">
  — <em>SimpleOpenNI</em>
</p>

<p style="padding-left: 60px;">
  Page de la bibliothèque <a href="http://code.google.com/p/simple-openni/">SimpleOpenNI</a>
</p>

<p style="padding-left: 60px;">
  Page détaillée pour l&rsquo;<a href="http://code.google.com/p/simple-openni/wiki/Installation">installation sur différents systèmes d&rsquo;exploitation</a>
</p>

<p style="padding-left: 60px;">
  Bibliothèque plus avancée, multi plateforme (mac osx, windows, linux) et qui permet de faire plus de choses. Pour toutes ces raisons, je vais particulièrement m&rsquo;y intéresser.
</p>

<p style="padding-left: 60px;">
  L&rsquo;installation n&rsquo;est pas forcément simple pour un novice. Le passage par le <em><a href="http://www.osxfacile.com/terminal.html">terminal</a></em> peut effrayer. Ça mérite cependant le détour.
</p>

<p style="padding-left: 60px;">
  <strong>Installation SimpleOpenNI sur MAC OS X</strong>
</p>

<p style="padding-left: 60px;">
  Installée et testée sur macosx 10.6 +
</p>

<p style="padding-left: 60px;">
  I &#8211; Télécharger l&rsquo;<em>installer :</em> <a href="http://code.google.com/p/simple-openni/downloads/list?can=2&q=Installer+osx">lien de téléchargement</a>
</p>

<p style="padding-left: 60px;">
  II &#8211; Dézipper <em>l&rsquo;installer</em>
</p>

<p style="padding-left: 60px;">
  III &#8211; Installation à partir de <em>Terminal</em>
</p>

<p style="padding-left: 60px;">
</p>

&nbsp;

<p style="padding-left: 60px;">
  IV &#8211; Télécharger la bibliothèque <em>SimpleOpenNI</em> : <a href="http://simple-openni.googlecode.com/files/SimpleOpenNI-0.26.zip">lien de téléchargement</a>
</p>

<p style="padding-left: 60px;">
  V &#8211; Faire glisser le dossier<em> SimpleOpenNI </em>(contenant les dossiers<em> documentation</em>,<em> examples</em>,<em> library</em>) dans votre dossier <em>libraries</em>.
</p>

<p style="padding-left: 60px;">
  <strong>Installation SimpleOpenNI sur Windows</strong>
</p>

<p style="padding-left: 60px;">
  I &#8211; Installation des différents pilotes :
</p>

<p style="padding-left: 60px;">
  Télécharger le <a href="Installer http://code.google.com/p/simple-openni/downloads/list?can=2&q=OpenNI_NITE_Installer+win64&colspec=Filename+Summary+Uploaded+ReleaseDate+Size+DownloadCount">paquet d&rsquo;installation win64</a> ou le <a href="http://code.google.com/p/simple-openni/downloads/list?can=2&q=OpenNI_NITE_Installer+win32&colspec=Filename+Summary+Uploaded+ReleaseDate+Size+DownloadCount">paquet d&rsquo;installation win32</a>
</p>

<p style="padding-left: 60px;">
  Ces paquets contiennent 4 installateurs de pilotes :
</p>

<p style="padding-left: 60px;">
  nite-win64-1.5.2.21-dev.msi (installation de Nite, modules de gestion et de reconnaissance de détection des mouvements . Complète OpenNI)
</p>

<p style="padding-left: 60px;">
  openni-win64-1.5.2.23-dev.msi (installation des pilotes openNI : framework opensource permettant les &lsquo;interactions naturelles&rsquo;)
</p>

<p style="padding-left: 60px;">
  sensor-win64-5.1.0.41-redist.msi (installateur des pilotes pour la détection de capteurs génériques)
</p>

<p style="padding-left: 60px;">
  SensorKinect091-Bin-Win64-v5.1.0.25.msi (installateur des pilotes pour la Kinect)
</p>

<p style="padding-left: 60px;">
  Installer ces pilotes dans cette ordre :
</p>

<ol style="padding-left: 90px;">
  <li>
    installateur openni
  </li>
  <li>
    installateur nite
  </li>
  <li>
    installateur pilotes génériques pour capteurs
  </li>
  <li>
    installateur pilotes Kinect
  </li>
</ol>

<p style="padding-left: 60px;">
  Note : il est possible qu&rsquo;il faille installer <a href="http://www.oracle.com/technetwork/java/javase/downloads/jdk-7u2-download-1377129.html">JAVA64bits</a>. Il est également possible qu&rsquo;il faille installer les pilotes 32bits si ça ne fonctionne pas.
</p>

<p style="padding-left: 60px;">
  II &#8211; Installation de la bibliothèque pour Processing
</p>

<p style="padding-left: 60px;">
  Télécharger la bibliothèque <em>SimpleOpenNI</em> : <a href="http://simple-openni.googlecode.com/files/SimpleOpenNI-0.26.zip">lien de téléchargement<br /> </a>Faire glisser le dossier<em> SimpleOpenNI </em>(contenant les dossiers<em> documentation</em>,<em> examples</em>,<em> library</em>) dans votre dossier <em>libraries</em>.
</p>

**Exemples de la bibliothèque**

<div style="width: 510px" class="wp-caption alignnone">
  <img title="NiteSlider2d" src="http://simple-openni.googlecode.com/svn/site/screenshots/NiteSlider2d_small.jpg" alt="" width="500" height="395" />
  
  <p class="wp-caption-text">
    NiteSlider2d
  </p>
</div>

<div style="width: 510px" class="wp-caption alignnone">
  <img title="NiteHands" src="http://simple-openni.googlecode.com/svn/site/screenshots/NiteHands_small.jpg" alt="" width="500" height="395" />
  
  <p class="wp-caption-text">
    NiteHands
  </p>
</div>

<div style="width: 510px" class="wp-caption alignnone">
  <img title="http://simple-openni.googlecode.com/svn/site/screenshots/NiteCircle_small.jpg" src="http://simple-openni.googlecode.com/svn/site/screenshots/NiteCircle_small.jpg" alt="" width="500" height="395" />
  
  <p class="wp-caption-text">
    NiteCircle
  </p>
</div>

<div style="width: 510px" class="wp-caption alignnone">
  <img title="http://simple-openni.googlecode.com/svn/site/screenshots/UserScene3d_small.jpg" src="http://simple-openni.googlecode.com/svn/site/screenshots/UserScene3d_small.jpg" alt="" width="500" height="387" />
  
  <p class="wp-caption-text">
    UserScene3d
  </p>
</div>

<div style="width: 510px" class="wp-caption alignnone">
  <img title="http://simple-openni.googlecode.com/svn/site/screenshots/User3dOri_small.jpg" src="http://simple-openni.googlecode.com/svn/site/screenshots/User3dOri_small.jpg" alt="" width="500" height="387" />
  
  <p class="wp-caption-text">
    User3dOri
  </p>
</div>

<div style="width: 510px" class="wp-caption alignnone">
  <img title="http://simple-openni.googlecode.com/svn/site/screenshots/UserTest_small.jpg" src="http://simple-openni.googlecode.com/svn/site/screenshots/UserTest_small.jpg" alt="" width="500" height="395" />
  
  <p class="wp-caption-text">
    UserTest
  </p>
</div>

&nbsp;

**Exemples créés à partir de la bibliothèque**


  
[Kinect Experiments][3]


  
[Kinect + Hand Held Icosahedron: Towards an Intelligent Healing Space][4]



[Kinect Zeichenmodule][5]



[Body Dysmorphic Disorder][6]



[Kinect Graffiti™][7]



[NITEtracking_Cloth][8]

&nbsp;



[INTEGRARTE ENTREGARTE &#8211; kinect experiments][9]



&nbsp;

#### 

**Exercice d&rsquo;exemple de la bibliothèque simpleOpenNI (Hands 3D) commenté**

<pre><span style="color: #7e7e7e;">// on importe la bibliothèque SimpleOpenNI</span>
<span style="color: #cc6600;">import</span> SimpleOpenNI.*;

<span style="color: #7e7e7e;">// création d'un contexte de captation pour la kinect</span>
<span style="color: #7e7e7e;">//on créée donc un objet SimpleOpenNI appelé 'conetxt'</span>
SimpleOpenNI context;

<span style="color: #cc6600;">float</span>        zoomF =0.5f;
<span style="color: #cc6600;">float</span>        rotX = <span style="color: #cc6600;">radians</span>(180);  <span style="color: #7e7e7e;">// by default rotate the hole scene 180deg around the x-axis, </span>
<span style="color: #7e7e7e;">// the data from openni comes upside down</span>
<span style="color: #cc6600;">float</span>        rotY = <span style="color: #cc6600;">radians</span>(0);
<span style="color: #cc6600;">boolean</span>      handsTrackFlag = <span style="color: #cc6600;">false</span>;
<span style="color: #7e7e7e;">// variable vectorielle qui va nous permettre de</span>
<span style="color: #7e7e7e;">// dessiner le tracé et le point</span>
<span style="color: #7e7e7e;">// quand une main est détectée</span>
<span style="color: #cc6600;">PVector</span>      handVec = <span style="color: #cc6600;">new</span> <span style="color: #cc6600;">PVector</span>();
<span style="color: #7e7e7e;">// déclaration d'une variable de type tableau</span>
<span style="color: #7e7e7e;">//pour stocker les coordonnées des positions</span>
<span style="color: #7e7e7e;">// de la min</span>
<span style="color: #cc6600;">ArrayList</span>    handVecList = <span style="color: #cc6600;">new</span> <span style="color: #cc6600;">ArrayList</span>();
<span style="color: #cc6600;">int</span>          handVecListSize = 30;
<span style="color: #7e7e7e;">// declaration d'une varibale de chaine de caractere</span>
<span style="color: #7e7e7e;">// pour afficher le type de mouvement de la main</span>
<span style="color: #7e7e7e;">// détecté par la kinect</span>
<span style="color: #cc6600;">String</span>       lastGesture = <span style="color: #006699;">""</span>;

<span style="color: #cc6600;">void</span> <span style="color: #cc6600;">setup</span>()
{
  <span style="color: #7e7e7e;">//taille de la scene + activation de l'affichage en 3D (P3D)</span>
  <span style="color: #cc6600;">size</span>(1024, 768, <span style="color: #006699;">P3D</span>); 

  <span style="color: #7e7e7e;">// activation et paramètres de l'objet 'context'</span>
  context = <span style="color: #cc6600;">new</span> SimpleOpenNI(<span style="color: #cc6600;">this</span>);

  <span style="color: #7e7e7e;">// activer : context.setMirror(true); / désactiver :context.setMirror(false);</span>
  <span style="color: #7e7e7e;">// l'affichage en miroir</span>
  context.setMirror(<span style="color: #cc6600;">false</span>);

  <span style="color: #7e7e7e;">// si aucune profondeur n'est détectée </span>
  <span style="color: #cc6600;">if</span> (context.enableDepth() == <span style="color: #cc6600;">false</span>)
  {
    <span style="color: #7e7e7e;">// on affiche le message suivant :</span>
    <span style="color: #cc6600;">println</span>(<span style="color: #006699;">"Profondeur non activée, la kinect n'est peut être pas connectée !"</span>);
    <span style="color: #cc6600;">exit</span>();
    <span style="color: #cc6600;">return</span>;
  }

  <span style="color: #7e7e7e;">// activation de la détection des mouvements</span>
  context.enableGesture();
  <span style="color: #7e7e7e;">// activation de la détection des mains</span>
  context.enableHands();

  <span style="color: #7e7e7e;">// activation de la détection de certains mouvement de la main</span>
  <span style="color: #7e7e7e;">// activation de la détection de mouvement type 'vague'</span>
  context.addGesture(<span style="color: #006699;">"Wave"</span>);
  <span style="color: #7e7e7e;">// activation de la détection de mouvement type 'clic' </span>
  context.addGesture(<span style="color: #006699;">"Click"</span>);
  <span style="color: #7e7e7e;">// activation de la détection de mouvement type 'on lève la main'</span>
  context.addGesture(<span style="color: #006699;">"RaiseHand"</span>);

  <span style="color: #7e7e7e;">// réglage de la sensibilité de la detection de la main</span>
  <span style="color: #7e7e7e;">//context.setSmoothingHands(.5);</span>

  <span style="color: #cc6600;">smooth</span>();

  <span style="color: #cc6600;">perspective</span>(<span style="color: #cc6600;">radians</span>(45),
  <span style="color: #cc6600;">float</span>(<span style="color: #7e7e7e;"><strong>width</strong></span>)/<span style="color: #cc6600;">float</span>(<span style="color: #000000;">height</span>),
  10.0f, 150000.0f);
}

<span style="color: #cc6600;">void</span> <span style="color: #cc6600;">draw</span>()
{
  <span style="color: #7e7e7e;">// rafraichissement de l'image </span>
  <span style="color: #7e7e7e;">//capturée par la camera de la kinect</span>
  context.update();

  <span style="color: #7e7e7e;">//arriere plan noir</span>
  <span style="color: #cc6600;">background</span>(0);

  <span style="color: #7e7e7e;">// dans la representation générée par processing</span>
  <span style="color: #7e7e7e;">// on place notre point de vue</span>
  <span style="color: #cc6600;">translate</span>(<span style="color: #7e7e7e;"><strong>width</strong></span>/2, <span style="color: #000000;">height</span>/2, 0);</pre>

<pre>  <span style="color: #cc6600;">rotateX</span>(rotX);
  <span style="color: #cc6600;">rotateY</span>(rotY);
  <span style="color: #cc6600;">scale</span>(zoomF);

  <span style="color: #7e7e7e;">// dessin des points blancs de la 'carte 3D'</span>
  <span style="color: #cc6600;">int</span>[]   depthMap = context.depthMap();
  <span style="color: #7e7e7e;">// pour accélerer l'affichage, on ne représente </span>
  <span style="color: #7e7e7e;">// qu'un point blanc sur 3 </span>
  <span style="color: #cc6600;">int</span>     steps   = 3;
  <span style="color: #cc6600;">int</span>     index;
  <span style="color: #cc6600;">PVector</span> realWorldPoint;

  <span style="color: #7e7e7e;">// quand on deplace notre point de vue à l'aide des fleches du clavier</span>
  <span style="color: #7e7e7e;">// on le fait à partir d'un point qui est placé à 1000 de la camera</span>
  <span style="color: #cc6600;">translate</span>(0, 0, -1000);

  <span style="color: #7e7e7e;">// couleur des points de profondeur</span>
  <span style="color: #cc6600;">stroke</span>(200); 

  <span style="color: #7e7e7e;">// visualisation points 3D</span>
  <span style="color: #7e7e7e;">// a chaque point de profondeur sur la largeur détecté par la kinect</span>
  <span style="color: #cc6600;">for</span> (<span style="color: #cc6600;">int</span> <span style="color: #000000;">y</span>=0;<span style="color: #000000;">y</span> &lt; context.depthHeight();<span style="color: #000000;">y</span>+=steps)
  {
    <span style="color: #7e7e7e;">// a chaque point de profondeur sur la hauteur détecté par la kinect</span>
    <span style="color: #cc6600;">for</span> (<span style="color: #cc6600;">int</span> <span style="color: #000000;">x</span>=0;<span style="color: #000000;">x</span> &lt; context.depthWidth();<span style="color: #000000;">x</span>+=steps)
    {
      <span style="color: #7e7e7e;">// </span>
      index = <span style="color: #000000;">x</span> + <span style="color: #000000;">y</span> * context.depthWidth();
      <span style="color: #7e7e7e;">// si </span>
      <span style="color: #cc6600;">if</span> (depthMap[index] &rt; 0)
      { 
        realWorldPoint = context.depthMapRealWorld()[index];
        <span style="color: #7e7e7e;">// on dessine le point en recuperant les positions X, Y, Z</span>
        <span style="color: #7e7e7e;">// délivrés par la kinect</span>
        <span style="color: #cc6600;">point</span>(realWorldPoint.<span style="color: #000000;">x</span>, realWorldPoint.<span style="color: #000000;">y</span>, realWorldPoint.<span style="color: #000000;">z</span>);
      }
    }
  } 

  <span style="color: #7e7e7e;">// dessin de la main reconnue</span>
  <span style="color: #cc6600;">if</span> (handsTrackFlag)
  {
    <span style="color: #cc6600;">pushStyle</span>();

    <span style="color: #7e7e7e;">// couleur du tracé du mouvement de la main (jaune)</span>
    <span style="color: #cc6600;">stroke</span>(255, 255, 0, 200);
    <span style="color: #7e7e7e;">// on désactive la couleur de remplissage</span>
    <span style="color: #cc6600;">noFill</span>();
    <span style="color: #7e7e7e;">// on active un objet Iterator de la bibliothèque simpleOpenNI</span>
    <span style="color: #7e7e7e;">// qui permet de détecter le mouvement de la main dans le temps</span>
    Iterator itr = handVecList.iterator(); 
    <span style="color: #7e7e7e;">// commencement du dessin du tracé de mouvement</span>
    <span style="color: #cc6600;">beginShape</span>();
    <span style="color: #cc6600;">while</span> ( itr.hasNext () )
    { 
      <span style="color: #7e7e7e;">// création d'une variable PVector</span>
      <span style="color: #7e7e7e;">// pour le dessin du tracé du mouvment</span>
      <span style="color: #cc6600;">PVector</span> p = (<span style="color: #cc6600;">PVector</span>) itr.next();
      <span style="color: #7e7e7e;">// récupération des positions x, y, z</span>
      <span style="color: #7e7e7e;">// détectés par la kinect</span>
      <span style="color: #7e7e7e;">// et assignation aux coordonées pour le dessin du tracé</span>
      <span style="color: #cc6600;">vertex</span>(p.<span style="color: #000000;">x</span>, p.<span style="color: #000000;">y</span>, p.<span style="color: #000000;">z</span>);
    }
    <span style="color: #7e7e7e;">// fin du dessin du tracé de mouvement</span>
    <span style="color: #cc6600;">endShape</span>();   

    <span style="color: #7e7e7e;">// couleur et epaisseur du point rouge de la main</span>
    <span style="color: #cc6600;">stroke</span>(255, 0, 0);
    <span style="color: #cc6600;">strokeWeight</span>(4);
    <span style="color: #7e7e7e;">// récupération des positions x, y, z</span>
    <span style="color: #7e7e7e;">// détectés par la kinect</span>
    <span style="color: #7e7e7e;">// et assignation aux coordonées pour le dessin du point rouge</span>
    <span style="color: #cc6600;">point</span>(handVec.<span style="color: #000000;">x</span>, handVec.<span style="color: #000000;">y</span>, handVec.<span style="color: #000000;">z</span>);
    <span style="color: #cc6600;">popStyle</span>();
  }

  <span style="color: #7e7e7e;">// on dessine la camera et son volume de détection</span>
  <span style="color: #7e7e7e;">// (boite jaune)</span>
  <span style="color: #7e7e7e;">//context.drawCamFrustum();</span>
}

<span style="color: #7e7e7e;">// -----------------------------------------------------------------</span>
<span style="color: #7e7e7e;">// evenements et fonctions liés aux mains</span>
<span style="color: #7e7e7e;">// -----------------------------------------------------------------</span>
<span style="color: #7e7e7e;">// création de la detection d'une main par la kinect</span>
<span style="color: #cc6600;">void</span> onCreateHands(<span style="color: #cc6600;">int</span> handId, <span style="color: #cc6600;">PVector</span> pos, <span style="color: #cc6600;">float</span> time)
{
  <span style="color: #7e7e7e;">//println("onCreateHands - handId: " + handId + ", pos: " + pos + ", time:" + time);</span>

  handsTrackFlag = <span style="color: #cc6600;">true</span>;
  handVec = pos;

  handVecList.clear();
  handVecList.<span style="color: #cc6600;"><strong>add</strong></span>(pos);
}

<span style="color: #7e7e7e;">// mise à jour de la detection d'une main par la kinect</span>
<span style="color: #cc6600;">void</span> onUpdateHands(<span style="color: #cc6600;">int</span> handId, <span style="color: #cc6600;">PVector</span> pos, <span style="color: #cc6600;">float</span> time)
{
  <span style="color: #7e7e7e;">//println("onUpdateHandsCb - handId: " + handId + ", pos: " + pos + ", time:" + time);</span>
  handVec = pos;

  handVecList.<span style="color: #cc6600;"><strong>add</strong></span>(0, pos);
  <span style="color: #cc6600;">if</span> (handVecList.<span style="color: #cc6600;">size</span>() &rt;= handVecListSize)
  { <span style="color: #7e7e7e;">// remove the last point </span>
    handVecList.remove(handVecList.<span style="color: #cc6600;">size</span>()-1);
  }
}

<span style="color: #7e7e7e;">// suppression de la detection d'une main par la kinect</span>
<span style="color: #cc6600;">void</span> onDestroyHands(<span style="color: #cc6600;">int</span> handId, <span style="color: #cc6600;">float</span> time)
{
  <span style="color: #7e7e7e;">//println("onDestroyHandsCb - handId: " + handId + ", time:" + time);</span>

  handsTrackFlag = <span style="color: #cc6600;">false</span>;
  context.addGesture(lastGesture);
}

<span style="color: #7e7e7e;">// -----------------------------------------------------------------</span>
<span style="color: #7e7e7e;">// evenement de mouvement</span>
<span style="color: #7e7e7e;">// -----------------------------------------------------------------</span>
<span style="color: #7e7e7e;">// reconnaissance de type de mouvements de la main par la kinect</span>
<span style="color: #cc6600;">void</span> onRecognizeGesture(<span style="color: #cc6600;">String</span> strGesture, <span style="color: #cc6600;">PVector</span> idPosition, <span style="color: #cc6600;">PVector</span> endPosition)
{
  <span style="color: #cc6600;">println</span>(<span style="color: #006699;">"onRecognizeGesture - strGesture: "</span> + strGesture + <span style="color: #006699;">", idPosition: "</span> + idPosition + <span style="color: #006699;">", endPosition:"</span> + endPosition);

  lastGesture = strGesture;
  context.removeGesture(strGesture); 
  context.startTrackingHands(endPosition);
}

<span style="color: #cc6600;">void</span> onProgressGesture(<span style="color: #cc6600;">String</span> strGesture, <span style="color: #cc6600;">PVector</span> position, <span style="color: #cc6600;">float</span> progress)
{
  <span style="color: #7e7e7e;">//println("onProgressGesture - strGesture: " + strGesture + ", position: " + position + ", progress:" + progress);</span>
}

<span style="color: #7e7e7e;">// -----------------------------------------------------------------</span>
<span style="color: #7e7e7e;">// Evenement du clavier</span>
<span style="color: #7e7e7e;">// -----------------------------------------------------------------</span>
<span style="color: #cc6600;">void</span> <span style="color: #7e7e7e;"><strong>keyPressed</strong></span>()
{
  <span style="color: #cc6600;">switch</span>(<span style="color: #7e7e7e;"><strong>key</strong></span>)
  {
    <span style="color: #7e7e7e;">// si j'appuie sur la barre espace</span>
    <span style="color: #7e7e7e;">// j'active / je desactive l'affichage en miroir</span>
  <span style="color: #cc6600;">case</span> <span style="color: #006699;">' '</span>:
    context.setMirror(!context.mirror());
    <span style="color: #cc6600;">break</span>;
  }

  <span style="color: #cc6600;">switch</span>(<span style="color: #7e7e7e;"><strong>keyCode</strong></span>)
  {
    <span style="color: #7e7e7e;">// si j'appuie sur la fleche gauche</span>
    <span style="color: #7e7e7e;">// je deplace mon point de vue vers la gauche</span>
  <span style="color: #cc6600;">case</span> <span style="color: #006699;">LEFT</span>:
    rotY += 0.1f;
    <span style="color: #cc6600;">break</span>;
    <span style="color: #7e7e7e;">// si j'appuie sur la fleche droite</span>
    <span style="color: #7e7e7e;">// je deplace mon point de vue vers la droite</span>
  <span style="color: #cc6600;">case</span> <span style="color: #006699;">RIGHT</span>:
    rotY -= 0.1f;
    <span style="color: #cc6600;">break</span>;
    <span style="color: #7e7e7e;">// si j'appuie sur la fleche haut</span>
    <span style="color: #7e7e7e;">// je deplace mon point de vue vers le haut</span>
  <span style="color: #cc6600;">case</span> <span style="color: #006699;">UP</span>:
    <span style="color: #cc6600;">if</span> (keyEvent.isShiftDown())
      zoomF += 0.01f;
    <span style="color: #cc6600;">else</span>
      rotX += 0.1f;
    <span style="color: #cc6600;">break</span>;
    <span style="color: #7e7e7e;">// si j'appuie sur la fleche bas</span>
    <span style="color: #7e7e7e;">// je deplace mon point de vue vers le bas</span>
  <span style="color: #cc6600;">case</span> <span style="color: #006699;">DOWN</span>:
    <span style="color: #cc6600;">if</span> (keyEvent.isShiftDown())
    {
      zoomF -= 0.01f;
      <span style="color: #cc6600;">if</span> (zoomF &lt; 0.01)
        zoomF = 0.01;
    }
    <span style="color: #cc6600;">else</span>
      rotX -= 0.1f;
    <span style="color: #cc6600;">break</span>;
  }
}</pre>

[Télécharger le sketch commenté ][10]

**Exercice technique**

<div id="attachment_124837" style="width: 480px" class="wp-caption alignnone">
  <a href="http://docilestudio.fr/ESA/wp-content/uploads/2012/04/kinectSphere.png"><img class="size-medium wp-image-124837" title="kinectSphere" src="http://docilestudio.fr/ESA/wp-content/uploads/2012/04/kinectSphere-470x373.png" alt="" width="470" height="373" /></a>
  
  <p class="wp-caption-text">
    Diriger un objet 3D (sphere) généré par Processing avec la main détectée par la kinect
  </p>
</div>

<pre><span style="color: #cc6600;">import</span> processing.<span style="color: #006699;">opengl</span>.*;

<span style="color: #7e7e7e;">// on importe la bibliothèque SimpleOpenNI</span>
<span style="color: #cc6600;">import</span> SimpleOpenNI.*;

<span style="color: #7e7e7e;">// création d'un contexte de captation pour la kinect</span>
<span style="color: #7e7e7e;">//on créée donc un objet SimpleOpenNI appelé 'conetxt'</span>
SimpleOpenNI context;

<span style="color: #cc6600;">float</span>        zoomF =0.5f;
<span style="color: #cc6600;">float</span>        rotX = <span style="color: #cc6600;">radians</span>(180);  <span style="color: #7e7e7e;">// by default rotate the hole scene 180deg around the x-axis, </span>
<span style="color: #7e7e7e;">// the data from openni comes upside down</span>
<span style="color: #cc6600;">float</span>        rotY = <span style="color: #cc6600;">radians</span>(0);
<span style="color: #cc6600;">boolean</span>      handsTrackFlag = <span style="color: #cc6600;">false</span>;
<span style="color: #7e7e7e;">// variable vectorielle qui va nous permettre de</span>
<span style="color: #7e7e7e;">// dessiner le tracé et le point</span>
<span style="color: #7e7e7e;">// quand une main est détectée</span>
<span style="color: #cc6600;">PVector</span>      handVec = <span style="color: #cc6600;">new</span> <span style="color: #cc6600;">PVector</span>();
<span style="color: #7e7e7e;">// déclaration d'une variable de type tableau</span>
<span style="color: #7e7e7e;">//pour stocker les coordonnées des positions</span>
<span style="color: #7e7e7e;">// de la min</span>
<span style="color: #cc6600;">ArrayList</span>    handVecList = <span style="color: #cc6600;">new</span> <span style="color: #cc6600;">ArrayList</span>();
<span style="color: #cc6600;">int</span>          handVecListSize = 30;
<span style="color: #7e7e7e;">// declaration d'une varibale de chaine de caractere</span>
<span style="color: #7e7e7e;">// pour afficher le type de mouvement de la main</span>
<span style="color: #7e7e7e;">// détecté par la kinect</span>
<span style="color: #cc6600;">String</span>       lastGesture = <span style="color: #006699;">""</span>;

<span style="color: #cc6600;">void</span> <span style="color: #cc6600;"><strong>setup</strong></span>()
{
  <span style="color: #7e7e7e;">//taille de la scene + activation de l'affichage en 3D (P3D)</span>
  <span style="color: #cc6600;">size</span>(1024, 768, <span style="color: #006699;">OPENGL</span>); 

  <span style="color: #7e7e7e;">// activation et paramètres de l'objet 'context'</span>
  context = <span style="color: #cc6600;">new</span> SimpleOpenNI(<span style="color: #cc6600;">this</span>);

  <span style="color: #7e7e7e;">// activer : context.setMirror(true); / désactiver :context.setMirror(false);</span>
  <span style="color: #7e7e7e;">// l'affichage en miroir</span>
  context.setMirror(<span style="color: #cc6600;">false</span>);

  <span style="color: #7e7e7e;">// si aucune profondeur n'est détectée </span>
  <span style="color: #cc6600;">if</span> (context.enableDepth() == <span style="color: #cc6600;">false</span>)
  {
    <span style="color: #7e7e7e;">// on affiche le message suivant :</span>
    <span style="color: #cc6600;">println</span>(<span style="color: #006699;">"Profondeur non activée, la kinect n'est peut être pas connectée !"</span>);
    <span style="color: #cc6600;">exit</span>();
    <span style="color: #cc6600;">return</span>;
  }

  <span style="color: #7e7e7e;">// activation de la détection des mouvements</span>
  context.enableGesture();
  <span style="color: #7e7e7e;">// activation de la détection des mains</span>
  context.enableHands();

  <span style="color: #7e7e7e;">// activation de la détection de certains mouvement de la main</span>
  <span style="color: #7e7e7e;">// activation de la détection de mouvement type 'vague'</span>
  context.addGesture(<span style="color: #006699;">"Wave"</span>);
  <span style="color: #7e7e7e;">// activation de la détection de mouvement type 'clic' </span>
  context.addGesture(<span style="color: #006699;">"Click"</span>);
  <span style="color: #7e7e7e;">// activation de la détection de mouvement type 'on lève la main'</span>
  context.addGesture(<span style="color: #006699;">"RaiseHand"</span>);

  <span style="color: #7e7e7e;">// réglage de la sensibilité de la detection de la main</span>
  <span style="color: #7e7e7e;">//context.setSmoothingHands(.5);</span>

  <span style="color: #cc6600;">smooth</span>();

  <span style="color: #cc6600;">perspective</span>(<span style="color: #cc6600;">radians</span>(45),
  <span style="color: #cc6600;">float</span>(<span style="color: #006699;">width</span>)/<span style="color: #cc6600;">float</span>(<span style="color: #006699;">height</span>),
  10.0f, 150000.0f);

}

<span style="color: #cc6600;">void</span> <span style="color: #cc6600;"><strong>draw</strong></span>()
{
  <span style="color: #cc6600;">lights</span>();
  <span style="color: #7e7e7e;">// rafraichissement de l'image </span>
  <span style="color: #7e7e7e;">//capturée par la camera de la kinect</span>
  context.update();

  <span style="color: #7e7e7e;">//arriere plan noir</span>
  <span style="color: #cc6600;">background</span>(0);

  <span style="color: #7e7e7e;">// dans la representation générée par processing</span>
  <span style="color: #7e7e7e;">// on place notre point de vue</span>
  <span style="color: #cc6600;">translate</span>(<span style="color: #006699;">width</span>/2, <span style="color: #006699;">height</span>/2, 0);
  <span style="color: #cc6600;">rotateX</span>(rotX);
  <span style="color: #cc6600;">rotateY</span>(rotY);
  <span style="color: #cc6600;">scale</span>(zoomF);

  <span style="color: #7e7e7e;">// dessin des points blancs de la 'carte 3D'</span>
  <span style="color: #cc6600;">int</span>[]   depthMap = context.depthMap();
  <span style="color: #7e7e7e;">// pour accélerer l'affichage, on ne représente </span>
  <span style="color: #7e7e7e;">// qu'un point blanc sur 3 </span>
  <span style="color: #cc6600;">int</span>     steps   = 3;
  <span style="color: #cc6600;">int</span>     index;
  <span style="color: #cc6600;">PVector</span> realWorldPoint;

  <span style="color: #7e7e7e;">// quand on deplace notre point de vue à l'aide des fleches du clavier</span>
  <span style="color: #7e7e7e;">// on le fait à partir d'un point qui est placé à 1000 de la camera</span>
  <span style="color: #cc6600;">translate</span>(0, 0, -1000);

  <span style="color: #7e7e7e;">// couleur des points de profondeur</span>
  <span style="color: #cc6600;">stroke</span>(200); 

  <span style="color: #7e7e7e;">// visualisation points 3D</span>
  <span style="color: #7e7e7e;">// a chaque point de profondeur sur la largeur détecté par la kinect</span>
  <span style="color: #cc6600;">for</span> (<span style="color: #cc6600;">int</span> y=0;y &lt; context.depthHeight();y+=steps)
  {
    <span style="color: #7e7e7e;">// a chaque point de profondeur sur la hauteur détecté par la kinect</span>
    <span style="color: #cc6600;">for</span> (<span style="color: #cc6600;">int</span> x=0;x &lt; context.depthWidth();x+=steps)
    {
      <span style="color: #7e7e7e;">// </span>
      index = x + y * context.depthWidth();
      <span style="color: #7e7e7e;">// si </span>
      <span style="color: #cc6600;">if</span> (depthMap[index] &gt; 0)
      { 
        realWorldPoint = context.depthMapRealWorld()[index];
        <span style="color: #7e7e7e;">// on dessine le point en recuperant les positions X, Y, Z</span>
        <span style="color: #7e7e7e;">// délivrés par la kinect</span>
        <span style="color: #cc6600;">point</span>(realWorldPoint.x, realWorldPoint.y, realWorldPoint.z);
      }
    }
  } 

  <span style="color: #7e7e7e;">// dessin de la main reconnue</span>
  <span style="color: #cc6600;">if</span> (handsTrackFlag)
  {
    <span style="color: #cc6600;"><strong>pushStyle</strong></span>();

    <span style="color: #7e7e7e;">// couleur et epaisseur de la sphère qui suit la main</span>
    <span style="color: #cc6600;">noStroke</span>();
    <span style="color: #cc6600;">fill</span>(255, 0, 255);
    <span style="color: #7e7e7e;">// récupération des positions x, y, z</span>
    <span style="color: #7e7e7e;">// détectés par la kinect</span>
    <span style="color: #7e7e7e;">// et assignation aux coordonées pour le dessin dela sphère</span>
    <span style="color: #7e7e7e;">//point(handVec.x, handVec.y, handVec.z);</span>
    <span style="color: #cc6600;">translate</span>(handVec.x-20, handVec.y-20, handVec.z-20);
    <span style="color: #7e7e7e;">//ellipse(x[i], y[i], i, i);</span>
    <span style="color: #cc6600;">sphere</span>(20);    

    <span style="color: #cc6600;"><strong>popStyle</strong></span>();
  }

  <span style="color: #7e7e7e;">// on dessine la camera et son volume de détection</span>
  <span style="color: #7e7e7e;">// (boite jaune)</span>
  <span style="color: #7e7e7e;">//context.drawCamFrustum();</span>
}

<span style="color: #7e7e7e;">// -----------------------------------------------------------------</span>
<span style="color: #7e7e7e;">// evenements et fonctions liés aux mains</span>
<span style="color: #7e7e7e;">// -----------------------------------------------------------------</span>
<span style="color: #7e7e7e;">// création de la detection d'une main par la kinect</span>
<span style="color: #cc6600;">void</span> onCreateHands(<span style="color: #cc6600;">int</span> handId, <span style="color: #cc6600;">PVector</span> pos, <span style="color: #cc6600;">float</span> time)
{
  <span style="color: #7e7e7e;">//println("onCreateHands - handId: " + handId + ", pos: " + pos + ", time:" + time);</span>

  handsTrackFlag = <span style="color: #cc6600;">true</span>;
  handVec = pos;

  handVecList.clear();
  handVecList.<span style="color: #cc6600;">add</span>(pos);
}

<span style="color: #7e7e7e;">// mise à jour de la detection d'une main par la kinect</span>
<span style="color: #cc6600;">void</span> onUpdateHands(<span style="color: #cc6600;">int</span> handId, <span style="color: #cc6600;">PVector</span> pos, <span style="color: #cc6600;">float</span> time)
{
  <span style="color: #7e7e7e;">//println("onUpdateHandsCb - handId: " + handId + ", pos: " + pos + ", time:" + time);</span>
  handVec = pos;

  handVecList.<span style="color: #cc6600;">add</span>(0, pos);
  <span style="color: #cc6600;">if</span> (handVecList.<span style="color: #cc6600;">size</span>() &gt;= handVecListSize)
  { <span style="color: #7e7e7e;">// remove the last point </span>
    handVecList.remove(handVecList.<span style="color: #cc6600;">size</span>()-1);
  }
}

<span style="color: #7e7e7e;">// suppression de la detection d'une main par la kinect</span>
<span style="color: #cc6600;">void</span> onDestroyHands(<span style="color: #cc6600;">int</span> handId, <span style="color: #cc6600;">float</span> time)
{
  <span style="color: #7e7e7e;">//println("onDestroyHandsCb - handId: " + handId + ", time:" + time);</span>

  handsTrackFlag = <span style="color: #cc6600;">false</span>;
  context.addGesture(lastGesture);
}

<span style="color: #7e7e7e;">// -----------------------------------------------------------------</span>
<span style="color: #7e7e7e;">// evenement de mouvement</span>
<span style="color: #7e7e7e;">// -----------------------------------------------------------------</span>
<span style="color: #7e7e7e;">// reconnaissance de type de mouvements de la main par la kinect</span>
<span style="color: #cc6600;">void</span> onRecognizeGesture(<span style="color: #cc6600;">String</span> strGesture, <span style="color: #cc6600;">PVector</span> idPosition, <span style="color: #cc6600;">PVector</span> endPosition)
{
  <span style="color: #cc6600;">println</span>(<span style="color: #006699;">"onRecognizeGesture - strGesture: "</span> + strGesture + <span style="color: #006699;">", idPosition: "</span> + idPosition + <span style="color: #006699;">", endPosition:"</span> + endPosition);

  lastGesture = strGesture;
  context.removeGesture(strGesture); 
  context.startTrackingHands(endPosition);
}

<span style="color: #cc6600;">void</span> onProgressGesture(<span style="color: #cc6600;">String</span> strGesture, <span style="color: #cc6600;">PVector</span> position, <span style="color: #cc6600;">float</span> progress)
{
  <span style="color: #7e7e7e;">//println("onProgressGesture - strGesture: " + strGesture + ", position: " + position + ", progress:" + progress);</span>
}

<span style="color: #7e7e7e;">// -----------------------------------------------------------------</span>
<span style="color: #7e7e7e;">// Evenement du clavier</span>
<span style="color: #7e7e7e;">// -----------------------------------------------------------------</span>
<span style="color: #cc6600;">void</span> <span style="color: #006699;">keyPressed</span>()
{
  <span style="color: #cc6600;">switch</span>(<span style="color: #006699;">key</span>)
  {
    <span style="color: #7e7e7e;">// si j'appuie sur la barre espace</span>
    <span style="color: #7e7e7e;">// j'active / je desactive l'affichage en miroir</span>
  <span style="color: #cc6600;">case</span> <span style="color: #006699;">' '</span>:
    context.setMirror(!context.mirror());
    <span style="color: #cc6600;">break</span>;
  }

  <span style="color: #cc6600;">switch</span>(<span style="color: #006699;">keyCode</span>)
  {
    <span style="color: #7e7e7e;">// si j'appuie sur la fleche gauche</span>
    <span style="color: #7e7e7e;">// je deplace mon point de vue vers la gauche</span>
  <span style="color: #cc6600;">case</span> <span style="color: #006699;">LEFT</span>:
    rotY += 0.1f;
    <span style="color: #cc6600;">break</span>;
    <span style="color: #7e7e7e;">// si j'appuie sur la fleche droite</span>
    <span style="color: #7e7e7e;">// je deplace mon point de vue vers la droite</span>
  <span style="color: #cc6600;">case</span> <span style="color: #006699;">RIGHT</span>:
    rotY -= 0.1f;
    <span style="color: #cc6600;">break</span>;
    <span style="color: #7e7e7e;">// si j'appuie sur la fleche haut</span>
    <span style="color: #7e7e7e;">// je deplace mon point de vue vers le haut</span>
  <span style="color: #cc6600;">case</span> <span style="color: #006699;">UP</span>:
    <span style="color: #cc6600;">if</span> (keyEvent.isShiftDown())
      zoomF += 0.01f;
    <span style="color: #cc6600;">else</span>
      rotX += 0.1f;
    <span style="color: #cc6600;">break</span>;
    <span style="color: #7e7e7e;">// si j'appuie sur la fleche bas</span>
    <span style="color: #7e7e7e;">// je deplace mon point de vue vers le bas</span>
  <span style="color: #cc6600;">case</span> <span style="color: #006699;">DOWN</span>:
    <span style="color: #cc6600;">if</span> (keyEvent.isShiftDown())
    {
      zoomF -= 0.01f;
      <span style="color: #cc6600;">if</span> (zoomF &lt; 0.01)
        zoomF = 0.01;
    }
    <span style="color: #cc6600;">else</span>
      rotX -= 0.1f;
    <span style="color: #cc6600;">break</span>;
  }
}</pre>

&nbsp;

[Télécharger le sketch][11]

&nbsp;

<div id="attachment_125739" style="width: 480px" class="wp-caption alignnone">
  <a href="http://docilestudio.fr/ESA/wp-content/uploads/2012/04/kinectObjLoader.png"><img class="size-medium wp-image-125739" title="kinectObjLoader" src="http://docilestudio.fr/ESA/wp-content/uploads/2012/04/kinectObjLoader-470x373.png" alt="" width="470" height="373" /></a>
  
  <p class="wp-caption-text">
    Importer un modele 3D et interagir avec lui par la Kinect
  </p>
</div>

Pré requis : avoir un modèle 3D enregistré sous un fichier .obj

[Isntallation de le bibliothèque objLoader][12]

&nbsp;

<pre><span style="color: #cc6600;">import</span> processing.<span style="color: #006699;">opengl</span>.*;
<span style="color: #7e7e7e;">// on importe la bibliothèque obj loader qui nous permet </span>
<span style="color: #7e7e7e;">// d'importer le fichier .obj</span>
<span style="color: #cc6600;">import</span> saito.objloader.*;

<span style="color: #7e7e7e;">// on importe la bibliothèque SimpleOpenNI</span>
<span style="color: #cc6600;">import</span> SimpleOpenNI.*;

<span style="color: #7e7e7e;">// création d'un contexte de captation pour la kinect</span>
<span style="color: #7e7e7e;">//on créée donc un objet SimpleOpenNI appelé 'conetxt'</span>
SimpleOpenNI context;

<span style="color: #cc6600;">float</span>        zoomF =0.5f;
<span style="color: #cc6600;">float</span>        rotX = <span style="color: #cc6600;">radians</span>(180);  <span style="color: #7e7e7e;">// by default rotate the hole scene 180deg around the x-axis, </span>
<span style="color: #7e7e7e;">// the data from openni comes upside down</span>
<span style="color: #cc6600;">float</span>        rotY = <span style="color: #cc6600;">radians</span>(0);
<span style="color: #cc6600;">boolean</span>      handsTrackFlag = <span style="color: #cc6600;">false</span>;
<span style="color: #7e7e7e;">// variable vectorielle qui va nous permettre de</span>
<span style="color: #7e7e7e;">// dessiner le tracé et le point</span>
<span style="color: #7e7e7e;">// quand une main est détectée</span>
<span style="color: #cc6600;">PVector</span>      handVec = <span style="color: #cc6600;">new</span> <span style="color: #cc6600;">PVector</span>();
<span style="color: #7e7e7e;">// déclaration d'une variable de type tableau</span>
<span style="color: #7e7e7e;">//pour stocker les coordonnées des positions</span>
<span style="color: #7e7e7e;">// de la min</span>
<span style="color: #cc6600;">ArrayList</span>    handVecList = <span style="color: #cc6600;">new</span> <span style="color: #cc6600;">ArrayList</span>();
<span style="color: #cc6600;">int</span>          handVecListSize = 30;
<span style="color: #7e7e7e;">// declaration d'une varibale de chaine de caractere</span>
<span style="color: #7e7e7e;">// pour afficher le type de mouvement de la main</span>
<span style="color: #7e7e7e;">// détecté par la kinect</span>
<span style="color: #cc6600;">String</span>       lastGesture = <span style="color: #006699;">""</span>;

<span style="color: #7e7e7e;">// on créée un objet dans cette bibliotheque</span>
<span style="color: #7e7e7e;">// on le nomme model</span>
OBJModel <span style="color: #006699;">model</span>;

<span style="color: #cc6600;">void</span> <span style="color: #cc6600;"><strong>setup</strong></span>()
{
  <span style="color: #7e7e7e;">//taille de la scene + activation de l'affichage en 3D (P3D)</span>
  <span style="color: #cc6600;">size</span>(1024, 768, <span style="color: #006699;">OPENGL</span>); 

  <span style="color: #7e7e7e;">// activation et paramètres de l'objet 'context'</span>
  context = <span style="color: #cc6600;">new</span> SimpleOpenNI(<span style="color: #cc6600;">this</span>);

  <span style="color: #7e7e7e;">// activer : context.setMirror(true); / désactiver :context.setMirror(false);</span>
  <span style="color: #7e7e7e;">// l'affichage en miroir</span>
  context.setMirror(<span style="color: #cc6600;">false</span>);

  <span style="color: #7e7e7e;">// si aucune profondeur n'est détectée </span>
  <span style="color: #cc6600;">if</span> (context.enableDepth() == <span style="color: #cc6600;">false</span>)
  {
    <span style="color: #7e7e7e;">// on affiche le message suivant :</span>
    <span style="color: #cc6600;">println</span>(<span style="color: #006699;">"Profondeur non activée, la kinect n'est peut être pas connectée !"</span>);
    <span style="color: #cc6600;">exit</span>();
    <span style="color: #cc6600;">return</span>;
  }

  <span style="color: #7e7e7e;">// activation de la détection des mouvements</span>
  context.enableGesture();
  <span style="color: #7e7e7e;">// activation de la détection des mains</span>
  context.enableHands();

  <span style="color: #7e7e7e;">// activation de la détection de certains mouvement de la main</span>
  <span style="color: #7e7e7e;">// activation de la détection de mouvement type 'vague'</span>
  context.addGesture(<span style="color: #006699;">"Wave"</span>);
  <span style="color: #7e7e7e;">// activation de la détection de mouvement type 'clic' </span>
  context.addGesture(<span style="color: #006699;">"Click"</span>);
  <span style="color: #7e7e7e;">// activation de la détection de mouvement type 'on lève la main'</span>
  context.addGesture(<span style="color: #006699;">"RaiseHand"</span>);

  <span style="color: #7e7e7e;">// réglage de la sensibilité de la detection de la main</span>
  <span style="color: #7e7e7e;">//context.setSmoothingHands(.5);</span>

  <span style="color: #cc6600;">smooth</span>();

  <span style="color: #cc6600;">perspective</span>(<span style="color: #cc6600;">radians</span>(45),
  <span style="color: #cc6600;">float</span>(<span style="color: #006699;">width</span>)/<span style="color: #cc6600;">float</span>(<span style="color: #006699;">height</span>),
  10.0f, 150000.0f);

  <span style="color: #7e7e7e;">//on appelle notre objet model</span>
  <span style="color: #7e7e7e;">// et on lui donne ses caracteristiques (le fichier .obj lié...)</span>
  <span style="color: #006699;">model</span> = <span style="color: #cc6600;">new</span> OBJModel(<span style="color: #cc6600;">this</span>, <span style="color: #006699;">"map_ground_path_s.obj"</span>, <span style="color: #006699;">"relative"</span>, <span style="color: #006699;">QUADS</span>);
  <span style="color: #7e7e7e;">// activation mode debug</span>
  <span style="color: #7e7e7e;">// model.enableDebug();</span>

  <span style="color: #7e7e7e;">//on indique l'echelle de notre objet</span>
  <span style="color: #006699;">model</span>.<span style="color: #cc6600;">scale</span>(200);
  <span style="color: #7e7e7e;">//on le déplace au centre de notre scène</span>
  <span style="color: #006699;">model</span>.translateToCenter();
}

<span style="color: #cc6600;">void</span> <span style="color: #cc6600;"><strong>draw</strong></span>()
{
  <span style="color: #cc6600;">lights</span>();
  <span style="color: #7e7e7e;">// rafraichissement de l'image </span>
  <span style="color: #7e7e7e;">//capturée par la camera de la kinect</span>
  context.update();

  <span style="color: #7e7e7e;">//arriere plan noir</span>
  <span style="color: #cc6600;">background</span>(0);

  <span style="color: #7e7e7e;">// dans la representation générée par processing</span>
  <span style="color: #7e7e7e;">// on place notre point de vue</span>
  <span style="color: #cc6600;">translate</span>(<span style="color: #006699;">width</span>/2, <span style="color: #006699;">height</span>/2, 0);
  <span style="color: #cc6600;">rotateX</span>(rotX);
  <span style="color: #cc6600;">rotateY</span>(rotY);
  <span style="color: #cc6600;">scale</span>(zoomF);

  <span style="color: #7e7e7e;">// dessin des points blancs de la 'carte 3D'</span>
  <span style="color: #cc6600;">int</span>[]   depthMap = context.depthMap();
  <span style="color: #7e7e7e;">// pour accélerer l'affichage, on ne représente </span>
  <span style="color: #7e7e7e;">// qu'un point blanc sur 3 </span>
  <span style="color: #cc6600;">int</span>     steps   = 3;
  <span style="color: #cc6600;">int</span>     index;
  <span style="color: #cc6600;">PVector</span> realWorldPoint;

  <span style="color: #7e7e7e;">// quand on deplace notre point de vue à l'aide des fleches du clavier</span>
  <span style="color: #7e7e7e;">// on le fait à partir d'un point qui est placé à 1000 de la camera</span>
  <span style="color: #cc6600;">translate</span>(0, 0, -1000);

  <span style="color: #7e7e7e;">// couleur des points de profondeur</span>
  <span style="color: #cc6600;">stroke</span>(200); 

  <span style="color: #7e7e7e;">// visualisation points 3D</span>
  <span style="color: #7e7e7e;">// a chaque point de profondeur sur la largeur détecté par la kinect</span>
  <span style="color: #cc6600;">for</span> (<span style="color: #cc6600;">int</span> y=0;y &lt; context.depthHeight();y+=steps)
  {
    <span style="color: #7e7e7e;">// a chaque point de profondeur sur la hauteur détecté par la kinect</span>
    <span style="color: #cc6600;">for</span> (<span style="color: #cc6600;">int</span> x=0;x &lt; context.depthWidth();x+=steps)
    {
      <span style="color: #7e7e7e;">// </span>
      index = x + y * context.depthWidth();
      <span style="color: #7e7e7e;">// si </span>
      <span style="color: #cc6600;">if</span> (depthMap[index] &gt; 0)
      { 
        realWorldPoint = context.depthMapRealWorld()[index];
        <span style="color: #7e7e7e;">// on dessine le point en recuperant les positions X, Y, Z</span>
        <span style="color: #7e7e7e;">// délivrés par la kinect</span>
        <span style="color: #cc6600;">point</span>(realWorldPoint.x, realWorldPoint.y, realWorldPoint.z);
      }
    }
  } 

  <span style="color: #7e7e7e;">// dessin de la main reconnue</span>
  <span style="color: #cc6600;">if</span> (handsTrackFlag)
  {
    <span style="color: #cc6600;"><strong>pushStyle</strong></span>();

    <span style="color: #7e7e7e;">// couleur et epaisseur de la sphère qui suit la main</span>
    <span style="color: #cc6600;">noStroke</span>();
    <span style="color: #cc6600;">fill</span>(255, 0, 255);
    <span style="color: #7e7e7e;">// récupération des positions x, y, z</span>
    <span style="color: #7e7e7e;">// détectés par la kinect</span>
    <span style="color: #7e7e7e;">// et assignation aux coordonées pour le dessin dela sphère</span>
    <span style="color: #7e7e7e;">//point(handVec.x, handVec.y, handVec.z);</span>
    <span style="color: #cc6600;">translate</span>(handVec.x-20, handVec.y-20, handVec.z-20);
    <span style="color: #7e7e7e;">// je fais subir une rotation</span>
    <span style="color: #7e7e7e;">// à mon modele 3D pour qu'il soit affiché</span>
    <span style="color: #7e7e7e;">// dans une position visible et intéressante</span>
    <span style="color: #cc6600;">rotateY</span>(1.5);
    <span style="color: #cc6600;">rotateZ</span>(1.5);

    <span style="color: #7e7e7e;">//en appliquant la fonction draw à notre objet 'model'</span>
    <span style="color: #7e7e7e;">// on le fait se dessiner</span>
    <span style="color: #006699;">model</span>.<span style="color: #cc6600;"><strong>draw</strong></span>(); 

    <span style="color: #cc6600;"><strong>popStyle</strong></span>();
  }

  <span style="color: #7e7e7e;">// on dessine la camera et son volume de détection</span>
  <span style="color: #7e7e7e;">// (boite jaune)</span>
  <span style="color: #7e7e7e;">//context.drawCamFrustum();</span>
}

<span style="color: #7e7e7e;">// -----------------------------------------------------------------</span>
<span style="color: #7e7e7e;">// evenements et fonctions liés aux mains</span>
<span style="color: #7e7e7e;">// -----------------------------------------------------------------</span>
<span style="color: #7e7e7e;">// création de la detection d'une main par la kinect</span>
<span style="color: #cc6600;">void</span> onCreateHands(<span style="color: #cc6600;">int</span> handId, <span style="color: #cc6600;">PVector</span> pos, <span style="color: #cc6600;">float</span> time)
{
  <span style="color: #7e7e7e;">//println("onCreateHands - handId: " + handId + ", pos: " + pos + ", time:" + time);</span>

  handsTrackFlag = <span style="color: #cc6600;">true</span>;
  handVec = pos;

  handVecList.clear();
  handVecList.<span style="color: #cc6600;">add</span>(pos);
}

<span style="color: #7e7e7e;">// mise à jour de la detection d'une main par la kinect</span>
<span style="color: #cc6600;">void</span> onUpdateHands(<span style="color: #cc6600;">int</span> handId, <span style="color: #cc6600;">PVector</span> pos, <span style="color: #cc6600;">float</span> time)
{
  <span style="color: #7e7e7e;">//println("onUpdateHandsCb - handId: " + handId + ", pos: " + pos + ", time:" + time);</span>
  handVec = pos;

  handVecList.<span style="color: #cc6600;">add</span>(0, pos);
  <span style="color: #cc6600;">if</span> (handVecList.<span style="color: #cc6600;">size</span>() &gt;= handVecListSize)
  { <span style="color: #7e7e7e;">// remove the last point </span>
    handVecList.remove(handVecList.<span style="color: #cc6600;">size</span>()-1);
  }
}

<span style="color: #7e7e7e;">// suppression de la detection d'une main par la kinect</span>
<span style="color: #cc6600;">void</span> onDestroyHands(<span style="color: #cc6600;">int</span> handId, <span style="color: #cc6600;">float</span> time)
{
  <span style="color: #7e7e7e;">//println("onDestroyHandsCb - handId: " + handId + ", time:" + time);</span>

  handsTrackFlag = <span style="color: #cc6600;">false</span>;
  context.addGesture(lastGesture);
}

<span style="color: #7e7e7e;">// -----------------------------------------------------------------</span>
<span style="color: #7e7e7e;">// evenement de mouvement</span>
<span style="color: #7e7e7e;">// -----------------------------------------------------------------</span>
<span style="color: #7e7e7e;">// reconnaissance de type de mouvements de la main par la kinect</span>
<span style="color: #cc6600;">void</span> onRecognizeGesture(<span style="color: #cc6600;">String</span> strGesture, <span style="color: #cc6600;">PVector</span> idPosition, <span style="color: #cc6600;">PVector</span> endPosition)
{
  <span style="color: #cc6600;">println</span>(<span style="color: #006699;">"onRecognizeGesture - strGesture: "</span> + strGesture + <span style="color: #006699;">", idPosition: "</span> + idPosition + <span style="color: #006699;">", endPosition:"</span> + endPosition);

  lastGesture = strGesture;
  context.removeGesture(strGesture); 
  context.startTrackingHands(endPosition);
}

<span style="color: #cc6600;">void</span> onProgressGesture(<span style="color: #cc6600;">String</span> strGesture, <span style="color: #cc6600;">PVector</span> position, <span style="color: #cc6600;">float</span> progress)
{
  <span style="color: #7e7e7e;">//println("onProgressGesture - strGesture: " + strGesture + ", position: " + position + ", progress:" + progress);</span>
}

<span style="color: #7e7e7e;">// -----------------------------------------------------------------</span>
<span style="color: #7e7e7e;">// Evenement du clavier</span>
<span style="color: #7e7e7e;">// -----------------------------------------------------------------</span>
<span style="color: #cc6600;">void</span> <span style="color: #006699;">keyPressed</span>()
{
  <span style="color: #cc6600;">switch</span>(<span style="color: #006699;">key</span>)
  {
    <span style="color: #7e7e7e;">// si j'appuie sur la barre espace</span>
    <span style="color: #7e7e7e;">// j'active / je desactive l'affichage en miroir</span>
  <span style="color: #cc6600;">case</span> <span style="color: #006699;">' '</span>:
    context.setMirror(!context.mirror());
    <span style="color: #cc6600;">break</span>;
  }

  <span style="color: #cc6600;">switch</span>(<span style="color: #006699;">keyCode</span>)
  {
    <span style="color: #7e7e7e;">// si j'appuie sur la fleche gauche</span>
    <span style="color: #7e7e7e;">// je deplace mon point de vue vers la gauche</span>
  <span style="color: #cc6600;">case</span> <span style="color: #006699;">LEFT</span>:
    rotY += 0.1f;
    <span style="color: #cc6600;">break</span>;
    <span style="color: #7e7e7e;">// si j'appuie sur la fleche droite</span>
    <span style="color: #7e7e7e;">// je deplace mon point de vue vers la droite</span>
  <span style="color: #cc6600;">case</span> <span style="color: #006699;">RIGHT</span>:
    rotY -= 0.1f;
    <span style="color: #cc6600;">break</span>;
    <span style="color: #7e7e7e;">// si j'appuie sur la fleche haut</span>
    <span style="color: #7e7e7e;">// je deplace mon point de vue vers le haut</span>
  <span style="color: #cc6600;">case</span> <span style="color: #006699;">UP</span>:
    <span style="color: #cc6600;">if</span> (keyEvent.isShiftDown())
      zoomF += 0.01f;
    <span style="color: #cc6600;">else</span>
      rotX += 0.1f;
    <span style="color: #cc6600;">break</span>;
    <span style="color: #7e7e7e;">// si j'appuie sur la fleche bas</span>
    <span style="color: #7e7e7e;">// je deplace mon point de vue vers le bas</span>
  <span style="color: #cc6600;">case</span> <span style="color: #006699;">DOWN</span>:
    <span style="color: #cc6600;">if</span> (keyEvent.isShiftDown())
    {
      zoomF -= 0.01f;
      <span style="color: #cc6600;">if</span> (zoomF &lt; 0.01)
        zoomF = 0.01;
    }
    <span style="color: #cc6600;">else</span>
      rotX -= 0.1f;
    <span style="color: #cc6600;">break</span>;
  }
}</pre>

[Télécharger le sketch et ses fichiers liés][13]

Pour aller plus loin



Une application la Kinect pour la détection de mouvements et la génération de formes : [TUIOKINECT][14]

&nbsp;

#### Pour aller plus loin

Une [bonne page][15] (en français) expliquant les différents pilotes et possibilités de la Kinect.

 [1]: http://docilestudio.fr/ESA/wp-content/uploads/2012/03/kinect.png
 [2]: http://en.wikipedia.org/wiki/Kinect
 [3]: http://vimeo.com/26532792
 [4]: http://vimeo.com/22878568
 [5]: http://vimeo.com/33616193
 [6]: http://vimeo.com/17073934
 [7]: http://vimeo.com/24665893
 [8]: http://vimeo.com/29845142
 [9]: http://vimeo.com/29723511
 [10]: http://docilestudio.fr/ESA/wp-content/uploads/2012/04/Hands3d.zip
 [11]: http://docilestudio.fr/ESA/wp-content/uploads/2012/04/Hands3d_sphere.zip
 [12]: http://docilestudio.fr/ESA/?p=111964 "2DGM – Reel | Virtuel | Actuel – 3D & son / Synesthésie : Cours technique n°2"
 [13]: http://docilestudio.fr/ESA/wp-content/uploads/2012/04/Hands3d_objLoader.zip
 [14]: http://tuiokinect.googlecode.com/files/TuioKinect-0.1-mac.zip
 [15]: http://sebastien.warin.fr/2011/01/05/1067-kinect-introduction-openkinect-openni-nite/

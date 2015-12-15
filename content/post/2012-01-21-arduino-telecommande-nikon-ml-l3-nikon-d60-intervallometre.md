---
title: Arduino + télécommande Nikon ML-L3 + Nikon D60 = Intervallomètre
author: jules
layout: post
date: 2012-01-20
categories:
  - Non classé
  - Projets
  - RDV Hacklab
  - Ressources
---
[Soirée Labx Bordeaux][1] from [Jul][2] on [Vimeo][3].

<!--more-->

Si vous avez un reflex, une télécommande Nikon, une carte Arduino et une pièce de 2 cents, vous pouvez avoir un Intervallomètre ! Et cela sans modifier aucun de ces objets de manière irréversible .

La fonction intervallomètre permet de prendre des photos à intervalle régulier, et ainsi de faire de jolis time lapses comme celui-ci, réalisé avec le système décrit ci-après

<img src="http://leblogdeponeymort.free.fr/images/intervalometre_1.JPG" alt="" border="0" />

Le principe : on remplace la pile de la télécommande par les contacts d&rsquo;une carte Arduino qui envoie du courant à intervalle régulier, et on bloque l&rsquo;interrupteur de la télécommande fermé. L&rsquo;appareil photo déclenche quand la télécommande envoie un signal.

**1. Programmer l&rsquo;Arduino pour qu&rsquo;elle envoie du courant sur un port à intervalle régulier.**

Le code est d&rsquo;une complexité extrême : il s&rsquo;agit du célèbre « blinking LED » qui sert à tester la carte Arduino, et dont on change les valeurs .

\___\___\___\___\___\___\___\___\___\___\___\___\___\___

void setup() {

pinMode(13, OUTPUT); // j&rsquo;ai pris le port 13 car il est muni d&rsquo;un LED sur l&rsquo;arduino UNO , ça permet de contrôler que le courant passe bien en sortie de carte
  
}

void loop() {
  
digitalWrite(13, HIGH); // set the LED on
  
delay(2000); // on déclenche pendant 2 secondes
  
digitalWrite(13, LOW); // set the LED off
  
delay(8000); // on attend pendant 8 secondes
  
}

\___\___\___\___\___\___\___\___\___\___\___\___\___\___\___\___\___\___

On peut régler l&rsquo;intervalle en millisecondes . Le temps de contact doit être de 2 seconde pour que le contact se fasse correctement.
  
Une fois le code chargé sur la carte, vous pouvez passer à le partie « hardware »

**2. Transformer une pièce de monnaie en pile**

Maintenant que l&rsquo;arduino envoie du courant comme on veut, il faut connecter les bornes à la place de la pile. On la remplace par une pièce de 2 cents sur laquelle on aura soudé la polarité -. une fois la soudure effectuée, on scotche le + le long de la tranche en faisant bien attention à l&rsquo;isoler de la pièce sous peine de court circuit (voir illustration)
  
Dans la télécommande, le contact + est au fond et le – sur une face de la pile. Ajustez en fonction et bonne chance&#8230;
  
Le contact du + est tout au fond du logement , pas facile de plaquer le fil dessus.

<img src="http://leblogdeponeymort.free.fr/images/intervalometre_4.JPG" alt="" border="0" />
  
_La polarité – soudée sur la pièce et le + disposé autour le la pièce mais bien isolé_

**3. Bloquer l&rsquo;interrupteur et c&rsquo;est parti**

Il vous reste à insérer votre pseudo-pile et à bloquer l&rsquo;interrupteur à l&rsquo;aide d&rsquo;un pince à linge, de scotch ou d&rsquo;un assistant

<img src="http://leblogdeponeymort.free.fr/images/intervalometre_2.JPG" alt="" border="0" />
  
_Et voilà c&rsquo;est parti !_

**4. Autres possibilités :**

à partir du même montage, vous pouvez faire plein d&rsquo;autres choses, il vous suffit de changer le programme de l&rsquo;arduino. Vous pouvez par exemple conditionner le déclenchement à l&rsquo;activation d&rsquo;un capteur (, cellule photosensible, contact&#8230;) Vous pouvez aussi synchroniser plusieurs appareils photos avec la même télécommande (pour faire de la photo 3D&#8230;)

 [1]: http://vimeo.com/35284752
 [2]: http://vimeo.com/user9548225
 [3]: http://vimeo.com

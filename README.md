# Projecteur-Leds-asservi  <p align="right"> <img width="80" height="80" src="https://github.com/ThomasMoun/Projecteur-Leds-asservi/blob/main/Logo_ENSEA.svg.png"> </p>

<p align="center"> 
 <img width="250" height="250" src="https://github.com/ThomasMoun/Projecteur-Leds-asservi/blob/main/projecteur%20de%20r%C3%AAve.png">
 
 <img width="200" height="340" src="https://github.com/ThomasMoun/Projecteur-Leds-asservi/blob/main/IMG_20230501_220601.jpg">

 <img width="200" height="250" src="https://github.com/ThomasMoun/Projecteur-Leds-asservi/blob/main/Untitled.png">

|Etudiants en charge du projet |       
|:----------------------------:|       
|Tom Charbonneau               |       
|Baptiste Gilles               |       
|Ludovic Sercy                 |
|Thomas Mouneyrat              |
|Bassem Barakat                |
|Quentin de La Chaise          |

|Professeurs encadrants le projet |
|:-------------------------------:|
|Nicolas Papazoglou               |
|Laurent Fiack                    |

*N.B. : Ce README s'adresse aux futurs ensearques qui auront le courage de s'aventurer sur le sinueux chemin de ce projet ; il s'adresse aussi aux électroniciens curieux et avide de découvertes ; enfin il s'adresse évidemment à nos chers professeurs.*

## Introduction

Le projecteur Leds est, comme son nom l'indique, un structure permettant l'éclairage coloré et la mise en valeur de décor dans différents évènements plus ou moins festifs.
Un projecteur de ce type doit pouvoir bouger suivant différents axes (2 dans notre cas Tilt-Pan) et le zoom ainsi que la couleur de la lumière émise doivent être ajustables.
Ce projet s'inscrit donc dans les domaines de la lumière et du son, et serait en théorie piloté par un régisseur lors d'évènements.
Ainsi, à la fin de la conception de ce projet on doit pouvoir être capable de le faire bouger en choisissant la direction et l'axe de mouvement, on doit aussi être en mesure de changer la couleur et de centrer la lumière sur des zones précises (tout cela via un unique contrôleur).

## Organisation du dépôt git

Dans ce dépôts git vous trouverez une branche pour chaque grand axe de travail du projet : 
 - Les différentes carte (Led, Alimentation, contrôle etc)
 - La partie mécanique (modélisation 3D)
 - Les parties drivers (moteurs, leds)
 
Dans la branche principale vous trouverez aussi les schémas utilisés dans ce README.

*Logiciels utilisés*

|Conception/Design PCB | Modélisation 3D | Programmation des cartes et définition des connexions |
|:--------------------:|:---------------:|:-----------------------------------------------------:|
|KiCAD 6.0             |Onshape          |STM32CubeIDE et STM32CubeMX                            |

|Alternatives possibles                                                                          |
|:----------------------------------------------------------------------------------------------:|
|Eagle (PCB)     /    Solidworks (onshape a l'avantage d'être gratuit)                           |

|Gestion de projet                                                                               |
|:----------------------------------------------------------------------------------------------:|
|Google Drive/Github/Redmine de l'école                                                          |                   

## Schémas d'architecture Hardware et/ou Software

_<p align = center>Schéma structurel associé à la structure 3D</p>_

<p align="center">
  <img width="700" height="500" src="https://github.com/ThomasMoun/Projecteur-Leds-asservi/blob/main/archiglobale.jpg">
</p>

*<p align =center>Schéma général d'architecture</p>*

<p align="center">
  <img width="1000" height="630" src="https://github.com/ThomasMoun/Projecteur-Leds-asservi/blob/main/Diagramme%20Architecture%20V2.jpg">
</p>

*<p align = center>Schéma commande et puissance</p>*

<p align="center">
  <img width="800" height="480" src="https://github.com/ThomasMoun/Projecteur-Leds-asservi/blob/main/Archi%20pcb%20puissance%20et%20commande.jpg">
</p>

Ce schéma nous a permis de synthétiser "qui a quel rôle" en commande et en alimentation


## Documentation

*Ce qui marche/Ce qui marche pas*

Général : 

-La carte d'alimentation semble fontionner bien qu'elle n'est pas été testé avec tout, elle possède tous les composants nécessaire à l'alimentation de l'ensemble
- Le réglage en intensité (via le contôleur) de la led issu du pcb "led test" fonctionne, le code qui passe par le DMX est donc correcte.
- Le mouvement du projecteur via le pilotage des moteurs n'est pas fiable, le code et des poids structurels sont à revoir.
- L'architecture du PCB de contrôle est correcte dans l'ensemble et possède tous les composants nécéssaires au bon fonctionnement du projecteur. Le régulateur linéaire est à déplacer car, suite à un soucis d'impression de via, on a rencontré des difficultés à le souder correctement empêchant son fonctionnement. Certaines capacités de découplage sont potentiellement à rapprocher du projecteur.

Point mécanique : 

Certaines des pièces sont à revoir pour la conception, il s'agit d'un prototype et il comporte beaucoup de défaut.

Défaut:
- Axe difficile à monter sur la pièce en U, il faut tordre la pièce en U pour insérer l'axe.
- Pas de buté axial sur l'axe
- tolérance des trous pas assez grands
- Solidité des axes des engrenages faibles
- Cage des engrenages trop rigide
- Montage des vis de la tête de projecteur impossible à cause de la structure en U qui empêche son accès
- Les vis de maintien entre la base et la partie tournante du projecteur étaient difficilement accessibles
    
## TODO
 
- Il reste une grosse partie programmation notamment pour le processeur de la carte de contrôle (centralisation des codes) et le pilotage des moteurs
- La carte Leds complète a été designé, il faut l'imprimer une première fois et la tester
- Reste à traiter le ventilateur ou un système de refroidissement de la struture (ventilo prévue dans la carte d'alimentation)
- Dans la lignée du ventilo, à voir pour un changement de matériau pour la structure ; l'ensemble est amené à chauffer
- Le zoom est une partie qu'on a très peu traité faute de temps, le projet de base est d'utiliser des lentilles placées devant chaque leds et qu'on viendrait éloignées ou rapprochées des leds pour zoomer. Le mouvement se ferait au travers d'un axe interne au projecteur (prévu dans la structure

Point mécanique :
 
Amélioration :
-Tolérance plus grande
-Utiliser un filetage dans les trous au lieu de vis + écrou
-Certains axes pas assez dimensionner pour résister aux contraintes
-Faire une structure moins rigide pour la cage des engrenages


## Deux points techniques importants    
        
### Le DMX

Afin de pouvoir contrôler le projecteur, nous utilisons une table DMX. Celle-ci est composée de différents curseurs, chacun pouvant contrôler un paramètre différent du projecteur. Les paramètres sont les suivants :
- le TILT
- le PAN
- le Zoom
- la couleur

Certains paramètres nécessitent plusieurs curseurs. En effet, un curseur permet de sélectionner une valeur entre 0 et 255. Pour les moteurs, par exemple, comme nous désirons pouvoir faire une rotation du projecteur de 540 degrés de tilt et 270 degrés de pan, et que les moteurs pas a pas choisi (NEMA 17) ont une résolution de 1,8 degré par pas et que nous désirons implémenter le microstepping pour plus de précision, il est nécessaire d’utiliser plusieurs curseurs. De la même manière, pour contrôler les LEDs, il faut choisir avec des curseurs indépendants les valeurs de Rouge, Vert, Bleu et Blanc.

La table DMX utilise le protocole DMX 512, cela permet d’utiliser un seul câble avec paire différentiel pour contrôler un grand nombre de paramètres et d’appareils. La trame DMX se présente de cette manière :
![image](https://user-images.githubusercontent.com/103488210/235350326-baa313e5-2bbd-46fc-8914-1c06e459d739.png)
*<p align =center>Trame DMX</p>*

Chaque trame commence par un Break puis un MAB. Il y a ensuite 513 canaux DMX, le premier est le start code qui est utilisé pour paramétrer certains appareils mais inutile dans notre cas. Les 512 canaux suivants contiennent les valeurs prises par les différents curseurs.

Le signal étant transmis sur une paire différentielle, il est nécessaire pour le décoder de le passer sur un seul fil. Pour cela, on utilise un transmitter RS-485. 
Afin de décoder la trame DMX, on utilise de l’UART. Il est nécessaire de détecter le début de la trame pour pouvoir connaitre les valeurs correspondantes aux bons curseurs. Pour cela on utilise une Frame Error de l’UART.

Une fois ces valeurs récupérées, on peut les transmettre aux drivers moteurs et LEDs pour effectuer les actions demandées.

### Driver Moteur

#### Le fonctionnement

L’objectif était de réaliser des drivers pour des moteurs pas a pas capable de faire du microstepping. Chaque driver est composé d’un STM32G0 en communication avec le PCB de contrôle qui lui fourni la position à atteindre. Le STM32 pilote ensuite des ponts en H associés aux deux phases du moteur.

Les moteurs choisis sont des NEMA 14 et NEMA 17, chacun de ces moteurs possède des caractéristiques différentes mais comme ils seront asservi en courant, on peut conserver le même driver et le programmer différemment pour éviter que ceux-ci ne grillent. Ces moteurs sont composés de deux phases A et B, ce sont les enroulements des moteurs. Ces enroulements permettent de créer un champ magnétique permettant d’orienter le stator dans la direction voulu.

<p align="center">
  <img width="200" height="200" src="https://user-images.githubusercontent.com/103488210/235354097-10496f05-6dda-4fd5-b31a-a278e0426909.png">
</p>
<p align =center><i>Phases du moteur</i></p>

Pour alimenter les enroulements, on utilise deux ponts en H ce qui nous permet de choisir le sens d’alimentation de chacune des phases.

<p align="center">
  <img width="400" height="260" src="https://user-images.githubusercontent.com/103488210/235354172-c46dd3ff-c34e-45e5-b294-985c387eb7b2.png">
</p>
<p align =center><i>Les deux états du pont en H</i></p>

En full step, ces phases sont alimentées alternativement dans un sens puis dans l’autre de manière à orienter le stator dans l’axe des enroulements.

<p align="center">
  <img width="163" height="199" src="https://user-images.githubusercontent.com/103488210/235354499-5270fc2f-ace9-4570-9945-cd7c2c8435de.png">
</p>
<p align =center><i>Ordre d'alimentation des phases</i></p>
<p align="center">
  <img width="308" height="307" src="https://user-images.githubusercontent.com/103488210/235354505-55667830-1796-4f3c-b822-adf4271f562d.png">
</p>

Pour le microstepping, on alimente simultanément les deux phases à différentes intensités afin d’aligner le rotor entre deux phases, cela nous permet d’augmenter le nombre de pas. On utilise le wave microstepping pour garder un couple constant au cours du temps.

<p align="center">
  <img width="166" height="319" src="https://user-images.githubusercontent.com/103488210/235354714-e61bf3ab-ad12-4880-b54f-28569bbd0e25.png">
</p>
<p align =center><i>Ordre d'alimentation des phases pour le Half-Step</i></p>
<p align="center">
  <img width="258" height="258" src="https://user-images.githubusercontent.com/103488210/235354720-fb71bb0a-ac08-456f-b14a-ac82e394dc53.png">
</p>

Pour un plus grand nombre de pas, on obtient les formes de courant suivantes :
<p align="center">
  <img width="258" height="258" src="https://user-images.githubusercontent.com/103488210/235354949-74e5b5ff-c1f8-4a50-82d9-bb2c70b8ac83.png">
</p>

On peut donc relier le courant au numéro du pas désiré par les équations suivantes :
- Ia = sin(num_pas * 360/32) * Imax
- Ib = cos(num_pas * 360/32) * Imax

Afin de d’asservir le courant arrivant dans chaque phase, on utilise un hacheur et un détecteur de courant pour chaque phase.

### Améliorations

- Le PCB n’ayant pas fonctionné, il est nécéssaire d’effectuer de nouveaux tests.
- Afin de pouvoir asservir le courant, il faut soit rajouter un hacheur soit dissocier les deux cotés de chaque pont en H pour pouvoir l'utiliser en hacheur (cette methode nécéssite des sorties PWM supplémentaires sur le STM32).
- Choisir mieux les composants pour qu'ils aient des tensions d'alimentation similaires afin de réduire le nombre de tensions d'alimentations différentes sur le driver.

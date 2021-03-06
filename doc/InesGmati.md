![Polytech](http://www.polytechnice.fr/jahia/jsp/jahia/templates/inc/img/polytech_nice-sophia.png)

Compte rendu Ines Gmati

# Séance1:20/01/2017

Pendant la première séance on a mis en place les idées pour le projet.

![résumerS01](https://s20.postimg.cc/yqi849nfx/S01.png)


# Séance 2:12/01/2018
On a approfondi les calculs pour la determination du vent réel.
Les calculs sont affiché sur la photo qui suit:

![photoCalcul](https://s20.postimg.cc/5mpeuruod/calcul_VR.jpg)

# Séance 3:19/01/2018

on a regardé le fonctionnement d'un GPS UBLOX: [cliquez ici pour le lien](https://playground.arduino.cc/UBlox/GPS)

# Semaine de vacances: du 29/01 au 3/02

Le 31/01 je suis allée à Cannes pour naviguer et partager les idées du projet avec l'entraîneur du Yach Club de Cannes.
Ci-dessous une photo d'un compas régulariser pour les compétitions de laser:
![photoCompas](https://s20.postimg.cc/bdept6eot/compas.jpg)

Le 03/02: naviguation avec le groupe de laseristes de Cannes. Debrief sur les courses faites avec l'entraineur.

# journée du 14/02

Récupération du matériel:
![ photoMatos](https://s20.postimg.cc/h3fv0xr0t/photo_Matos.jpg)

# journée du 20/02
j'ai soudé 3 résistances, 2 connecteurs RJ11 et 4 connecteurs blancs sur la platine groove.

1ère familiarisation avec l'anémomètre.
Problème dans la convertion **de** changement d'état **à** force de vent en noeuds. 
Un lien qui donne des idées sur comment faire cette convertion:[ link01](https://forum.arduino.cc/index.php?topic=92398.0)
le programme trouvé sur cette page ne nous convient pas.

information  utile: 1 km/h ---> 0,539957 Knots

1er code utilisé:
<pre><code>
  void setup() { 
  pinMode(13, OUTPUT); 
  pinMode(2, INPUT); 
  Serial.begin(9600);
  }
  // Boucle principale:
  void loop() { 
  int BP = digitalRead(2); // Lecture du capteur 
  Serial.println(BP);
  if (BP == LOW) {
  digitalWrite(13, HIGH); // Allume la Led
  Serial.println("HIGH");
  }
  else {
  digitalWrite(13, LOW); // Eteind la Led
  Serial.println("LOW");
  } 
  }
</pre></code>  

2éme code utilisé:
<pre><code>
  int impulsion_anemometre = 3;           //pin pour compter le nombre d'impulsion 
int compt = 0;  //fonction pour compter le nombre d'impulsiofloat vitesse = 0;  //vitesse du vent
float valeur = 2.4;
void setup()
{
  Serial.begin(1200);
  attachInterrupt(1,compteur,RISING); //fonction pour compter le nombre d'interruption
}


void loop()
{
   delay(1000);
   compt = 0;
   Serial.println("vitesse du vent en km/h: 0");
 }
void compteur()
{
    compt++;
    Serial.println(compt);
    vitesse = valeur*compt; //calcul de la vitesse du vent
[}    delay(1000);
    Serial.print("vitesse du vent en km/h:");
    Serial.println(vitesse);
    delay(1000);
 }
</pre></code>

# Séance 4:22/02/2018

recherche de code plus performant pour la girouette et l'anémomètre. Pas de résultat satisfaisant pour l'instant.

# Séance 5: 08/03/2018

Le code de l'anémomètre ne renvoit pour l'instant que les changement d'état. On cherche toujours à afficher la vitesse du vent en km/h.
En ce qui concerne la girouette les valeurs afficher correspondent aux variations de la résistance, on essaie encore de transformer 16 intervalles de réssistance différents à leurs caps respectifs (ex:[0,23]--> Nord).

# Semaine de vacances du 19/04 au 27/04

On cherche à obtenir la vitesse et la direction dans laquelle le bateau avance à partir du code du GPS. On va partir ces informations à partir de la longitide et de la latitude.

Le code du GPS est sur le readme.
En rentrant le longitude et la latitude donné par le GPS on retrouve bien notre position. Le GPS marche comme il faut.
![testGPS](https://s20.postimg.cc/trnqo71bh/Test_Gps.png)

Essaies sur le module bluetooth et un smartphone: difficulté à connecté le module HC-06 au smartphone. Mais le module marche(la led s'allume une fois le circuit sous tension).

Nouveau code pour la girouette qui devrait donné les 360°. Mais le résultat n'est pas concluant pour l'instant.

Autres lien intéressant pour la girouette: [link02](http://cactus.io/hookups/weather/anemometer/davis/hookup-arduino-to-davis-anemometer-software) 

On a consacré une journée pour mettre en commun les programmes des différents outils.
Le code est fonctionnel, mais il nous reste quelques lignes à programmer dans le but d'afficher clairement le résultat qu'on cherche.

# 3 semaines avant le rendu

J'ai rencontré beaucoup de problème avec le module bluetooth. J'ai essayée d'utiliser les branchement et les code qu'on a vu en cours mais cela n'a pas voulu marcher. J'ai donc décider d'essyer avec un autre branchement et un autre code.
Le module marche et on a réussi à associer notre module au téléphone. 
Le résultat de l'application écrit sur app inventor ressemble à cela pour l'instant:

![photoAppli](https://s20.postimg.cc/o66z60m8d/Screenshot_2018-04-24-23-18-50.png)





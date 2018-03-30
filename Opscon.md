# A.1 Aperçu
Le présent document décrit le système TDGB qui est un jeu de style *tower defense*
dans lequel des oursons en gélatine attaqueront le joueur qui devra se défendre en construisant
des tours possédants des habiletés spécifiques afin d'éliminer ces oursons en gélatine. Le système sera
construit pour être compatible avec la plateforme Android uniquement.

# A.2 Document de concept opérationnel

## A.2.1 Portée
Le document présentera et analysera le système TDGB en définissant les prérequis
pour l'exécution des tâches qui seront effectuées par l'utilisateur ainsi qu'en définissant
le vocabulaire utilisé entre le client et l'équipe de développement.

### A.2.1.1 Identification
Le système est connu sous le nom de *Tower Defence Gummy Bear* (TDGB).

### A.2.1.2 Aperçu du document
Le document s'adresse au gestionnaire, à l'équipe de développement ainsi qu'aux possibles investisseurs.
Autrement dit, il s'adresse à toute personne reliée au projet cherchant de l'information sur le système.

### A.2.1.3 Aperçu du système
Voir Figure 1 à l'annexe en A.2.9

## A.2.2 Documents de référence

## A.2.3 Système actuel
Puisque les développeurs programmeront la totalité du système, nous baserons notre analyse
sur une application déjà existante, soit Realm Defense, disponible sur le *App Store* et le
*Google Play Store*.

### A.2.3.1 Passé du système, objectifs et portée
Realm Defense est un jeu stratégique disponible sur les plateformes Android et IOS.
L'application a été développée par Babeltime, une compagnie basée à San Mateo
en Californie. Le but de Realm Defense est d'offrir un jeu de stratégie du type *tower defense* sur les appareils mobiles.

### A.2.3.2 Politiques et contraintes opérationnelles
Outre le fait que l'application doit fonctionner sur Android et IOS, il serait peu utile
de s'interroger sur les politiques et les contraintes opérationnelles de Realm Defense,
puisque l'équipe de développeurs de TDGB ne sera pas dans le même environnement de travail
que l'équipe de Babeltime.

### A.2.3.3 Description du système actuel
L'application Realm Defense est un jeu stratégique de style *Tower Defense*. Les joueurs
doivent construire des tours pour faire face à plusieurs vagues d'ennemis. L'application
n'a pas de mode multijoueur, puisque l'utilisateur joue contre des ennemis contrôlés
automatiquement, mais elle comporte plusieurs fonctionnalités permettant de compétitionner
contre d'autres joueurs pour l'obtention du meilleur score. Ces fonctionnalités nécessitent
une connexion internet puisque des requêtes doivent être envoyées pour aller chercher les
résultats des autres joueurs.

Les fonctionnalités nécessitant une connexion internet sont les suivantes: le tournoi,
la ronde sans fin et le mode arcade. Le tournoi est un défi quotidien entre tous les
utilisateurs de l'application. Le joueur obtenant le meilleur score de la journée
obtient une récompense. La ronde sans fin est une grande carte dans laquelle le
joueur affronte une vague sans fin et plus le temps avance, plus la récompense lorsque la
partie se terminera sera grande. Le mode arcade permet à l'utilisateur de jouer un mode spécial
dans lequel il se défend en utilisant des armes plutôt que des tours. Il doit choisir l'arme
et frapper les ennemis qu'il veut attaquer. Comme les récompenses changent souvent,
elles sont stockées sur le serveur de l'application. De ce fait, ces fonctionnalités
nécessitent que le joueur soit constamment connecté.

### A.2.3.4 Mode d'opération du système actuel
Les modes d'opérations de Realm defense sont le mode navigation du menu principal, le mode jeu,
le mode pause et le mode rapport de fin de partie. Le mode navigation du menu principal permet
au joueur de choisir parmi les options suivantes : commencer une partie, afficher les tours
disponibles, ajuster les réglages et visiter le magasin de l'application. Le mode jeu permet
au joueur de construire et vendre des tours, d'affronter des ennemis, de mettre le jeu en pause
et d'augmenter la vitesse de jeu. Le mode pause permet au joueur de recommencer la partie,
d'ajuster les réglages et quitter la partie. Le mode rapport de fin de partie permet à
l'utilisateur d'observer son score et de le comparer avec celui des autres joueurs.

### A.2.3.5 Classes d'utilisateurs et autre personnel impliqué
* Joueur/utilisateur
* Développeur/testeur

#### A.2.3.5.1 Structure organisationnelle
Non-applicable. La structure organisationnelle de Babeltime n'est pas utile puisque les
développeurs travailleront dans un environnement différent.

#### A.2.3.5.2 Profil des classes utilisateurs
Les deux classes utilisateurs connus de Realm Defense sont l'utilisateur/joueur et le
développeur/testeur. La première est la classe qui utilisera l'application et s'amusera
à se défendre contre des vagues d'ennemis. La deuxième est la classe qui conçoit et
développe l'application. Elle a également pour mandat de la tester, la déployer et la maintenir.

#### A.2.3.5.3 Interactions entre les classes utilisateurs
Les testeurs informent les développeurs lors de la détection d'un bogue. Aussi, les développeurs
ajoutent et modifient les fonctionnalités existantes que le joueur utilise.

#### A.2.3.5.4 Autre personnel impliqué
Non-connu.

### A.2.3.6 Environnement de support
Une option dans le jeu permet d'écrire une lettre à l'équipe de support de Babeltime.

## A.2.4 Justifications et nature du changement
Les jeux actuellement sur le marché sont axés sur les graphiques et n'ont qu'un nombre limité
de fonctionnalités.

### A.2.4.1 Justifications pour le changement
Le but du système TDGB est de développer un jeu axé sur la jouabilité et le nombre de
fonctionnalités ainsi que le respect de la vie privée des utilisateurs. De plus, les
développeurs souhaitent offrir une application hors-ligne, c'est-à-dire qui ne nécessite pas
de connexion internet constante.

### A.2.4.2 Description des changements désirés
L'équipe souhaite offrir une application dans laquelle les réglages et la construction se
font dans un menu. Elle désirerait aussi offrir un générateur de carte permettant aux utilisateurs
de jouer des niveaux différents. De plus l'équipe de développement voudrait offrir une expérience de
jeu totalement hors-ligne.

### A.2.4.3 Priorités parmi les changements
* Fonctionnalités essentielles:
	- Carte(gui) ayant les dimensions x cases par y cases:
		- possède un chemin qui a possède les caractéristiques suivantes:
			+ Commence à la première rangée du haut de l'écran et se termine dans la dernière rangée
				du bas de la carte
			+ On ne peut pas construire de tours sur le chemin
			+ Le chemin est libre de tout obstacle pour permettre aux ennemis de circuler librement
	- Chaque case aura sur l'écran les dimensions suivantes: 120 points et la résolution du jeu est de 1080 x 1920 points par pouce (PPP)
	- Menu du haut indiquant les ressources du joueur
	- Menu du bas offrant les options de construction au joueur
* Les tours que le joueur peut construire possèdent les caractéristiques suivantes:
	- Elles ont une portée (détermine la distance à laquelle peut attaquer un ennemi)
	- Elles ont un dommage (détermine les dégâts qu'elles peuvent faire pour chaque attaque réussie sur un ennemi)
	- Elles ont une durée de construction
	- On peut abandonner la construction d'une tour durant sa construction et obtenir 100% des ressources utilisées pour sa construction
* Lors qu'on appuie sur une certaine partie de l'écran, un menu s'affiche au joueur lui permettant de :
	- Faire une nouvelle partie
	- Sauvegarder
	- Options(contenant le volume, la luminosité, etc.)
	- Quitter

* Fonctionnalités désirables:
	- Les tours:
		* Elles ont un niveau (détermine le niveau de la tour puisqu'elles possèdent plusieurs
		niveaux et ont un effet différent en fonction du niveau de la tour -> plus de dégâts,
		une animation différente, etc.)
		* Elles ont une durabilité

* Fonctionnalités optionnelles:
	- Générateur de cartes (avec des options à déterminer)
	- Générateur d'ennemis (pour permettre à l'utilisateur de personnaliser l'expérience davantage)

### A.2.4.4 Changements considérés mais exclus
Nous avons abandonné l'idée d'implémenter la fonctionnalité multijoueur, car cela
nécessiterait des connaissances trop avancées et un budget trop élevé pour le client.
De plus, nous avons également considéré rendre compatible notre jeu sur plusieurs plateformes, mais les
défis techniques et la jouabilité ne serait pas la même sur un ordinateur de bureau que sur un appareil
mobile et nous avons décidé d'abandonner cette option. 

### A.2.4.5 Suppositions et contraintes
Le projet sera réalisé en faisant appel à trois développeurs qui effectueront 135 heures chacun pour un
total de 405 heures sur ce projet. Le projet doit être livré au client au plus tard le 23 avril 2018
avant minuit. Les technologies utilisées pour faciliter le développement de l'application sont le
framework Corona SDK, le langage de programmation Lua et le gestionnaire de sources Git. Un nombre de
fonctionnalités de 10 au minimum sera exigé pour chaque développeur faisant partie du projet et chacun
d'entre eux sera rémunéré à un taux fixe.

## A.2.5 Concepts pour le système proposé
Le but du système est de donner une nouvelle saveur à un style de jeu bien implanté: le style de jeu *tower defense*.

### A.2.5.1 Passé, objectifs et portée
Le système n'a pas de passé puisqu'il s'agit d'une nouvelle application. Les objectifs
du système est d'innover au niveau des fonctionnalités et de les livrer en maximisant la
valeur ajoutée pour le client.

### A.2.5.2 Politiques et contraintes opérationnelles
L'ensemble des fonctionnalités doivent être remises pour le 23 avril 2018. Les contraintes
budgétaires nous forcent à limiter la distribution de l'application. C'est pourquoi, elle
ne sera pas disponible pour les tablettes ayant le système d'exploitation Android et IOS. N'ayant pas de fonds pour
l'utilisation de logiciels payants, l'application sera développée uniquement avec des logiciels
gratuits. De plus, l'équipe de développement n'a que 405 heures à investir et elle travaillera
sous le système d'exploitation Windows.</p>

### A.2.5.3 Description du système proposé
L'application sera développé pour pour Android 4.0.3(nom de code: Ice Cream Sandwich) et les versions ultérieures.
Elle supportera l'API de niveau 15 d'Android et les APIs ultérieures. L'application aura des performances élevées, puisqu'elle possède des graphiques et
animations simples en deux dimensions et cela fera en sorte qu'elle n'exigera pas beaucoup de ressources
du système pour bien fonctionner. L'application ne nécessitera pas de connexion internet pour fonctionner.
Le joueur affrontera seul un adversaire avec une intelligence artificielle simplistique et essaiera de le vaincre.

### A.2.5.4 Modes d'opération
Le mode *navigation menu* permet à l'utilisateur d'offrir les options de création de partie, de visionnement
des scores et de configuration de l'application.
Le mode *période de construction* laisse une période de temps prédéfinie à l'utilisateur pour construire des
tours et autres options avant le mode *période de bataille,* qui lui consiste à affronter les ennemis présents
sur la carte.
Il y a aussi le mode *pause*, permettant d'arrêter temporairement toute activité de l'application lors
de la période de construction ou de la *période de bataille*, que ce soit déclenché volontairement par
l'utilisateur à l'aide de l'interface ou automatiquement lors de la mise en arrière-plan de l'application
pour passer à une autre application sur son appareil mobile.
Le mode *rapport de fin de partie* permet à l'utilisateur de consulter ses statistiques reliées à la partie
jouée, contenant notamment le score et propose à l'utilisateur de retourner au mode *navigation menu*.
Finalement, le *mode test* sera seulement disponible pour les testeurs et servira pour la maintenance en
affichant à la console les informations pertinentes à propos des événements qui se sont produits durant
l'exécution de l'application.

### A.2.5.5 Classes d'utilisateurs et autre personnel impliqué <a name="ClasUtil2"></a>
* Utilisateur
* Utilisateur premium
* Développeur/Testeur

#### A.2.5.5.1 Structure organisationnelle
L'équipe de développement est composé d'un chef d'équipe et de deux développeurs.

#### A.2.5.5.2 Profil des classes utilisateurs
L'utilisateur de base a une limitation sur le nombre de fonctionnalités disponibles et ne peut
pas fermer les publicités. L'utilisateur premium doit payer un montant mensuel pour avoir accès
à toutes les fonctionnalités et pouvoir fermer les publicités. De plus, l'utilisateur premium
a accès à un niveau de difficulté supérieur et commence la partie avec plus de ressources pour
la construction des tours.

#### A.2.5.5.3 Interactions parmi les classes utilisateurs
Non-Applicable

#### A.2.5.5.4 Autre personnel impliqué
Non-Applicable

###  A.2.5.6 Environnement de support
Une option dans le menu sera disponible pour rapporter un bogue à l'équipe de développement.
Mentionnons aussi que l'application sera déployée sur le *Google Play Store* exclusivement.

## A.2.6 Scénarios opérationnels
* Avant la partie :
	- Naviguer le menu
	- Ajuster les réglages
	- Commencer une partie
* Durant la partie :
	+ Période d'invasion ennemie
		- Accélérer la vitesse de défilement du temps
		- Accéder au menu
		- Mettre en pause
	+ Période entre les vagues d'ennemis
		- Construire une tour
		- Recycler une tour
		- Accéder au menu
		- Mettre en pause
* Après la partie :
	- Quitter vers le menu
	- Recommencer une partie

## A.2.7 Sommaire des impacts
Le présent système offrira l'opportunité à plusieurs développeurs de mettre à profit leurs compétences et
de développer une application avec des ressources limitées pour la plateforme Android. Les membres de
l'équipe de développement pourront mettre à profit leurs compétences et les affiner en cours de projet.

### A.2.7.1 Impacts opérationnels
* Aucun changement dans le budget opérationnel.

### A.2.7.2 Impacts organisationnels
Le présent projet procurera trois emplois pour 3 développeurs et permettront à ces individus
de développer leurs compétences avec le langage de programmation Lua.

### A.2.7.3 Impacts durant le développement
L'équipe de développement se rencontrera deux fois par semaine. Une rencontre se fera en personne
et l'autre se fera par vidéo conférence, typiquement le lundi ou le vendredi.

## A.2.8 Analyse du système proposé


### A.2.8.1 Bénéfices
* Amélioration de la jouabilité.
* Performance accrue ( graphiques minimalistes ) .
* Respect de la vie privée ( Pas de collecte de données ).
* Possibilité de payer pour éviter les publicités.
* Application de base gratuite.

### A.2.8.2 Inconvénients et limitations
Le budget limité nous contraint d'offrir à nos futurs clients des graphiques minimalistes,
car l'équipe se compose avant tout de développeurs qui ont très peu de connaissances en infographie.
De plus, nous avons fait le choix de ne pas supporter de mode multijoueur, car l'équipe ne possède pas
d'infrastructure serveur. Il faut également mentionner que le jeu a une faible portabilité,
car il est conçu pour la plateforme Android uniquement. Toutefois, on peut techniquement l'utiliser
sur d'autres plateformes comme Windows, Linux et IOS, mais il n'a pas été optimisé pour être utilisé
sur ces plateformes pour des raisons de budget. De plus, le fait que transposer l'application sur un
ordinateur de bureau se ferait au détriment de conditions de jeu. Enfin, l'équipe de développement est limitée
par le framework de base de Corona qui est gratuit.

### A.2.8.3 Autres possibilités considérées
L'utilisation de *Xamarin* a été considéré pour offrir une application multi-plateforme aux
joueurs, mais une plus grande connaissance du langage C# et F# aurait été nécessaire afin
de pouvoir profiter pleinement de cet environnement de développement. Les développeurs qui
ont pris en charge le projet n'ont pas ces compétences donc c'est pour cette raison que
cette option a été écartée.

\newpage

## A.2.9 Annexe

![Diagramme de séquence du système TDGB](diagramme_sequence.png)


## A.2.10 Glossaire
* API: Interface qui permet à une application d'utiliser les services d'une autre application sans en
	connaître le fonctionnement précis pour arriver à offrir ce service.
* Environnement de développement intégré(EDI): Logiciel composé d'outils qui permettent au
	programmeur de pouvoir rapidement modifier, compiler et
* exécuter du code dans un langage compatible avec l'EDI sans devoir connaître les commandes qui
	sont normalement nécessaires pour compiler du code.
* Graphiques: Tout ce que l'utilisateur voit lorsque le logiciel fonctionne et qui est associé au
	logiciel. Cela exclut les fenêtres des autres applications
* et les différents processus engendrés par le système d'exploitation qui n'a rien à voir avec le
	logiciel exécuté.
* Jeu *tower defense*: Jeu dans lequel le joueur doit construire des tours qui empêchent les unités
	ennemies de pouvoir se rendre à un certain endroit afin de remporter la partie.
* Jouabilité: Facilité avec laquelle un nouvel utilisateur peut s'adapter au logiciel en fonction
	de son aisance avec ce genre de logiciel.
* Plateforme: Environnement sur lequel un logiciel peut être installé et exécuté
	(Windows, Linux, Mac OS X).
* Portabilité: Capacité à un logiciel à pouvoir être utilisé sur plusieurs plateformes en ayant des fonctionnalités
	similaires d'une plateforme à une autre.
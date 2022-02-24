---
title: PodcastScience - Alpha Go
date: 2022-02-24
lastmod: 2022-02-24
author: nicotupe
# avatar: /img/author.jpg
# authorlink: https://author.site
feature_image: https://i.imgur.com/OHy8o7I.jpg
# images:
#   - /img/cover.jpg
categories:
  - DOSSIER
tags:
  - alphaGo
numeros: 
  - 3
draft: false
---

Pour tout savoir sur le fonctionnement d'Alpha Go.

<!--more-->

Cet article est une version écrite du dossier de [PodcastScience](https://www.podcastscience.fm/emission/2021/12/31/podcast-science-460-alpha-go-lalgo-qui-bat-lego/). En particulier il est a destination de personne dont la très grande majorité n'a jamais joué au Go voire n'a jamais entendu parler de ce jeu, soyez indulgents sur les généralités!

{{< rawhtml >}}
<iframe src="https://embed.acast.com/607aec11b1d7373173d66907/61d443a42c941a001275d929?subscribe=false" frameborder="0" allow="autoplay" width="100%" height="110"></iframe>
{{< /rawhtml >}}

En mars 2016, un ordinateur a battu à 4 victoires contre 1 Lee Sedol, l’un des plus grand joueur de Go de l’époque. Bien que peu connu dans l’occident, le jeu de Go est un jeu très populaire en Asie. Il était considéré depuis longtemps comme un étalon de l’intelligence humaine que les ordinateurs seraient bien loin de dépasser. 

Vingt ans après [la victoire de Deep Blue contre Kasparov aux échecs](https://en.wikipedia.org/wiki/Deep_Blue_versus_Garry_Kasparov), on pouvait se douter qu’un tel exploit arriverait tôt ou tard pour le jeu de Go. Mais la plupart des spécialistes pensaient qu’on était encore à des décades d’un tel algorithme.

Alors pourquoi le jeu de Go est si différent des échecs pour les ordinateurs et comment a fait Alpha Go pour battre Lee Sedol et maintenant, dans ses dernières itérations, tous les joueurs de la planète?
C’est ce que nous allons voir dans ce dossier.

## Le go, un jeu difficile?

Le Go est un très vieux jeu, tellement vieux qu’il est dûr de savoir de quand il date exactement. Il a probablement été créé en chine environ en -700 soit plus de 1000 ans avant les échecs! Le go est aujourd’hui très populaire en Corée, au Japon et se développe en Europe.

Quand j’ai l’occasion de demander à quelqu’un s’il connaît le Go, j’ai toujours le même genre de réponse : 

> “Je connais de nom, c’est le jeu super difficile avec des pierres blanches et noires c’est ca?”

C’est intéressant de s’arrêter sur cette remarque pour voir ce qu’est un jeu simple et un jeu difficile. En fait, le go fait parti des jeux de sociétés aux règles les plus simples qui existent : 

-  A son tour on pose une pierre n’importe où sur une des cases vides du plateau.
- Si un ensemble de pierres est entouré par des pierres de l’autre couleur elles sont capturées.
- On a pas le droit de jouer dans un endroit où l’on serait immédiatement capturé (suicide)
- Il y a aussi une règle pour éviter les boucles infinies : on a pas le droit de faire un coup qui remet le plateau dans sa position précédente.

Si vous y réfléchissez, ce n’est vraiment pas beaucoup de règles par rapport à la plupart des jeux qu’on considère comme “simples”. Prenez par exemple les échecs auxquels la plupart d’entre vous ont déjà joué : 

- Le pion bouge en avançant une case à la fois devant lui…
- …sauf quand il capture où il peut bouger en diagonale
- …et sauf pour son premier mouvement où il peut bouger de deux cases
- Le cavalier? oui il peut sauter par dessus les autres pièces.
- Je vous ai parlé du roque?

Bref, les échecs ont des règles beaucoup plus complexes sur le papier. 

Et pourtant, même les personnes qui connaissent les deux jeux trouvent en général le Go plus intimidant. Ce n’est pas forcément au nombre de règles qu’on peut juger l’impression que l’on a d’un jeu. 

Par exemple, aux échecs, les mouvement différent de chaque pièces donne une indication au joueur sur leur role, leur utilité. 

Ou encore le but du jeu est beaucoup plus simple à appréhender aux échecs qu’au Go. Aux échecs, le but du jeu est de tuer le roi, au Go c’est d’avoir le plus de “territoire” (ne me lancez pas sur la définition de territoire…).

Mais alors comment se fait-il qu’un jeu avec beaucoup moins de règles ait été considéré beaucoup plus compliqué à battre que les échecs? C’est parce que les machines n’ont pas les mêmes problèmes que nous…

## Combinatoire

La première très grosse différence pour un ordinateur est le nombre de coups et de parties possibles. Un Goban (le plateau du jeu de Go) est un carré de 19x19 cases (en fait ce sont des intersections mais ça joue le même rôle que des cases). Pour vous donner une idée concrète, c'est un peu plus grand que 4 échiquiers mis les un à coté des autres!

![Imgur](https://i.imgur.com/AvoLteF.png)

Et comme si cela ne suffisait pas, comme je vous le disait, au go on passe ses tour à poser des pierres donc au début il n’y a rien sur le plateau. Si bien que le nombre de possibilités de jeu est très très grand : Pour le premier coup on a 361 possibilités, après deux coups il y a 62000 possibilités, après 5 coups, il y a 1000 milliards de possibilités. 

Pour comparaison encore, aux échecs après 5 coups on a “que” 24 millions de possibilités soit de l’ordre de 100 000 fois moins de possibilités.

Les parties sont aussi plus longues en moyenne. Si aux échecs une partie dure en moyenne entre 40 et 80 coups, au Go on est plus autour des 150 à 200 coups. Et à chaque tour il y a en moyenne 250 coups valides, soit près de 10 fois plus qu’aux échecs.

Comparer de la sorte qui a la plus grosse a peu d’intérêt pour des humains. Par exemple, le Gomoku (une sorte de puissance 4 qui se joue sur un Goban) possède a peu près les mêmes caractéristiques que le go mais pour autant n’est pas réputé comme étant aussi complexe. Ou encore *"aller acheter du pain le matin"* contient infiniment fois plus de possibilités mais a l’air d’être considéré plus simple par la plupart des humains (ils sont bizarres ces humains). Mais cela donne une idée sur la possibilité de tester toutes les possibilités pour choisir la meilleure. 

C’était déjà impossible pour le gros d’une partie d’échecs (les fin de parties sont moins combinatoires) mais cela devient absolument impossible au go.

Malgré tout, cet aspect combinatoire est quelque chose qui a justement été approché pour les échecs par Deep Blue. Grâce à une base de données de parties de professionnels, il avait réussi à battre l’humain. Le Go a un autre problème de taille : l’évaluation d’une partie en cours.

## Qui gagne?
La plupart des jeux, en particulier les jeux modernes et jeu vidéo ont ce qu’on appelle des *"boucles de rétroaction"*, c’est a dire qu’un joueur sait en général très rapidement si ce qu’il fait est bien ou pas : 

-  il marque des points
- le boss clignote rouge
- Le héros perd de la vie
- etc.

Ces boucles de rétroaction permettent aux joueurs de très rapidement apprendre et s’adapter à ce qu’essaie de lui faire faire le jeu. C’est aussi une caractéristique des jeux très utile pour les ordinateurs : un ordinateur peut, à tout moment, évaluer si ce qu’il fait est bien ou pas.

Les échecs ne dérogent pas à la règle, les joueurs expérimentés ont pour habitude de donner un nombre de points à chaque pièce : un pion vaut 1 point, un cavalier 3 points, une tour 5 points, une dame 9 points. Si bien qu’un joueur sait que s’il perd un cavalier pour prendre une tour, il y gagne. Ça permet aussi d’évaluer la partie : si un joueur a plus de points que l’autre, il est en train de gagner. 

D’ailleurs en général les bon joueurs abandonnent quand ils se font prendre la dame ayant pris trop de retard. Ce n’est pas une science exacte, mais ça donne une bonne idée.

Au Go, il n’y a pas vraiment ce genre de choses ou du moins pas de manière aussi palpable et concrète que dans les jeux vidéos ou les échecs. On pourrait penser qu’à l’image des échecs le nombre de pierres capturées peut jouer ce rôle de proxy. Mais dès que les joueurs deviennent expérimentés, très peu de pierres sont capturées et en général ces captures font partie d’une stratégie plus globale si bien que leur nombre a peu d’importance.

Pour savoir où ils en sont dans la partie, les joueurs essaient d’évaluer le territoire qu’ils auront en fin de partie en fonction de ce qu’ils pensent qu’ils ont mis de côté, ce qu’ils ont en potentiel en prenant en compte que ça peut être envahi, etc. 

Par exemple en fin de partie, un joueur même débutant arrive a dire où sont les territoires : 

![Imgur](https://i.imgur.com/JfVkF60.gif)

Mais en début de partie c'est déjà beaucoup plus compliqué : 

![Imgur](https://i.imgur.com/HN5Ienj.png)

C’est particulièrement sujet à l’interprétation! Autant dire l’horreur pour une machine essayant d’automatiser cela.

En résumé on a donc un jeu avec beaucoup de possibilités et une capacité limitée à évaluer une partie en cours de jeu... L’enfer pour des algorithmes qui essaient d’apprendre en testant plein d’options et en évaluant au fur et à mesure leur efficacité. 

C’est en partie ce qui explique que le go était vu comme un jeu loin d’être approchable par un algorithme.

## L’algorithme le plus bête

Devant quelque chose d’aussi compliqué, on se demande bien par où commencer. Alors Imaginons que vous découvrez ce jeu aujourd’hui, comment choisiriez vous vos coups? 

Si vous êtes un matheux comme moi, probablement au hasard! C’est justement par là qu'on va commencer.

Au cœur d’AlphaGo il y a un procédé qui a l’air stupide et qui pourtant donne déjà de bon résultats. Comme on vient de le voir, il est impossible de tester toutes les possibilités avant de choisir comment jouer au Go, il y a trop de possibilités. Alors, comme on n’a aucune raison de choisir un coup plutôt qu’un autre, on peut en essayer quelque uns au hasard puis voir ce que ça donnerait et choisir parmi ceux-là le plus prometteur.

Il reste un problème, c’est bien beau d’avoir sélectionné des coups potentiels mais comme on a vu aussi, il est très compliqué d’évaluer la qualité des dits coups en milieu de partie. En fait, l’idéal serait de tester quelques parties en partant de ces positions et de voir si l’on gagne ou l’on perd…

Vu qu’on ne sait pas bien jouer, il nous reste à jouer ces parties au hasard (chaque joueur joue au hasard à son tour) plusieurs milliers de fois et on compte le nombre de fois où l’on gagne. Le coup qui donnera le plus de victoires sera probablement meilleur que les autres!

Résumons comment fonctionnerait un tel algorithme : 

- quand c’est à lui de jouer, l’ordinateur choisit au hasard plusieurs coups potentiels
- pour chacun de ces coups il joue plusieurs centaines de parties au hasard
- il choisit au final le coup pour lequel il gagne le plus de parties

Aussi étrange que cela paraisse, ce type d’algorithme donne déjà des résultats assez acceptables pour peu qu’on essaie beaucoup de coups et beaucoup de parties : il arrivera à battre des amateurs jusqu’à un niveau avancé (environ 1d).

Utiliser le hasard quand on n’a pas la puissance ou le temps de faire tous les calculs est une méthode assez classique, c’est ce qu’on appelle la [méthode de Monté Carlo](https://en.wikipedia.org/wiki/Monte_Carlo_method). Ici, comme on ne peut pas tester toutes les possibilités, on en teste un certain nombre au hasard pour approcher le résultat.

Cet algorithme bien qu’étant un bon début ne permet pas de battre des bons amateurs alors comment l’améliorer? C’est en utilisant le Deep Learning [dont on a déjà parlé](https://www.podcastscience.fm/dossiers/2016/03/01/deep-learning/) que Deep Mind est parvenu à atteindre le niveau des professionnels.


## Les réseaux de neurones

Assez rapidement quand on joue à un jeu, on a des intuitions, on apprend de nos parties passées ce qui ressemble à un bon ou un mauvais coup. Comme on l’avait vu dans l’épisode sur le Deep Learning, on a depuis de nombreuses années des outils pour que les machines puissent apprendre avec beaucoup d’exemples. 

L’un de ces outils qui a explosé au début des années 2010 sont les réseaux de neurones convolés. En particulier ils sont très efficaces pour apprendre à détecter des choses dans les images. Il paraît donc être une bonne idée de les utiliser pour apprendre à mieux jouer au Go du fait de l’aspect très visuel de l’estimation d’une partie. Et comme il y a d’énormes bases de données de parties de professionnels disponibles, il y a largement assez de données pour permettre aux machines d’apprendre.

Lors de l’épisode sur le deep learning, je n’était pas rentré dans les détails sur comment on permet à une machine d’apprendre. Et avec tous les articles expliquant de les ordinateurs sont sur le point de dominer l’humanité, on peut croire que c’est facile à faire… En fait, ce dont on parle peu quand on parle de machine learning c’est a quel point mettre en œuvre ce type d’apprentissage peut être complexe et relativement artisanal.

Contrairement à ce que les délires de certains entrepreneurs laissent croire, les ordinateurs sont aujourd’hui très stupides et ils ne comprennent que les nombres. Par contre ils calculent vite et on a depuis l’explosion de l’apprentissage profond des méthodes pour leur faire apprendre via des exemples visuels. 

On ne va pas rentrer dans tous les détails ce serait trop long et trop fastidieux mais je vais vous donner quelques exemples de ce qu’a mis en place Deep Mind pour réussir à apprendre de parties de professionnels.

D’abord ils ont décomposé les parties en chaque coup : on a donc des millions d'état de plateau plateaux et on sait si, à la fin, cette position a mené à une victoire ou une défaite. Et comme victoire et défaite ne veut rien dire pour une machine, ils vont donner une note à ces plateaux : 1 quand ils ont mené à une victoire, -1 quand ils ont mené à une défaite. Tous ces plateaux et leur résultats constituent une "base d’aprentissage", la collection d’exemple sur laquelle la machine peut apprendre.

En se contentant de faire ça, les ordinateurs ne parvenaient pas d’apprendre suffisamment vite. Deep Mind a alors ajouté des informations pour aider la machine. Au lieu de se contenter de lui donner l’état du plateau, ils lui donnent aussi certaines informations que tous les joueurs calculent à chaque tour, par exemple : 

- le nombre de pierres qu’il manque pour capturer chaque groupe de pierres (les libertés)
- combien de pierres sont dans chaque groupe de pierres
- est-ce que cette pierre est prise ou risque d’être prise dans l’un des piège basiques bien connus
- etc.

Ce qu’il faut retenir ici c’est que contrairement à ce qu’on pourrait croire, beaucoup d’algorithmes d’apprentissages obtiennent des résultats impressionnants grâce à ce type d’”aide” à la compréhension fourni par les humains.

A ce stade et grâce à cet apprentissage, Deep Mind avait un algorithme capable pour une position de plateau de lui donner une note. Pour les curieux, Alpha Go contient en fait pas mal de variantes : un réseau qui donne une note à un coup, un réseau qui va prédire la qualité de tous les coups du plateau d’un coup, etc.

## De la décision un peu plus éclairée

Revenons à notre recherche de Monte Carlo. Vous vous rappelez qu’on choisissait des coups au hasard puis on jouait au hasard pour voir le meilleur coup. Grâce à ces réseaux entrainés, on peut maintenant faire quelque chose de plus malin.

Au lieu de choisir les coups au hasard, Alpha Go va utiiser un réseau de neurone pour choisir quel coup tester. Il ne va pas choisir forcément celui qui a la meilleur note selon le réseau mais va être influencé par ça. Imaginons que le réseau donne 30% chances de victoires à un coup et 70% chances à un autre, l’algorithme va avoir alors 3 chances sur 10 de choisir le premier et 7 chances sur 10 de choisir le deuxième.

Puis pour chacun de ces coups, AlphaGo va toujours faire des parties pour voir quel est le coup le plus intéressant. Mais au lieu de jouer au hasard AlphaGo va utiliser un réseau de neurone pour jouer. Comme on a besoin de faire énormément de parties pour évaluer ces coups, Deep Mind a entrainé un réseau de neurone plus simple et un peu moins bon pour qu’il soit suffisamment rapide pour faire ces parties test en grand nombre.

A ce stade on a un algorithme qui ressemble beaucoup à la manière de jouer d’un humain : 

- Grâce à son expérience il choisit des coups qui ont l’air intéressant
- Rapidement il essaie de jouer les coups qui suivent pour voir ce que ça donne
- Il choisit alors le coup qui a l’air d’amener au meilleur résultat.

On a alors un algorithme qui a appris grâce à un grand nombre de parties de professionnels. Le problème est qu’en copiant des professionnels on va avoir du mal à les dépasser, comment, alors que la machine a appris à copier des coups de professionnels, pourrait-elle réussir a jouer mieux qu’eux? Après tout ce n’est qu’une pale copie, un best of des meilleurs humains…. 

## Renforcement
A partir de cette base on a un algorithme qui joue très bien au Go, qui commence à être capable de battre certains professionnels. Pour aller au dela et dépasser ses pairs, l’algorithme va devoir progresser par lui même.

C’est dans ce but qu’AlphaGo utilise une dernière méthode du monde de l’apprentissage : le renforcement. AlphaGo va jouer un grand nombre de parties contre lui-même et tâcher de s’améliorer au fur et à mesure. Ce procédé parait assez basique mais est en général très compliqué à mettre en oeuvre.

AlphaGo joue des parties contre lui même et va renforcer les parties du réseau de neurones qui l’ont poussé à jouer les coups gagnants et pénaliser ceux qui l’ont mené à la défaite.

Voila l’algorithme qui a battu Lee Sedol 4 jeux à 1 et pour l’anecdote la défaite d’AlphaGo était du à un bug corrigé plus tard! Si vous voulez en savoir plus sur cette victoire je vous recommande l'excellent documentaire ci-dessous disponible gratuitement sur Youtube.

{{< rawhtml >}}
<iframe width="560" height="315" src="https://www.youtube.com/embed/WXuK6gekU1Y" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture" allowfullscreen></iframe>
{{< /rawhtml >}}

Si vous voulez voir AlphaGo en action, vous pouvez télécharger [Katrain](https://github.com/sanderland/katrain/releases) et visualiser tout ce que j'ai raconté.

![Imgur](https://i.imgur.com/OHy8o7I.jpg)

Dans l'image ci-dessus vous voyez en vert quelques coups sélectionnés par l'algorithmes avec leur scores associés. En haut à droite vous voyez aussi une estimation du score de chaque joueur à chaque coups

## AlphaZero

Un an après ce succès, Deep Mind a publié AlphaZero, une toute nouvelle version d’AlphaGo. Cette version change radicalement la structure d’AlphaGo et remet en cause pas mal de choses de ce que j’ai pu vous dire.

Là où AlphaGo avait besoin de plusieurs réseaux de neurones et de concepts de Go pour réussir à être entrainés (taille des groupes, libertés, etc.), AlphaZero n’utilise qu’un seul réseau de neurone et n’a aucune de ces règles implémentés.

Là où AlphaGo avait besoin d’une base de 30 millions de coups de professionnels pour commencer à apprendre par lui même, AlphaZero a appris a jouer au Go tout seul, sans aucun exemple de parties humaines.

Après quelques jours d’entrainements, AlphaZero est non seulement capable de battre les humains mais en fait écrase AlphaGo : il bat AlphaGo 100 parties à 0.

Et comme il n’a besoin d’aucune donnée humaine, cet algorithme a été utilisé pour les échecs, le shogi, etc. C’est aujourd’hui l’un des algorithme les plus performants au monde dans tous les jeux de sociétés classiques.

AlphaGo et AlphaZero ont marqué une étape importante des développement en intelligence artificielle. AlphaGo montre que pour faire marcher ce type d’algorithme, on a souvent besoin, de manière artisanale, d’ajouter beaucoup de couches de fonctionnement pour aider la machine à apprendre. 

AlphaZero a quand a lui montré que même sans données humaines, un algorithme pouvait atteindre dans certains cas un niveau sur-humain.


> “While the Baroque rules of Chess could only have been created by humans, the rules of Go are so elegant, organic, and rigorously logical that if intelligent life forms exist elsewhere in the universe, they almost certainly play Go.”
― Edward Lasker

## Biblio

Cet article a été principalement basé sur le livre [Deep Learning and the game of Go](https://www.amazon.com/Deep-Learning-Game-Max-Pumperla/dp/1617295329)
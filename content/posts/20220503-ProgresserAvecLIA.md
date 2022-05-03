---
title: Progresser avec l'AI
date: 2022-05-03
author: nicotupe
feature_image: https://i.imgur.com/OHy8o7I.jpg
tags:
  - alphaGo
numeros: 
  - 4
draft: true
---

Ces derniers jours j'ai l'impression d'avoir passé un palier de niveau. On dit souvent que la progression au Go ne se fait pas linéairement mais par palier et j'ai enfin eu l'impression de débloquer quelque chose pour passer un palier que j'avais autour du niveau 8k OGS. 

Pour ce faire, une des choses qui m'a beaucoup aidé est l'IA. Je profite de cet article pour vous partager comment j'ai utilisé cet outil pour améliorer mon jeu.

## Un premier exemple

Avant de rentrer dans les détails pratique, un premier exemple qui pourra illustrer les erreurs que je faisais et que je fais moins aujourd'hui.

{{< ogs "43404437" 76 >}}

Dans cette partie, je suis noir, je suis un peu en retard selon l'IA mais à mon niveau c'est un retard qui peut largement se rattraper. Et surtout j'ai une énorme influence au centre qui va commencer à être compliquée à envahir. Du coup ce qui devait arriver arriva, Blanc décide de rentrer en utilisant une des nombreuses faiblesses de mon centre.

Il y a une semaine, mon réflexe aurait été :

> C'est chez moi ici! Je dois tuer cette pierre au plus vite!

Et cela finissait toujours pareil, je perdais quelques pierres à la guerre et le groupe envahisseur vivait "chez moi". Grâce à l'IA j'ai complètement changé ma manière d'approcher ce genre de situation, si bien que voici les 3 coups suivants : 

{{< ogs "43404437" 79 >}}

Au lieu d'attaquer le groupe envahisseur, j'ai d'abord réparé mes faiblesses les plus proches afin de ne pas lancer une attaque trop facile pour blanc.

Bien sur à ce stade Blanc a trois pierres, il sera plus dur à tuer mais, et c'est un autre enseignement de l'IA, mon objectif reste de faire plus de points que l'adversaire, du coup si au lieu de le tuer je peux concrétiser mon influence ça pourrait me faire gagner la partie.

Et comme je ne suis pas une machine, je fais justement une grosse erreur plus tard : 

{{< ogs "43404437" 111 >}}

A ce stade je m'obstine à vouloir tuer l'envahisseur en laissant de coté l'énorme faiblesse que ce groupe approchait à gauche et ça n'a pas manqué, j'ai perdu la partie.

## Travailler avec l'IA

L'IA est beaucoup critiquée dans le Go comme n'aidant pas à progresser. En fait je pense que c'est un peu plus compliqué que ça : il faut apprendre à lire l'IA et surtout oublier vite les séquences qu'on ne comprend pas ou qui jouent sur une lecture à 50 coups.

De mon coté le plus intéressant avec actuellement est de comprendre quels sont les coups les plus importants sur le goban et j'ai réalisé que je me trompais souvent. Je crois que certains parlent de direction de jeu mais il me semble que c'est plus que ça, ça peut aussi être dans des situations d'invasion plus tard dans le jeu.

La chaine "râler autour du goban" présente très bien cette approche dans cette vidéo : 

{{< youtube "_Hptf-mfE2A" >}}


Pour ce faire j'ai eu deux approches, la première consiste à revoir les parties avec ai-sensei ou avec OGS et de regarder quels coups propose l'IA (ai-sensei a ce sujet est meilleur vu qu'il donne plusieurs propositions). Mais au lieu de regarder des situations critiques où il y a un seul bon coup, je regardais plutôt des situations de fuseki ou de mid-game pour comprendre la philosophie de jeu.

L'autre approche consiste à jouer en utilisant l'IA. Pour ça j'ai joué sur "The Conquest of Go" contre une IA et en parallèle ai lancé Katago. A chaque coup, je réfléchis à ce que je veux jouer puis consulte l'IA pour savoir ce qu'elle en pense. Cela demande un peu de rigueur pour ne pas copier bêtement l'IA mais apprend beaucoup de choses. On découvre que ses "mauvais coups" ne sont pas forcément ceux qu'on croit, je vous fait un florilège plus bas. 

Cette deuxième approche, plus complexe à mettre en place, apprend pas mal de choses parce qu'on est "dans le jeu" alors que dans les review c'est parfois compliqué de se remettre dans une situation donnée.

Puis, histoire d'appliquer ce que je comprennais, j'ai enchainé les parties d'OGS et mine de rien ça aussi ça aide beaucoup!


## Ce que j'ai appris

Ce que j'ai appris durant ces cessions va paraitre très bête mais j'ai dans l'idée que ça va raisonner avec des joueurs de mon niveau! Et oui, c'est ce que plein de joueurs dan vous auront dit...

### L'influence ce n'est pas du territoire

On commence par du évident et pourtant...

{{< ogs "42654490" 18 >}}

Il m'arrive souvent d'avoir deux murs sur chaque coté du plateau (là ce ne sont pas encore des murs mais vous voyez l'esprit). Et blanc ne peut pas s'empécher de venir jouer au milieu, "chez moi". Alors mon premier réflexe est d'aller jouer proche de lui pour l'"attaquer". L'IA, surtout en début de jeu, considère ça comme plutôt un mauvais coup. Ca dépend bien sur des circonstances mais l'idée que j'en ai retenu plusieurs choses : 

- la pierre est là, c'est trop tard pour décréter que c'est ton territoire
- cette pierre sera très dure voire impossible à tuer
- si tu commences un combat maintenant, les séparations de territoires vont se décider à tes dépend
- le plateau est grand et beaucoup d'autres endroits sont vides

Alors aussi étonnant que ça paraisse, dans ce genre d'"invasion" de la zone d'influence, je laisse maintenant en général mon adversaire tranquile et profite de ce coup gote pour aller prendre une autre partie du goban.

### Le meilleur moyen de tuer un groupe c'est de l'encercler

Encore un conseil un peu étrange, après tout go voudrait dire "jeu de l'encerclement"... Mais à chaque fois que j'avais une invasion, j'avais tendance à l'attaquer de près et à essayer de l'encercler tout en lui empéchant de faire des yeux.

En général l'IA ne fait pas ce genre d'attaque directe mais de ce que j'en comprend va plutôt : 
- renforcer ses faiblesses locales
- continuer de prendre des points, si la bataille est au centre et qu'il reste du bord ou des coins elle ignore tout simplement l'invasion
- profiter de ce groupe faible pour aller fermer ou prendre de l'influence dans une zone qui ira, in fine, vers un encerclement du groupe

Ce dernier point est celui qui est le plus efficace avec les joueurs agressifs (coucou Fox) qui ont tendance à se créer plein de coupes, la plupart du temps on réussi à les forcer à choisir entre la survie d'un des deux groupes faibles.

### Un groupe fort peut devenir faible très vite

Ceci est *LA* chose qui me fait perdre le plus de parties. Il faut bien comprendre qu'il existe 3 statuts de groupes : 
- Vivant : le groupe a deux yeux, vraiment, pas des yeux potentiels si on joue
- Fort : le groupe a plein de moyen de s'échapper ou de faire ses yeux
- Faible : c'est la merde

Et le passage de groupe fort a faible peut aller très très vite. Pire, quand cela arrive c'est souvent un passage de *fort* à *presque mort*. Le cas classique est lors d'une attaque où tellement obsédé par tuer ou entourer un groupe on ne se rend pas compte que l'un de ses groupes est devenu très faible. 

Ci-dessous blanc joue un coup qui menace de séparer des groupes mais surtout en faisant ça il donne l'opportunité à noir de séparer un de ses groupes et d'en faire un groupe faible ou plutôt presque mort...

{{< ogs "43343337" 122 >}}

### Jouer simple et solide c'est bien

Enfin, la chose la plus importante que j'ai appris c'est que jouer simple et solide c'est bien. Quand j'hésite entre un hane, un tobi, un kema, etc. Soit vos groupes sont fort et faire avoir une coupe locale n'est pas grave et surtout apporterait quelque chose stratégiquement sinon je choisis la solution la plus solide. Non pas qu'une coupe va tout changer mais répéter régulièrement cette pratique ne va amener qu'à des problèmes plus tard, quand vous aurez besoin de groupes fort pour appuyer une attaque.








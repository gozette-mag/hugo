---
title: Une vue du 9x9
date: 2022-02-24
lastmod: 2022-02-24
author: Nicotupe
# avatar: /img/author.jpg
# authorlink: https://author.site
feature_image: https://i.imgur.com/K9xLq4L.png
# images:
#   - /img/cover.jpg
categories:
  - DOSSIER
tags:
  - 9x9
numeros: 
  - 3
mathjax: true
# nolastmod: true
draft: false
---

Comme beaucoup le savent, je suis un grand fan du format 9x9 pour le go et je vous propose ici une nouvelle façon de voir l'ouverture et le jeu au 9x9 en s'imaginant sur un 19x19.

<!--more-->

## Premier coup

L'AI a tendance à favoriser le Tengen pour commencer. Malgré tout beaucoup de joueurs avec qui j'ai discuté n'aiment pas trop jouer si loin des bords, en particulier ils préfèrent jouer un peu plus près au hoshi (comme au 19x19) ou au Komoku.

{{< sgf "(;PB[Black]PW[White]SZ[9];B[dd];B[fg])" 2 >}}

Mais alors pourquoi l'AI et beaucoup de bons joueurs aiment tant le Tengen? Pour le comprendre je vous propose de mettre quatre 9x9 cote à cotes et de regarder ce que ces ouvertures donnent sur un 19x19.

Pour le Hoshi ça donne ça : 

{{< sgf "(;PB[Black]PW[White]SZ[19];B[dd];B[nn];B[dn];B[nd])" 4 >}}

Autant dire que si le coin haut gauche est bien approché, les autres coins sont très libres pour une attaque... Et en ouvrant au san-san c'est encore pire : 

{{< sgf "(;PB[Black]PW[White]SZ[19];B[cc];B[mm];B[cm];B[mc])" 4 >}}

Alors qu'un tengen semble un compromis plus intéressant

{{< sgf "(;PB[Black]PW[White]SZ[19];B[ee];B[oo];B[eo];B[oe])" 4 >}}

## Réponse

D'ailleurs si on regarde les réponses de blanc c'est encore plus intéressant. Pour l'ouverture au Tengen, l'AI suggère de répondre au milieu, par exemple : 

{{< sgf "(;PB[Black]PW[White]SZ[9];B[ee];W[ec])" 2 >}}

Sur un 19x19 cela fait sens, on approche deux coins à la fois.

{{< sgf "(;PB[Black]PW[White]SZ[19];B[ee];W[ec];B[oo];W[om];B[eo];W[em];B[oe];W[oc])" 100 >}}

## Joseki

Un "joseki" du 9x9 selon l'AI est la séquence suivante (on reste a peu près au même taux de victoire) : 

{{< sgf "(;PB[Black]PW[White]SZ[9];B[ee];W[ec];B[gd];W[eg];B[cd];W[cf])" 100 >}}

Et sur un 19x19 cela donne ça : 

{{< sgf "(;PB[Black]PW[White]SZ[19];B[ee];W[ec];B[gd];W[eg];B[cd];W[cf];B[oe];W[oc];B[qd];W[og];B[md];W[mf];B[eo];W[em];B[gn];W[eq];B[cn];W[cp];B[oo];W[om];B[qn];W[oq];B[mn];W[mp])" 100 >}}

Il faut bien sur imaginer que les 4 gobans ne sont pas connectés et regarder plutôt la situation autour des coins mais est-ce que vue comme cela la situation parait plus équilibrée que sur le 9x9?

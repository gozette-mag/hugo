---
title: "[Glossaire] Un groupe"
date: 1900-05-03
author: raleur
feature_image: /img/cover.jpg
tags:
  - glossaire
numeros: 
  - 4
draft: false
---



Un _groupe_ est une pierre, ou un ensemble de pierres qu’on ne souhaite pas sacrifier durant la partie. 

<!--more-->

Ici la pierre de noir en carré peut déjà être considérée comme un groupe. 

{{< static_sgf "(;FF[4]CA[UTF-8]GM[1]SZ[19]AP[maxiGos:7.01];B[cd];W[dd];B[ce];W[de];B[cf];W[df];B[bg];W[cg];B[rb];W[qb];B[qc];W[pb];B[qd];W[pc];B[pd];W[nc];W[lc];B[qf];B[ql];W[qn];B[qo];W[pn];B[po];W[nn];B[pp];W[ro];B[pq];W[qp];B[qr];W[qq];B[rr];W[jq];B[cq];W[dq];B[cp];W[dp];B[bn];W[do]TR[rf][sf][sg][rg][ri][si][sh][rh][rj][sj]SQ[ql]CR[nn][pn][qn][ro][qp][qq])" 38 false >}}

Stratégiquement parlant, noir n’acceptera pas de la sacrifier car elle lui permet d’obtenir une zone de points en triangle en plus de ne pas laisser le groupe blanc – en rond – se renforcer trop facilement.

### Groupe faible

Un groupe _faible_ est un groupe qui ne possède qu’une seule direction – deux sauts d’une intersection sans toucher de pierres adverses – ou, une seule base de vie. Ici le groupe noir en carré est un groupe faible, il ne possède qu’une capacité de base de vie qui est un équivalent à la direction.

{{< static_sgf "(;FF[4]CA[UTF-8]GM[1]SZ[19]AP[maxiGos:7.01];B[cp];W[cq];B[dp];W[dq];B[eq];W[er];B[fq];W[fr];B[gr];W[gp];B[fp];W[gq];B[ep];W[fo];B[hr];W[iq]SQ[fq][fp][ep][dp][cp][eq]TR[cm])" 16 false >}}


> N.-B. Lorsqu’un groupe est faible, il devient impératif de le protéger en trouvant de nouvelles directions.


### Groupe stable

Un groupe stable est un groupe qui possède au minimum deux directions, ou bien une direction et une capacité de base de vie. Ici noir possède deux directions, deux sauts d’une intersection sans toucher de pierres adverses vers le Nord et l’Est.

{{< static_sgf "(;FF[4]GM[1]CA[UTF-8]SZ[19]ST[0]AP[maxiGos:7.01];B[dq];W[bq];B[ep];W[co];B[fp];W[dn];B[en];W[gp];B[fn];W[go];W[gr];W[ip];W[dl]SQ[dq][ep][fp][fn][en]TR[fl][fj][hm][jm])" 16 false >}}


> N.-B. Lorsqu’un groupe est stable il est possible de tenuki – jouer ailleurs –, mais parfois on peut préférer rajouter au groupe une direction supplémentaire afin d’éviter une attaque trop sévère ou trop profitable à l'autre couleur. 

> P.-S. Un groupe ne peut pas posséder plus de quatre directions – les directions correspondant aux points cardinaux du plateau –. Si vous en trouver davantage, dans ce cas vérifiez si certaines directions ne vont pas vers la même zone du plateau.


### Groupe fort

Un groupe fort est un groupe qui possède deux yeux, ou bien un groupe dont on peut assurer avec certitude qu’il possède deux yeux - on parle parfois de groupe vivant -. Ici noir est un groupe fort, bien qu’on ignore la manière, on est certain qu’il possède deux yeux dans la zone marquée de triangles.

{{< static_sgf "(;FF[4]GM[1]CA[UTF-8]SZ[19]ST[0]AP[maxiGos:7.01];B[dq];W[dp];B[eq];W[do];B[fq];W[gp];B[eo];W[en];B[fo];W[dm];B[cl];W[fm];B[dl];W[fl];B[el];W[fj];B[di]SQ[dq][eq][fq][fo][eo]TR[fs][fr][er][es][ds][cs][bs])" 17 false >}}


> P.-S. Le statut d’un groupe n’est pas immuable, celui-ci peut changer au cours de la partie. Il faut alors vérifier ce statut après chaque coup joué à proximité d’un de nos groupes

Le glossaire est une série d'articles proposé par Nicolas Large (de la chaine Youtube [Râler autour d'un goban](https://www.youtube.com/channel/UCqxAbpvUeJCJhi0rIMv4_7A)) dans laquelle plusieurs termes courants au go sont définis.
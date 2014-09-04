---
sharing: true
comments: true
layout: page
title:  "Métriques"
date:   2014-06-12 08:00:00 +0100
locale: "fr"
permalink: /fr/console/website-metrics/
lead: "Cet écran vous propose des graphiques sur le temps de réponse, la disponibilité et le temps de chargement d’un site."
weight: "005"
---

![Check my Website console website metrics](/assets/img/fullsize/en/console/website-metrics/metrics.png)

## Navigation dans les graphiques

Vous pouvez naviguer dans les graphiques à partir de la barre située au dessus de chacun d'eux.

![Navigation dans les grahiques de la console Check my Website](/assets/img/fullsize/en/console/website-metrics/graph-navigation.png)

De gauche à droite :

- L'icône <i class="fa fa-backward"></i> permet de naviguer dans les période de temps précédentes. Voir ci-dessous pour période de temps.
- L'icône <i class="fa fa-fw fa-hand-o-right"></i> permet de préciser le contexte du graphique. Voir ci-dessous pour les explications de ce qu'est un contexte.
- L'icône <i class="fa fa-refresh"></i> permet de rafarîchir la page comme n'importe laquelle autre page de la console.
- L'icône <i class="fa fa-forward"></i> permet de naviguer dans les période de temps suivantes.

### Période de temps

Pour chaque graphique, vous pouvez choisir la période de temps affichée.

![Période de temps dans les graphiques de la console Check my Website](/assets/img/fullsize/en/console/website-metrics/graph-time-window.png)

Vous pouvez choisir parmi :

- Une heure
- Un jour
- Une semaine
- Un mois
- Trois mois

### Intervalle d'échantillonage de graphique

L'intervalle d'échantillonage du graphique fonctionne de pair avec la période de temps.

![Échantillonage dans les grpahiques de la console Check my Website](/assets/img/fullsize/en/console/website-metrics/graph-sampling.png)

Choisissez `auto` pour laisser la console décider de ce que représente un point du graphique.
Sur cet écran d'exemple, chaque point représente une valeur d'une minute. 

![Détail d'un point dans les graphiques de la console Check my Website](/assets/img/fullsize/en/console/website-metrics/graph-point-details.png)

Vous pouvez passer le curseur sur le graphique pour voir en détail ce que chaque point représente.

## Graphique de temps de réponse

Ce graphique représente le [temps de réponse](/fr/terms-definitions/#response-time) des différents lieux de contrôle pour un site web. Ce que vous voyez dépend de la période de temps choisie et de l'intervalle.

![Graphique de temps de réponse de la console Check my Website](/assets/img/fullsize/en/console/website-metrics/response-time-graph.png)

### Qu'est-ce que représente le temps de réponse dans ce graphique ?

Le temps de réponse représenté dans ce graphique est le temps qu'il faut au serveur pour envoyer la page.

Quand un navigateur se connecte à un serveur web, celui-ci doit exécuter un certain nombre d'étapes décomposées comme suit :

- Requête DNS.
- Connexion initiale.
- Attente.
- Réception de données. Pour une page web, c'est le contenu de celle-ci sans aucune autre requête. Les CSS et les fichiers média ne sont donc pas pris en compte.
- Fermeture de la connexion.

<p class="alert alert-info" role="alert">Notez que la requête DNS est <strong>mise en cache</strong> par le service Check my Website.</p>

Votre site est considéré :

- `Vert` quand cette valeur est au dessous de *500ms*.
- `Orange` quand cette valeur se situe entre *500ms* et *800ms*.
- `Rouge` quand cette valeur est au dessus de *800ms*.

### Contexte du graphique du temps de réponse

Cliquer sur l'icône <i class="fa fa-fw fa-hand-o-right"></i> vous donne plusieurs possibilités que nous allons expliquer.

![Contexte du graphique de temps de réponse de la console Check my Website](/assets/img/fullsize/en/console/website-metrics/graph-scope.png)

`Global` indique le temps de réponse moyen pour tous les lieux de contrôle choisis.

### Scission du graphique de temps de réponse

En dehors du contexte `Global`, vous pouvez choisir de scinder le graphique par lieu de contrôle avec l'icône <i class="fa fa-fw fa-hand-o-right"></i>. 

![Division du graphique de temps de réponse de la console Check my Website](/assets/img/fullsize/en/console/website-metrics/graph-split.png)

Chaque lieu de contrôle est représenté par sa propre couleur.

### Graphique du temps de réponse pour un lieu de contrôle

Cliquez un lieu de contrôle dans le menu <i class="fa fa-fw fa-hand-o-right"></i> vous donne la possibilité de ne voir que ce lieu de contrôle.

![Graphique du temps de réponse par lieu de la console Check my Website](/assets/img/fullsize/en/console/website-metrics/graph-location-detail.png)

Dans cet exemple, le graphique représente le temps de réponse du lieu de contrôle `Gravelines (59)`, dans le nord de la France.

## Graphique de disponibilité

Ce graphique représente la [disponibilité](/fr/terms-definitions/#availability) d'un site web pour la période temps et l'intervalle choisi.

![Graphique de disponibilité de la console Check my Website](/assets/img/fullsize/en/console/website-metrics/availability-graph.png)

La disponibilité d'un site web est considéré :

- `Vert` quand cette valeur est au dessous de *95%*.
- `Orange` quand cette valeur se situe entre *90%* et *95%*.
- `Rouge` quand cette valeur est au dessus de *90%*.

Ce site web n'a pas connu de problème pendant le dernier jour. Chaque point représente une heure (`Auto`).

## Graphique du temps de chargement de la page

Ce graphique représente le temps de chargement d'une page pour la période de temps et l'intervalle choisi. Par temps de chargement d'une page, nous entendons le temps que cela prend réellement à charger la page dans le navigateur. C'est ce temps que perçoivent vos utilisateurs, visiteurs.

![Graphique du temps de chargement de la page de la console Check my Website](/assets/img/fullsize/en/console/website-metrics/page-load-time-graph.png)

Le temps de chargement d'une page est considéré :

- `Vert` quand cette valeur est au dessous de *3000ms*.
- `Orange` quand cette valeur se situe entre *3000ms* et *5000ms*.
- `Rouge` quand cette valeur est au dessus de *5000ms*.

Dans ce graphique, il semble que le site web ait été surchargé le *23/07/2014* à *18:02* avec un temps de chargement de page aux alentours de *5 secondes*; comparée à la valeur habituelle de *500ms*.

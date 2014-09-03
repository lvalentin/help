---
sharing: true
comments: true
layout: page
title:  "Timeline d'une page web"
date:   2014-06-12 08:00:00 +0100
locale: "fr"
permalink: /fr/console/website-timeline/
lead: "La page de chronologie donne le détail du chargement d’une page, composant par composant."
weight: "006"
---

## Qu'est-ce qu'une timeline et HAR ?

Une timeline représente le chargement des composants d'une page web dans le navigateur.

Le format HTTP Archive Format (HAR est un format ouvert pour exporter et échanger de sdonnées collectées par les outils de supervision. Créé par Jan Odvarko et Simon Perkins, ce format est basé sur une structure JSON. La version en cours est la 1.22.

VOus pouvez lire en anglais les [spécifications complètes](http://www.softwareishard.com/blog/har-12-spec/) pour en savoir plus sur le format HAR.

## Le filmstrip

Au dessus de la timeline se trouve ce que nous appelons un filmstrip. C'est certainement la façon la plus simple et la plus sympa de comprendre comment se charge une page web « je pourrais dire dessiner » dans un navigateur.

![Filmstrip dans la console Check my Website](/assets/img/fullsize/en/console/website-timeline/filmstrip.png)

Dans ce cas, il y a uniquement trois copies d'écran prises :

1. Une première vide à *2ms*; la page commence à se dessiner.
2. Une à *167ms*; tous les textes et les CSS semblent être chargés. Il manque juste quelques images.
3. La page complète est dessinée en *1.45 s*. Pas si mal !

## La Timeline dans la console Check my Website

La timeline vous montre le temps nécessaire au chargement de chaque composant d'une page web depuis le serveur **sans cache navigateur**.

![Timeline dans la console Check my Website](/assets/img/fullsize/en/console/website-timeline/timeline.png)

La copie d'écran est tronquée du fait de sa longueur exceptionnelle !

À la fin de la timeline se trouve une ligne particulière qui donne le total. Cela représente le nombre total de requêtes « *82* » faîtes sur le serveur, le poids total de la page  « *980 KB* » et le temps total de chargement « *468ms* ».

Il y a deux lignes à droite de la timeline.

- La bleue indique le temps écoulé avant de voir l'événement `DOMContentLoaded` pris en compte dans le navigateur. *419ms* dans cet exemple.
- La rouge est le temps écoulé pour l'événement `Load`. *468ms* dans cet exemple.

Regardez du côté des [Navigation Timing specs](https://dvcs.w3.org/hg/webperf/raw-file/tip/specs/NavigationTiming/Overview.html) pour savoir exactement ce que sont ces événements.

### Détail d'un composant dans la timeline

Chaque ligne dans la timeline possède cinq colonnes :

![Détail d'un composant dans la console Check my Website](/assets/img/fullsize/en/console/website-timeline/component-detail.png)

1. La `Méthode` HTTP utilisée, `GET` dans ce cas en opposition à `POST` par exemple.
2. Le `Chemin` du composant. Si vous souhaitez avoir le chemin complet, voyez dessous dans la section encore plus de détail.
3. L'`État` du composant, qui est en fait le code réponse HTTP du serveur. Regardez [ceci](http://en.wikipedia.org/wiki/List_of_HTTP_status_codes) pour une liste complètes des codes retour HTTP.
4. La `Taille` du composant en KB. *11KB* dans cet exemple.
5. La `Timeline` du composant, scindé en temps d'attente « partie grise » et temps pour recevoir le composant « partie verte ».

Quand vous déplacez votre souris au dessus d'un composant, la timeline vous montre les valeurs exactes pour attendre et recevoir le composant.

![Détail d'un composant au survol de la souris dans la console Check my Website](/assets/img/fullsize/en/console/website-timeline/component-detail-mouseover.png)

Le composant `Mashup-571x348.png` est chargé à *123ms*, à un temps d'attente de *11ms* une durée de réception de *56ms* pour un temps toal de chargement dans le navigateur de *67ms*.

### Encore plus de détail d'un composant dans la timeline

Vous en voulez encore ? Pas de souci ! Voici l'**en-tête complet reçu depuis le serveur pour un composant**. Vous pouvez obtenir ceci en cliquant sur chacun des composants dans la timeline.

![Détail complet d'un composant dans la console Check my Website](/assets/img/fullsize/en/console/website-timeline/component-complete-detail.png)

Cliquez l'icône <i class="fa fa-times-circle"></i> pour fermer le détail complet d'un composant.
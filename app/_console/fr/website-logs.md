---
sharing: true
comments: true
layout: page
title:  "Événements et logs"
date:   2014-06-12 08:00:00 +0100
locale: "fr"
permalink: /fr/console/website-logs/
lead: "Cet écran vous permet de voir l’ensemble des événements survenus pour un site."
weight: "004"
---

## Définition d'un log

Le concept d'événements historiques ou journal d'événements « log » se réfère à la suite séquentielle d'événements enregistrée dans un fichier ou une base de données affectant un processus particulier « application, site web… ».

![Journal d'événements d'un site dans la console Check my Website console](/assets/img/fullsize/en/console/website-logs/logs.png)

## Navigation dans le journal d'événements

Vous pouvez naviguer dans le journal d'événements avec la barre située au dessus des événements eux-même.

![Navigation dans le journal d'événements de la console Check my Website](/assets/img/fullsize/en/console/website-logs/logs-navigation.png)

De gauche à droite :

- L'icône <i class="fa fa-backward"></i> permet de naviguer dans les événements précédents en fonction de la période de temps choisie. Voir ci-dessous pour période de temps.
- L'icône <i class="fa fa-refresh"></i> permet de rafraîchir la page comme n'importe laquelle autre page de la console.
- L'icône <i class="fa fa-trash-o"></i> rend possible la purge des logs. Elles sont alors effacées.
- L'icône <i class="fa fa-forward"></i> permet de naviguer dans les événements suivants en fonction de la périodfe de temps choisie.

Comme pour tout graphique, vous pouvez choisir la période de temps à afficher.

![Sélection de la période dans le journal d'événements de la console Check my Website](/assets/img/fullsize/en/console/website-logs/logs-time-window.png)

Vous pouvez choisir parmi :

- Une heure
- Un jour
- Une semaine
- Un mois

## Journal d'événements, événements

Le journal d'événements affichent des événements. Quand cela arrive t'il ?

- Changement d'état.
- Notification.

![Détail du journal d'événements dans la console Check my Website](/assets/img/fullsize/en/console/website-logs/logs-line.png)

De fauche à droite :

- Un badge indique l'[état](/fr/terms-definitions/) de l'événement. Vert pour `Ok`, orange pour `Attention`, rouge pour `Critique`.
- La date et heure de l'événement.
- L'icone <i class="fa fa-fw fa-hand-o-right"></i> indique le contexte de l'événement. Le contexte peut être Global en opposition à un lieu de contrôle par exemple.
- L'événement lui-même, le message.
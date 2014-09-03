---
sharing: true
comments: true
layout: page
title:  "Vue d'ensemble générale"
date:   2014-06-12 08:00:00 +0100
locale: "fr"
permalink: /fr/console/overview/
lead: "La vue d'ensemble générale vous donne une vue d’ensemble de tous les sites que vous supervisez."
weight: "002"
---

La vue d'ensemble est située à l'adresse [https://console.checkmy.ws/#/overview](https://console.checkmy.ws/#/overview).

![Vue globale dans la console Check my Website](/assets/img/fullsize/en/console/overview/global-overview-fullscreen.png)

Comme toutes les pages de la console, la [barre de menu et la navigation](/fr/console/menu-navigation/) se trouvent en haut de l'écran.

Vous pouvez toujours revenir à cette vue d'ensemble générale en cliquant le logo Check my Website dans le coin en haut à gauche du menu.

De haut en bas, voici ce que vous propose cette vue d'ensemble générale.

## La vue d'ensemble générale

Dans les faits, la vue d'ensemble générale se compose juste de ces 6 badges situés sous la navigation.

![Détail vue globale dans la console Check my Website](/assets/img/fullsize/en/console/overview/global-overview.png)

- Le *vert* donne le nombre de sites en [état `OK`](/fr/terms-definitions/#ok-state).
- Le *orange* donne le nombre de sites en [état `Attention`](/fr/terms-definitions/#warning-state).
- Le *rouge* donne le nombre de sites en [état `Critique`](/fr/terms-definitions/#critical-state).
- Le *bleu* donne le nombre de sites en [état `En attente`](/fr/terms-definitions/pending-state).
- Le *gris* donne le nombre de sites en [état `Inconnu`](/fr/terms-definitions/#unknown-state).

Cliquez sur l'un de ces badges filtre la [navigation](/fr/console/menu-navigation/) par état, affichant uniquement les sites dans l'état cliqué.

- Le badge *bleu* à droite donne le nombre `Total` de sites web que vous supervisez avec le service Check my Website.

## La disponibilité immédiate

La disponibilité immédiate permet de connaître la [disponibilité](/fr/terms-definitions/#availability) moyenne pour l'ensemble des sites que vous supervisez.

![Disponibilité immédiate dans la console Check my Website](/assets/img/fullsize/en/console/overview/instant-availability.png)

Si tous vos sites web sont disponibles comme dans l'exemple ci-dessus, cette valeur est à *100%* et vous pouvez retourner vous coucher !

## Le Top 5

Le Top 5 donne la liste de vos 5 sites les plus performants pour le temps de réponse et la disponibilité.

![Top 5 dans la console Check my Website](/assets/img/fullsize/en/console/overview/top-five.png)

### Top 5 disponibilité

À gauche, vous trouvez les 5 sites les plus [disponibles](/fr/terms-definitions/#uptime). Ce sont ceux qui sont dans l'état `OK` depuis le plus longtemps. Un mois pour le meilleur dans ce exemple d'écran.

### Top 5 des temps de réponse

À droite, vous trouvez les 5 sites dont les [temps de réponse]((/en/terms-definitions/#response-time)) sont les meilleurs. Ce sont les 5 sites qui répondent le plus vite. *41ms* pour le plus rapide de cet exemple.

<p class="alert alert-warning" role="alert">Cela <strong>ne signifie pas</strong> que ce sont les plus rapides à être chargés dans un navigateur.</p>
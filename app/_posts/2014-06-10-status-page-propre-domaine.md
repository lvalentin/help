---
sharing: true
comments: true
layout: post
title:  "Bonnes pratiques pour votre page de statut"
date:   2014-06-10 09:00:00 +0100
tags:
- checkmyws
- tips
author: Olivier Jan
post_img : hello-robot.jpg
lead: "Comment régler ses DNS pour avoir une page de statut sur votre propre domaine ?"
---

Vous souhaitez une [page de statut](/2014/05/checkmyws-status-page/) répondant à `http://status.votre-domaine.com` plutôt qu'une adresse `checkmy.ws` ? Et bien c'est désormais possible sur [Check my Website](http://www.checkmy.ws) !

Revue de détail de la marche à suivre, avec comme exemple monitoring-fr.org… Comme d'habitude !

## Créer un enregistrement CNAME

Commencez par créer un enregistrement `CNAME` au niveau de vos serveurs DNS. Celui-ci doit être sous la forme `status.votre-domaine.com` pointant vers `status.checkmy.ws`.

![Réglage CNAME sur les serveurs DNS](../img/posts/status-page-propre-domaine/dns-cname.png)

Pour monitoring-fr.org, le CNAME est donc `status.monitoring-fr.org` ou `status` en abrégé pointant vers `status.checkmy.ws`.

## Réglages dans la console Check my Website

Reste à paramétrer les préférences de la page de statut dans la console. Rendez-vous dans l'onglet `préférences` du site à paramétrer.

![Réglages dans la console](../img/posts/status-page-propre-domaine/statut-reglages-console.png)

- `Publique` : `Oui` pour que la page de statut soit accessbile à des personnes non identifées, publique quoi !
- `Alias` : La valeur de l'enregistrmeent `CNAME` des DNS. Pour notre exemple, `status.monitoring-fr.org`.
- `Lien de la page` : `http://status.monitoring-fr.org` qui est l'adresse à laquelle la page de statut sera accessible. Vous pouvez ignorer l'icône du triangle puisque les DNS sont en place.


## Victoire

La page de statut de monitoring-fr.org répond bien sur le domaine [monitoring-fr.org](http://status.monitoring-fr.org) !

![Page de statut sur son domaine](../img/posts/status-page-propre-domaine/statut-page.png)

Vous conviendrez j'espère qu'il n'y a plus aucune excuse pour ne pas utiliser une page de statut pour votre site !

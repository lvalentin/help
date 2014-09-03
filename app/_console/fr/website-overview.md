---
sharing: true
comments: true
layout: page
title:  "Vue détail d’un site"
date:   2014-06-12 08:00:00 +0100
locale: "fr"
permalink: /fr/console/website-overview/
lead: "Comme la vue globale mais appliquée à un site que vous supervisez."
weight: "003"
---

Vous avez une vue générale de site pour chacun des sites web que vous supervisez avec le service Check my Website.

![Vue générale d'un site dans la console Check my Website](/assets/img/fullsize/en/console/website-overview/website-overview.png)

Il y a dix parties dans cette vue générale que nous allons détailler maintenant.

## Identité du site web

Rien de particulier, juste l'adresse de la page, du site que vous supervisez.

![Identité site web dans la console Check my Website](/assets/img/fullsize/en/console/website-overview/website-url.png)

Le badge sur la gauche vous indique l'[état](/fr/terms-definitions/) du site monitoré à cet instant.

Si votre site possède un [favicon](http://fr.wikipedia.org/wiki/Favicon), celui-ci est représenté. Cliquez sur un site web vous amène à ce site web ! Si il n'y a pas de favicon, le logo Check my Website est représenté comme dna l'exemple en haut de cette page.

## Menu du site web

Comme la barre de menu mai spour les sites web. Cliquez sur n'importe qeulle tabulation pour aller à cette partie particulière de la page.

![Menu site dans la console Check my Website](/assets/img/fullsize/en/console/website-overview/website-menu.png)

- [`Vue d'ensemble`](/fr/console/website-overview/) donne une vue d'ensemble générale d'un site web. C'est là que nous sommes actuellement.
- [`Événements`](/fr/console/website-events/) donne l'ensemble des événements intervenus pour un site web. Ce peut-être le passage d'un état `Ok` à `Attention`, un état `Critique` à `Ok`.
- [`Métriques`]/fr/console/website-metrics/) est la partie où se trouvent des graphiques sur les temps de réponse, la notation YSlow…
- [`Timeline`](/fr/console/website-timeline/) donne le détail du chargement d'une page et de ses composants au standard [HAR](http://www.softwareishard.com/blog/har-12-spec/).
- [`YSlow`](/fr/console/website-yslow/) sont des recommandations de l'équipe performance Yahoo pour faire des sites web plus rapides. Ne manquez pas cette partie si vous prenez soin de la vitesse et de la conformité de votre site web.
- [`Préférences`](/fr/console/website-settings/) vous permet de modifier n'importe quel paramètre d'un contrôle de site web.

## Durée de l'état

Votre site web est dans un état en cours. `Ok` dans l'exemple. Ce panneau donne l'indication sur la durée de l'état en cours du site web. En d'autres termes, c'est le temps écoulé depuis le dernier changement d'état.

![Durée de l'état dans la console Check my Website console](/assets/img/fullsize/en/console/website-overview/state-duration.png)

La date juste au dessous de cette valeur est la date de dernier changement d'état.

## États par lieux de contrôle

L'état que vous avez eu dans la [vue d'ensemble générale](/fr/console/overview/) est calculé. Il est à `Ok` si la majorité des contrôles de sites web sont dans cet état. Ce panneau vous donne le détail de l'état de chaque lieux de contrôle.

![États par lieux de contrôle dans la console Check my Website](/assets/img/fullsize/en/console/website-overview/states.png)

De gauche à droite :

- L'état du site pour un lieu en particulier. Par exemple *`Ok`* depuis Paris.
- Le nom de ce lieu de contrôle, par exemple *Paris*.
- Le [temps de réponse](/fr/terms-definitions/#response-time) pour ce lieu de contrôle, par exemple *14ms* depuis Paris.

## Informations

Ce panneau donne quelques informations sur la réponse reçue depuis le serveur pour le site web.

![Informations sur un site dans la console Check my Website](/assets/img/fullsize/en/console/website-overview/informations.png)

Pour chaque information, vous avez une couleur qui peut varier à droite. Cetet couleur varie en fonction de bonne spratiques admises par la communauté.

- Un badge vert indique que tout est bien.
- Un badge orange indique des points à améliorer.
- Un badge rouge indique que tout va mal ;) 

Quelle ssont les informations données :

- Le nombre de [requêtes HTTP](/fr/terms-definitions/#http-request) faîte sopur recevoir la page. Moins, c'est mieux dans ce cas précis ! Dans cet exemple, *82* requêtes sont faîtes, ce qui est considéré un peu trop.
- Le nombre d'`Éléments non trouvés` est le nombre de composants demandés qui n'ont pas été trouvés sur le serveur « erreur 404 ». Un zéro est la seule option viable pour un bon site web ! Voilà la signification du rouge dans l'exemple avec une valeur à *1*
- Le nombre d'`Erreurs Javascript`est le nombre d'erreurs trouvées dans le code Javascript invoqués par cette page.
- Le nombre de `Nombre de redirections` est le nombre de [redirections HTTP](/fr/terms-definitions/#http-redirect) impliquées dans le rendu de cette page. Ici encore, le moins, c'est mieux ! À chaque fois que vous faîtes une redirection, vous ajoutez une nouvelle requête, de la latence pour contacter le nouveau composoant requêté… En version courte, **vous allongez le temps de rendu de la page**.

## Notation YSlow

Ce panneau vous done une notation YSlow pour le site, basée sur les [règles YSlow](http://checkmyws.github.io/yslow-rules/fr/). La note maximum est 100.

![Notation YSlow dans la console Check my Website](/assets/img/fullsize/en/console/website-overview/yslow.png)

Ce site web, malgré quelques erreurs indiquées dans le panneau d'informations, se porte plutôt pas mal avec un score de *95* et une notation *A*.

## Disponibilité sur les dernières 24 heures

Ce panneau permet de répondre à la question suivante : Est-ce que ce site a eu des problèmes de [disponibilité](/fr/terms-definitions/#availability) pendant ces dernières 24 heures ?

![Disponibilité sur les 24 dernières dans la console Check my Website](/assets/img/fullsize/en/console/website-overview/availability.png)

Celui-ci n'a pas connu de problème de disponibilité puisque il est à *100*. Bravo ! Cette valeur peut être utilisé dans le cadre de calcul de [SLA](/fr/terms-definitions/#service-level-agreement).

## Dernier temps de réponse

Le dernier [temps de réponse](/fr/terms-definitions/#response-time) montre le dernier temps de réponse moyen observé depuis tous les lieux de contrôle, par exemple *43ms*.

![Dernier temps de réponse dans la console Check my Website](/assets/img/fullsize/en/console/website-overview/last-response-time.png)

## Temps de réponse moyen sur les dernières 24 heures

Le temps de réponse moyen sur les denrières 24 heures donne le temps de réponse moyen observé depuis 24 heures depuis tous le slieux de contrôle, par exemple *45ms*.

![Temps de réponse moyen sur les dernières 24 heures dans la console Check my Website](/assets/img/fullsize/en/console/website-overview/mean-time.png)

L'indacteur en bleu est un indicateur de tendance qui indique si la moyenne des derniers temps de réponse est meilleur ou pire que le dernier temps de réponse.

## Événements, logs des dernières 24 heures

Tous les événements intervenus sur le site au cours des dernières 24 heures. Il y a principalement événement quand un site change d'[état](/fr/terms-definitions/#states). Ce panneau peut donc être vide.

![Événements des dernières 24 heures dans la console Check my Website console website](/assets/img/fullsize/en/console/website-overview/logs.png)

Dans l'écran d'exemple ci-dessus, le site web est passé de l'`état attention` à l'`état Ok`, ce qui est plutôt une bonne nouvelle !
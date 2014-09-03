---
sharing: true
comments: true
layout: page
title:  "Préférences"
date:   2014-06-12 08:00:00 +0100
locale: "fr"
permalink: /fr/console/website-settings/
lead: "Vous pouvez éditer et modifier n’importe quel site supervisé sur la page de préférences, à la fois en mode basique et mode avancé."
weight: "008"
---

Vous pouvez éditer et modifier n'importe quel paramètre d'un contrôle de site web depuis cette page.

![Préférences dans la console Check my Website](/assets/img/fullsize/en/console/website-settings/settings.png)

Nous faisons tout notre possible pour fournir des contrôles avec des réglages par défaut pertinents. Cela veut dire moins de travail pour vous. Vous pouvez compter sur les réglages par défaut pour tirer le meilleur parti du service Check my Website.

Cependant, vous pouvez changer n'importe quel paramètre en cliquant simplement dessus.

## Le menu préférences

Juste sous les tabulations de navigation se trouve le menu préférences.

![Menu préférences dans la console Check my Website](/assets/img/fullsize/en/console/website-settings/settings-menu.png)

De gauche à droite, vous pouvez trouver :

1. Le bouton `Désactiver` pour désactiver temporairement ou définitivement le contrôle d'un site web. Une fois cliqué, le site web n'est **plus** supervisé.
2. Le bouton `Supprimer` pour supprimer un site web de la supervision et de la console.
3. Le bouton `Replanifier le contrôle` pour re-plannifier immédiatement un contrôle du site web.
4. Le bouton `Mode avancé` qui permet de passer en mode avancé de la page des préférences. C'est en fait la même page avec plus d'options.

## Les préférences générales

Les préférences générales vous aide à saisir une adresse, URL d'un site ou page web et à vérifier quelques options de base.

![Préférences générales dans la console Check my Website](/assets/img/fullsize/en/console/website-settings/general.png)

- La `Date de création` ne peut pas être changée bien sûr. C'est la date et l'heure de création du contrôle.
- L'`URL` est l'adresse Internet du site web, de la page que vous souhaitez superviser.	
- L'`Intervalle` permet de choisir la fréquence de contrôles. 1 minute par défaut, sauf dans les comptes gratuits où cette valeur est de 5 minutes.
- Les `Tags` permettent de classer votre site web par mots clés.

### Les préférences général en mode avancé

Quatre nouveaux réglages apparaissent en mode avancé.

![Préférences générales en mode avancé dans la console Check my Website](/assets/img/fullsize/en/console/website-settings/advanced-general.png)


- `Méthode HTTP` est la méthode utilisée pour dialoguer avec le serveur. En général, `GET` ou `POST`.
- `Paramètres` permet de passer des paramètres à l'URL requêtée.
- `En-têtes` permet de manipuler les `headers` de la requête faîte au serveur.
- `Corps` vous permet la même chose sur le `body` de la requête.

## Les préférences des lieux de contrôle

Les préférences des lieux de contrôle permettent facilement de choisir les lieux depuis lesquels sont inités les contrôles pour un site web. Sur Check my website, ces contrôles sont effectués en parallèle.

Le nombre maximal de lieux de contrôle que vous pouvez choisir dépend du niveau de souscription au service. Regardez la page des [souscriptions](http://www.checkmy.ws/fr/pricing/) pour connaître les différentes options.

![Préférences lieux de contrôle dans la console Check my Website](/assets/img/fullsize/en/console/website-settings/locations.png)

## Les préférences du contrôle

Vous pouvez triturer les options principales d'un contrôle de site web dans ce panneau.

![Préférences d'un contrôle dans la console Check my Website](/assets/img/fullsize/en/console/website-settings/checks.png)

- `Dernier contrôle`  est la date et l'heure du dernier contrôle effectué.
- `Jeux de règles YSlow` permet de choisir le jeux de règles à utiliser avec YSlow. Voyez du côté de [YSlow](/fr/console/website-yslow/) pour plus d'informations sur ce sujet.

### Les préférences du contrôle en mode avancé

Trois nouvelles options apparaîssent en mode avancé.

![Préférences d'un contrôle en mode avancé dans la console Check my Website](/assets/img/fullsize/en/console/website-settings/advanced-checks.png)

- `Code réponse HTTP` est le code réponse attendu dans la réponse du serveur web. C'est en général `200`.
- `Limite de temps HTTP (ms)` permet de fixer une limite de temps à ne pas dépasser. Si vous entrez *500ms*, alors votre site web doit répondre en moins de 5 secondes . Vous serez notifié si le site web répond au delà de cette limite de 5 secondes.
- `Chaîne de caractères` permet de spécifier une chaîne de caractères à trouver dans la réponse du serveur web. Permet de vérifier qu'un site n'a pas été [défacé](http://fr.wikipedia.org/wiki/D%C3%A9facement).

## Les préférences de notifications

Toutes les préférences pour tous les moyens de notification se trouvent ici réunies.

![Préférences des notifications dans la console Check my Website](/assets/img/fullsize/en/console/website-settings/notifications.png)

- `Notification par Email` permet d'activer ou désactiver les notifications pour un site web.
- `Destinataires` est la liste des adresses électroniques des personnes à alerter en cas de problèmes.

### Les préférences de notifications en mode avancé

Deux nouvelles options se présentent en mode avancé.

![Préférences des notifications en mode avancé dans la console Check my Website](/assets/img/fullsize/en/console/website-settings/advanced-notifications.png)

- `Contrôles de confirmation` permet de préciser le nombre maximal de contrôles de confirmation à effectuer avant d'envoyer une notification. Plus vous en utilisez, moins vous avez de chance de recevoir un « faux positif ». Mais le délai avant envoi d'une notification s'allonge d'autant. *3* est une bonne valeur pour être notifié dans un délai correct tout en minimisant les « faux positifs ».	
- `États` permet de choisir les états sur lesquels vous souhaitez être notifié. Choisir `Ok` et `Critique` permet de recevoir une notification pour chaque changement d'état entre `Ok` et `Critique` mais aussi entre `Critique` et `Ok`.

## Les préférences de la page de statut

Les préférences de la [page de statut](/fr/console/website-status-page/) permettent de construire une page de statut pour communiquer sur l'état de santé de votre site web auprès de vos visiteurs ou de vos collègues.

![Préférences de la page de statut dans la console Check my Website](/assets/img/fullsize/en/console/website-settings/status.png)

- `Publique` permet de choisir de rendre la page de statut publique ou non.
- `Alias` est un alias Internet à laquelle votre page de statut peut être trouvée. Pratique pour avoir une page de statut sur votre propre domaine plutôt que sur celui de checkmy.ws.
- `Lien de la page` est l'alias + le protocole utilisé pour votre page de statut. Vous devez avoir une entrée CNAME dans vos DNS pour que cela fonctionne.
- `Partage de la page` permet à vos visiteurs de partager cette page de statut sur les principaux Réseaux sociaux.

### Les préférences de la page de statut en mode avancé

Deux nouveaux réglages apparaîssent en mode avancé.

![Préférences de la page de statut en mode avancé dans la console Check my Website](/assets/img/fullsize/en/console/website-settings/advanced-status.png)

- `Réseaux sociaux` permet de partager sur votre page de statut vos principales adresses de réseaux sociaux. 
- `Description` permet de décrire la page, votre activité directement sur la page de statut. 

Plus d'informations sur la page de statut peut être trouvée dans la [documentation](/en/console/website-status-page/).
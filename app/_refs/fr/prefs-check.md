---
sharing: true
comments: true
layout: post
title:  "Console : Du fun avec les en-têtes HTTP"
date:   2014-06-12 08:00:00 +0100
tags:
- console
- usecase
- checkmyws
author: Olivier Jan
post_img : atom-puzzle.jpg
lead: "Étude de quelques exemples concrets de manipulation des headers dans la console Check my Website."
---

J'avais commencé à « jouer » avec les [contrôles avec arguments](/2014/05/wordpress-test-fonctionnement-checkmyws/) lors d'un précédent billet. Il est question aujourd'hui de triturer les headers, en-têtes HTTP en bon français pour pouvoir se **sortir de situations de supervision délicates**.

Le premier cas nous est arrivé via le support. Je vous le livre tel que.

## Vérifier Outlook Web Access

La question reçue au support était celle-ci :

> Bonjour, je cherche a monitorer notre webmail qui est en HTTPS et qui à un certif et j'ai donc une erreur 400, avez vous une solution ?

Nous avons été voir le webmail en question et nous sommes aperçus qu'il s'agissait d'un serveur webmail basé sur Outlook Web Access.

Ce type de webmail attend un `user-agent` dans la requête qui est lui est faite, sinon le contrôle est en erreur. 

Je prends l'exemple habituel de monitoring-fr.org pour illustrer le cas support mais les réglages, le raisonnement s'applique bien sûr à un serveur Outlook Web Access.

Pour résoudre le problème, il faut se rendre dans le mode avancé des préférences pour le site et renseigner une clé et une valeur pour `En-têtes`.

Vous pouvez par exemple mettre `User-Agent` comme clé et `Chrome/33.0.1750.146` comme valeur.

![Réglages en mode avancé des headers](../img/posts/console-headers-http-manipulation/console-preferences-check.png)

Voilà les entrées journal du serveur web de monitoring-fr.org qui est testé de cette façon. Les IPs sont remplacés par `xxx.xxx.xxx.xxx`. Nous voyons par contre clairement la requête demandée et le `User-Agent` que nous avons renseigné.

~~~
xxx.xxx.xxx.xxx - - [06/Jun/2014:10:36:50 +0200] "GET / HTTP/1.1" 301 5 "-" "Chrome/33.0.1750.146" "xxx.xxx.xxx.xxx"
xxx.xxx.xxx.xxx - - [06/Jun/2014:10:36:50 +0200] "GET / HTTP/1.1" 200 12861 "-" "Chrome/33.0.1750.146" "xxx.xxx.xxx.xxx"
~~~

Outlook Web Acces, c'est fait !

## Vérifier un cluster web

Prenons maintenant un cas d'école pour tester un site particulier derrière des répartiteurs de charge.

![Architecture](../img/posts/console-headers-http-manipulation/synaptic.png)

Quand vous demandez votre site via son adresse `http://www.mon-super-site-a-moi.com`, la résolution DNS vous enverra vers l'IP du répartiteur de charge. Pareil pour le contrôle Check my Website.

Si vous souhaitez tester chacun des membres de votre cluster web, il faut utiliser le FQDN (ou IP) de chaque noeud. Bien evidement, il faut que les noeuds soit accessible depuis [`les internets`](http://www.thedailyfrench.fr/2013/02/11/d-ou-vient-l-expression-les-internets) mondiale.

Problème, comment demander à `www1` de nous servir le site `http://www.mon-super-site-a-moi.com` ?

Utiliser les en-têtes bien sûr ! Étudions les en-têtes d'une requête vers mon-super-site-a-moi...

~~~
Host: www.mon-super-site-a-moi.com
User-Agent: Mozilla/5.0 (Macintosh; Intel Mac OS X 10.9; rv:29.0) Gecko/20100101 Firefox/29.0
Accept: text/html,application/xhtml+xml,application/xml;q=0.9,*/*;q=0.8
Accept-Language: fr,fr-fr;q=0.8,en-us;q=0.5,en;q=0.3
Accept-Encoding: gzip, deflate
Connection: keep-alive
If-Modified-Since: Fri, 06 Jun 2014 08:10:58 GMT
Cache-Control: max-age=0
~~~

Notons au passage le `User-Agent`… Magnifique, très complet ! Blague à part, il y a là une clé et une valeur qui nous intéresse particulièrement; c'est `Host` avec la valeur `mon-super-site-a-moi.com`.

Nous allons utiliser ce paramètre conjoitement avec le contrôle d'une chaîne de caractère dans la réponse pour être 100% sûr que :

- Nous contrôlons bien un FQDN ou une IP d'un pool de répartition. `http://www.mon-super-site-a-moi.com` est servi par `www1`, `www2` et `www3` via `wwww`
- Nous contrôlons bien le site `http://www.mon-super-site-a-moi.com` sur un serveur où est également hébergé `http://www.ton-super-site-mais-a-moi-quand-meme.com`.

D'abord, un premier réglage en mode avancé des préférences pour spécifier l'adresse du serveur, flouté dans la copie d'écran. Ce peut être `www1` pour notre exemple.

![Réglages paramètre Host des en-têtes](../img/posts/console-headers-http-manipulation/console-host-header.png)

La partie intéressante est bien sûr `En-têtes` où nous retrouvons `Host` comme clé et `www.mon-super-site-a-moi.com` comme valeur

Un deuxième réglage dans la partie `Contrôles` des préférences pour fixer la chaîne de caractères attendue dans la réponse. Celle-ci doit être unique au site à tester bien sûr. Dans l'exemple, c'est le mot `location` qui est recherché dans la réponse. Non, vous ne pouvez pas me demander pourquoi c'est `location`…

![Réglages en mode avancé des headers](../img/posts/console-headers-http-manipulation/console-pattern.png)

## Une conclusion, la vôtre ?

Comment un cas d'école relativement complexe à expliquer peut finalement se terminer par une solution plutôt simple pourrait être la conclusion.

Nous n'avons vu que deux cas mais il est **possible de s'adapter à pas mal de situations grâce aux diverses manipulations sur les paramètres d'un contrôle et sur les en-têtes, corps** de celui-ci. 

Si vous avez un cas concret d'utilisation, surtout bien tordu, n'hésitez pas à nous le soumettre ! C'est ma façon de vous laisser conclure sur le sujet.

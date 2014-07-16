---
sharing: true
comments: true
layout: post
title:  "PacketBeat : Solution possible pour l'APM ?"
date:   2014-06-24 08:00:00 +0100
tags:
- elk
- opensource
- apm
author: Olivier Jan
post_img : launching-controls.jpg
lead: "PacketBeat est la première solution clé en main contruite sur ELK pour la supervision et l'APM de votre site web."
---

Si vous avez déjà essayé ELK, vous avez dû arriver à la conclusion que celui-ci est de plus en plus à considérer comme un "framework" de traitements d'événements et métriques plutôt qu'un produit fini, prêt à l'emploi.

L'installation de la pile ELK ne pose aucun souci mais le **paramétrage d'un flux de traitement spécifique à un contexte donné peut demander pas mal de temps**. Il faut en effet formater, filtrer les données et ensuite construire les tableaux de bord pertinents sur ces données.

Toutes ces **opérations demandent du temps, des compétences et c'est donc naturellement que Packetbeat ouvre la voie à des solutions clés en main construites sur ELK**. Du coup, tout est prêt… Ou presque à la sortie de la boîte !

Je prends le pari que [Packetbeat](http://packetbeat.com/) pourrait bien être le premier d'une longue série.

## Définition APM

Dans les domaines des technologies de l'information et la gestion des systèmes, l'Application Performance Management (APM) est la partie de la supervision qui comprend **la surveillance et la gestion de la performance ainsi que la disponibilité des applications**. L'APM vise à détecter et diagnostiquer les problèmes de performance des applications de façon à **maintenir, garantir le niveau de service attendu**. L'APM traduit les indicateurs techniques informatiques en indicateurs qui ont du sens, de la valeur pour l'entreprise « indicateurs métiers, business ».

## Packetbeat, kesako ?

Packetbeat est un système distribué de surveillance de paquet pouvant être utilisé dans le cadre de l'Application Performance Monitoring « APM ». C'est une espèce de [Wireshark](http://www.wireshark.org/) avec beaucoup plus de fonctionnalités d'analyse.

Les agents Packetbeat **surveillent le trafic entre vos processus applicatifs, analysent à la volée les protocoles comme HTTP, MySQL, PostgreSQL ou REDIS et corrélent les messages en transactions**. Vu les technos supervisées, c'est clairement destiné, au moins pour le moment, à une architecture web plus ou moins traditionnelle. Pour chaque transaction, les agents insérent un document JSON dans Elasticsearch

Packebeat utilise une version modifiée de Kibana permettant de créer des widgets pour visualiser les topologies de réseau.

Pour résumé, il est possible de dire que **Packetbeat est avant tout un client de la solution Elasticsearch Kibana**.

### Installation de Packetbeat

Je passe la partie installation de la pile ELK qui ne présente aucune difficulté et que nous avons [déjà abordée](/2014/04/elk-elasticsearch-logstash-kibana/) sur Wooster pour focaliser sur les parties spécifiques à Packetbeat.

### Configuration de Packetbeat

La configuration d'un agent est simple et vous pouvez très bien vous contenter d'indiquer dans le fichier de configuration `/etc/packetbeat/packetbeat.conf` le serveur Elasticsearch du serveur.

Côté serveur, il faut préciser un « index template » Elasticsearch et charger quelques modèles de tableaux de bord. Ces opérations se font dans une logique toute « Elasticsearch »; avec la commande `curl` comme seul outil.

	curl -XPUT 'http://localhost:9200/_template/packetbeat' -d@packetbeat.template.json

Cett commande charge le modèle `packetbeat.template.json` sur le serveur Elasticsearch situé sur `localhotst`.

Tout est très bien expliqué dans le [guide de démarrage](http://packetbeat.com/getstarted) de Packetbeat.

## Les tableaux de bord

C'est bien évidemment les **tableaux de bord fournis qui donnent tout leur sens à ce genre de solutions** construites sur ELK. Ils fournissent la matière de base aux différentes analyses à mener pour comprendre son application. Et Packetbeat n'est pas avare de graphiques comme le montre cette copie d'écran issu de la démonstration.

![Packetbeat statistics dashboard](../img/posts/packetbeat-elk-apm/packetbeat-stats-dashboard.png)

Je vais reprendre quelques graphiques, mais cette fois issus du premier site web que j'ai placé sous inspection packetbeat et pour lesquels j'ai quelques informations que je voudrais partager avec vous. 

### Top web transactions

![Top web transactions](../img/posts/packetbeat-elk-apm/top-web-transactions.png)

Il est possible d'apprendre déjà pas mal de choses avec ce tableau.

Les `GET` vers `/sites/…` indique une installation Drupal et pourtant la requête la plus demandée est `/wp-login.php`; certainement signe de quelques mal-intentionnés tentant de vérifier les technos utilisées avant « attaque ».

Et Check my Website me confirme que je ne devrais pas voir de 404 si la page existait. Le contrôle ne renvoie pas d'éléments non trouvés dans la page de ce site.

![Informations générales de la page](../img/posts/packetbeat-elk-apm/checkmyws-resume.png)

### Web transaction errors

Je retrouve d'ailleurs ces `wp-login.php` comptabilisé en 404 dans cet autre graphique, qu'il conviendrait sûrement de renommer en répartition des codes retours serveurs.

![Web transactions errors](../img/posts/packetbeat-elk-apm/web-transactions-errors.png)

J'avais obtenu modestement ce genre de graphique avec mes essais [ELK Nginx](/2014/06/nginx-syslog-elk/).

### Web transactions

Ce graphique donne le volume de transactions HTTP pour l'application durant les 24 dernières heures.

![Web transactions volume](../img/posts/packetbeat-elk-apm/web-transactions-volume.png)

Le site « dort » entre 2 heures et 8 heures du matin. Au plus haut de la journée, le site génère 400 transactions minute.

### Slowest web transactions

Encore un graphique intéressant qui permet d'analyser les transactions applicatives en présentant la répartition en temps de réponse de celles-ci.

![Slowest web transactions](../img/posts/packetbeat-elk-apm/slow-web-transactions.png)

Une liste complète des requêtes les plus lentes est également disponibles pour compléter l'analyse.

## Conclusion de ce petit galop d'essai

L'analyse que fait Packetbeat depuis les flux réseaux permet de remonter beaucoup d'informations qui sont corrélées en transactions. C'est cette particularité qui fait la singularité de Packetbeat. C'est un superbe complément à une solution classique de supervision. Et n'oubliez pas que **c'est une vision utilisateur qui vous est présentée**.

Packetbeat est jeune mais plein de potentiel et de promesses dans un domaine; l'APM, où les solutions Open Source ne sont pas légion.

Le fait qu'il soit construit sur **ELK est un gage de cohérence** si vous avez décidé comme moi de faire de **celui-ci un de vos piliers de supervision**. Pas de nouveau outil à apprendre, pas d'installation supplémentaire ou presque, que du bonheur !

Définitivement un outil à suivre de près et encore une belle démonstration de la puissance et de la flexibitlité de la pile ELK sera ma conclusion !

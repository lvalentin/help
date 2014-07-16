---
sharing: true
comments: true
layout: concise
title:  "Supervision : Vous êtes plutôt actif, passif ?"
date:   2014-05-30 08:00:00 +0100
tags:
- monitoring
- supervision
author: Olivier Jan
post_img : cocktail-home.jpg
lead: "Actif, passif, interne, externe : Rappel des différents modes de supervision d'un site web."
---

Je suis persuadé que notre offre de services [Check my Website](http://www.checkmy.ws) peut parfaitement compléter une solution de monitoring « in house ».

C'est en effet un complément idéal à une solution qui voit les choses de l'intérieur puisque de notre côté, nous voyons les choses de l'extérieur.

Il est temps d'expliquer les **notions de supervision interne, externe, avec ou sans agent, active, passive, proche de l'utilisateur**; d'autant qu'elles recoupent à peu près les mêmes concepts de supervision.

C'est un fait, nous sommes à une époque où les systèmes d'informations sont de plus en plus distribués. C'est donc une **longue chaîne de liaison qui est mise en œuvre pour pouvoir servir une page web dans le navigateur d'un utilisateur**.

Rappelez-vous que dans le [billet sur pourquoi superviser](/2014/02/pourquoi-superviser-site-web/), je disais que la supervision permettait de répondre entre autres à :

1. Est-ce que mon service est disponible ?
2. Il n'est pas disponible, qu'est-ce qui ne fonctionne pas ?

Comment alors mixer les différentes formes de monitoring pour obteniur la meilleure couverture possible ?

## Les différentes méthodes supervision

Avant de voir si les différentes formes de supervision sont plutôt exclusives ou cumulatives, il est important de définir ces formes.

### Monitoring actif

Dans cette forme de supervision, c'est le serveur de supervision qui interroge à intervalles réguliers les composants à surveiller. C'est la forme de supervision la plus communément déployée aujourd'hui. Il existe pléthore d'outils dans le monde Open Source pour effectuer ce type de supervision dont les noms les plus connus sont Nagios, Shinken, Icinga et Zabbix.

![Exemple contrôle actif SNMP avec Nagios](../img/posts/monitoring-interne-externe-actif-passif/nagios-snmp-actif.png)

C'est aussi le mode utilisé par le service Chek my Website pour vérifier à intervalles la réponse des sites testés.

### Monitoring passif

Fort logiquement, cette forme de supervision est l'exact inverse de la précédente. Ici, ce sont les composants surveillés qui envoient à intervalles réguliers (ou non) métriques et messages vers une instance centrale de supervision. C'est le mode de fonctionnement du couple Collectd-Graphite par exemple.

![Exemple contrôle passif SNMP avec Nagios](../img/posts/monitoring-interne-externe-actif-passif/nagios-snmp-passif.png)

Les interruptions SNMP, la gestion des logs sont des exemples de supervision passive. les messages et métriques sont envoyées depuis la source « le composant surveillé » vers le serveur de supervision.

Nous utiliserons ce mode de supervison pour Check my Website dans le cadre des contrôles « Real User Monitoring » à venir. C'est le navigateur de l'internaute qui poussera les données vers notre API.

### Monitoring externe

Répondant également au doux nom de monitoring synthétique, c'est la forme de supervision qui permet de rendre compte de l'état d'un serveur en se plaçant au plus proche possible de l'utilisateur.

C'est le type de supervison que propose Check my Website. Elle ne nécessite pas d'instrumentation spécifique sur le serveur à superviser.

### Monitoring interne

Le monitoring interne est fait directement sur l'infrasctructure mise en œuvre. Il nécessite un agent de supervision installé sur les serveurs à superviser. Il est aussi d'usage de dire que le monitoring interne est celui qui est fait avant le firewall sortant de l'entreprise.

## Complémentaires, exclusifs ?

Le monitoring externe permet le mieux de répondre à la question 1 du préambule; à savoir mon site est-il disponible ? Ce type de monitoring vous donne **le point de vue le plus proche possible de l'utilisateur final**. Et si la page attendue est correctement servie, vous pouvez être certain que tout ce qui est utilisé pour la composer fonctionne, que ce soit la base de données, les disques durs, la mémoire…

Par contre, **quand quelque chose ne va pas, le monitoring interne, qu'il soit passif ou actif, est la meilleure source d'informations et d'aide au diagnostic**.

Une solution complète de monitoring, métrologie pour un site web pourrait donc être composée de :

- Monitoring interne passif pour les logs par exemple et pour une métrologie à intervalles courts (moins de 1 mn)
- Monitoring interne actif pour s'assurer de la disponibilité des différents composants de l'application. Ainsi votre instance PHP5-FPM peut interroger à intervalles réguliers le serveur MySQL dont elle a besoin pour votre site web.
- Monitoring externe actif pour vérifier au plus proche de l'utilisateur la disponibilité et la performance du site web.
- Monitoring externe passif pour envoyer des données de type « Real User Monitoring ».

Un peu de tout quoi ! Après tout, l'homme est omnivore et a besoin de varier ses menus. Pourquoi cela serait-il différent pour la supervision ?


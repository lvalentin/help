---
sharing: true
comments: true
layout: post
title:  "Journalisation, logs Nginx avec ELK via Syslog"
date:   2014-06-05 08:00:00 +0100
tags:
- nginx
- elk
- opensource
author: Olivier Jan
post_img : timeolite.jpg
locale: "en"
lead: "Profitons de la sortie de Nginx 1.7 qui permet de journaliser dans Syslog pour envoyer accès et erreurs à ELK."
---

Voilà un billet bien opportuniste puisqu'il me permet de saluer la sortie de Nginx 1.7 et de vous présenter une première machine prête à l'emploi pour tester le setup proposé.

Nginx 1.7 permet de journaliser accès et erreurs dans syslog plutôt que dans des fichiers plats et donc d'envoyer ces événements vers une instance Logstash.

Le but est **d'obtenir des événements structurés sur lesquels il sera possible de faire des recherches et statistiques**.

## Démarrage d'un serveur ELK

Pour vous éviter d'avoir à suivre de nombreuses procédures d'installation, vous pouvez utiliser la machine virtuelle que nous mettons à disposition pour ELK.

Vous devez avoir Vagrant et VirtualBox installés sur votre machine. L'installation est sans problème sur Windows, OS X et Linux.

Clonez le dépôt des [applications virtuelles Check my Website](https://github.com/checkmyws/v-apps) et déplacez-vous dans le répertoire `elk`.

Hop, un `vagrant up` et laissez agir…

Vous pouvez vous connecter sur `http://192.168.56.20/kibana/` pour vérifier que tout fonctionne bien.

![Kibana prêt à l'emploi et fonctionnel](../img/posts/nginx-syslog-elk/kibana-awaiting.png)

Allez, un dernier `vagrant ssh` pour vous connecter à la machine si besoin.

### Configuration Nginx

Rien de compliqué puisque la nouvelle version gère ce type de journalisation nativement. Il suffit d'éditer le fichier de configuration pour le site web à journaliser et d'y ajouter ces lignes à l'intérieur du bloc `server`.

    access_log syslog:server=127.0.0.1:5140;
    error_log syslog:server=127.0.0.1:5140;
    
Il faut indiquer l'adresse du serveur Syslog destinataire et le port si différent « comme ici `5140` » du port standard `514`.

### Configuration Logstash

Ci-dessous un fichier de configuration complet pour Logstash. Si vous utilisez notre machine virtuelle, tout a été fait pour vous.

~~~
input {
  tcp {
    port => 5140
    type => nginx
  }
  udp {
    port => 5140
    type => nginx
  }
}

filter {
  if [type] == "nginx" {
    grok {
      match => [ "message", "%{COMBINEDAPACHELOG}" ]
    }
  }
}

output {
  elasticsearch { host => localhost }
  stdout { codec => rubydebug }
}
~~~

C'est une configuration minimale pour ce genre de tâches. Logstash se met en écoute sur le port UDP et TCP 5140, histoire de ne pas se mélanger avec le syslog système et de ne pas avoir besoin de privilèges élevés.

Le filtre est un filtre [Grok](http://logstash.net/docs/1.4.1/filters/grok) faisant appel au motif `COMBINEDAPACHELOG`.

La sortie envoie tout à Elasticsearch sur le serveur local.

## Le festival peut commencer

Chargez dans votre navigateur la page par défaut de Nginx accessible sur `http://192.168.56.20` pour générer des accès.

Dans Kibana, nous obtenons des événements parfaitement structurés.

![Détail d'un accès Nginx dans Kibana](../img/posts/nginx-syslog-elk/kibana-detail-access.png)

Vous souhaitez voir la répartition des pages par type de requêtes, codes retour… Tout est désormais possible !

![Exemple de tableau de bord Nginx dans Kibana](../img/posts/nginx-syslog-elk/kibana-dashboard.png)

Vous trouverez dans les sources du dossier `elk` un dossier dashboards dans lequel se trouve le fichier `nginx.json` à importer pour reproduire le tableau de bord ci-dessus.

C'est un tableau de bord simple qui présente la répartition des accès par type de réponse serveur, type de requêtes ainsi que les 4 requêtes les plus demandés.

Pour compléter ce tableau de bord, vous pouvez décider de faire suivre des événements vers Nagios avec le plugin Logstash [nagios_nsca](http://logstash.net/docs/1.4.1/outputs/nagios_nsca) ou envoyer des métriques à Statsd et/ou Graphite avec le plugin [graphite](http://logstash.net/docs/1.4.1/outputs/graphite).

Vous pourriez par exemple envoyer à Nagios les URLs en 404 pour information et envoyer le compte de ces mêmes 404 vers Statsd/Graphite. À vous de jouer !

## Conclusion

Voilà une première jolie illustration concrète de la puissance de ELK. Le problème n'est plus de collecter des données de supervision mais de **savoir quoi en faire et comment les représenter** pour les « faire parler ». Autrement dit, une fois réglé le formatage des données à remonter, c'est dans Kibana que ça se passe ! Qui fera le meilleur tableau de bord Kibana pour Nginx ?

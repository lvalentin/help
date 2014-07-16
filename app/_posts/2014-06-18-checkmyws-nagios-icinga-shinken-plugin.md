---
sharing: true
comments: true
layout: post
title:  "Premier plugin Check my Website pour vos solutions de supervision"
date:   2014-06-18 08:00:00 +0100
tags:
- nagios
- plugin
- checkmyws
author: Olivier Jan
post_img : gaertners-tonometer.jpg
lead: "Le premier plugin pour connecter votre solution de supervision à Check my Website vient de sortir."
---

Vous me croirez ou non mais c'est un moment plein d'émotion que de voir débarquer le premier plugin pour pouvoir mixer [le meilleur des deux mondes](/2014/05/monitoring-interne-externe-actif-passif/); à **savoir votre outil de supervision interne et un service externe comme Check my Website**.

Et comme les utilisteurs de Nagios like, Shinken, Icinga et autres sont légion parmi nous, c'est un **plugin qui permet à votre installation « Nagios Plugin Compatible » de venir interroger l'API de Check my Website pour récupérer dans votre outil les valeurs récoltées** par le service.

## Installation et utilisation du plugin

Rien de bien compliqué dans l'installation. il vous faut un interpréteur Python, langage du plugin et une dépendance Python est requise.

Le plus simple pour installer la dépendance Python est `pip`.

~~~
pip install --upgrade checkmyws-python docopt
~~~

Récupérer ensuite le fichier et le rendre exécutable.

~~~
wget --no-check-certificate https://raw.githubusercontent.com/checkmyws/checkmyws-plugins/master/nagios/check_mywebsite.py
chmod +x check_mywebsite.py
~~~

Vous avez bien sûr tout intérêt à déposer le plugin dans votre dossier `libexec` de plugins Nagios. 

### Configuration au niveau console.

Avant de pouvoir utiliser le plugin, il faut **récupérer l'ID Check my Website du site dont les données sont à récupérer**. Vous trouvez cette information en `mode avancé` dans l'onglet `préférences` de votre site.

![Sélection de l'ID du site dans la console](../img/posts/checkmyws-nagios-icinga-shinken-plugin/console-check-id.png)

La [page de statut](/2014/05/checkmyws-status-page/) pour le site doit également être activée.

### Utilisation du plugin

Comme pour tout plugin Nagios, le plus simple pour connaître le fonctionnement du plugin est de l'exécuter avec un `-h`.

~~~
$ ./check_mywebsite.py -h
Check my Website plugin.

Usage:
  check_mywebsite.py [(-v | --verbose)] [--proxy=<proxy>] [-f] <check_id>
  check_mywebsite.py (-h | --help)
  check_mywebsite.py (-V | --version)

Options:
  -f               Display perfdata.
  -e               Display extra output.
  --proxy=<proxy>  Proxy URL.

  -h --help        Show this screen.
  -V --version     Show version.
  -v --verbose     Verbose.
~~~

La commande accepte essentiellement deux paramètres.

- `-f` permet de récupérer les données de performance du plugin.
- `-e` permet d'utiliser la sortie étendue du plugin et d'afficher des URLs cliquables dans la console comme nous le verrons plus bas. 

~~~
./check_mywebsite.py -e -f 95c81e64-48af-4190-acb7-48bd659ea903
~~~

donne une sortie richement dotée en `perfdata`.

~~~
200 Ok, Mean response time: 63ms [<a href='http://95c81e64-48af-4190-acb7-48bd659ea903.status.checkmy.ws'>status page</a>] [<a href='https://console.checkmy.ws/#/dashboard?_id=95c81e64-48af-4190-acb7-48bd659ea903'>console</a>] | 'FR:SXB:OVH:DC'=66ms;;;0; 'DE:FRA:OVH:DC'=46ms;;;0; 'FR:PAR:OVH:DC'=60ms;;;0; 'IT:MIL:OVH:DC'=72ms;;;0; 'ES:MAD:OVH:DC'=66ms;;;0; 'FR:GRA:OVH:DC'=72ms;;;0; 'mean_time'=63ms;;;0; 'yslow_page_load_time'=1036ms;;;0; 'yslow_score'=93;;;0;100
~~~

la même commande encapsulée dans `time` donne les durées d'exécution suivantes :

~~~
time ./check_mywebsite.py -e -f 95c81e64-48af-4190-acb7-48bd659ea903

real	0m0.319s
user	0m0.072s
sys		0m0.024s
~~~

Avec 0,3 secondes de temps d'exécution, ce n'est **pas un plugin qui va ajouter de la latence à votre installation** !

## Configuration dans Icinga

Comme j'avais une machine prête avec un Icinga version 1 à jour, c'est avec celui-ci que j'ai mis en place l'automatisation du contrôle.

### Création d'une commande

Une commande minimale pour notre exemple

~~~
define command {
	 command_line	$USER1$/check_mywebsite.py -e -f $_SERVICECHECKMYID$
	 command_name   check_mywebsite
}
~~~

J'utilise une macro personnalisée `$_CHECKMYID$` qui sera définie dans le service ci-dessous plutôt qu'un `$ARG1$` peu explicite.

### Création d'un hôte

La notion d'hôte de Nagios ne fonctionnant pas trop pour un site web réparti sur un ou plusieur sserveur sweb, j'utilise le nom du site comme `hostname`et fixe l'adresse IP sur la boucle locale. Cette définition d'hôte s'appuie sur un `template application-server` qu'il faut créer au préalable.

~~~
define host {
	 alias			Site Web monitoring-fr.org
	 use            application-server
	 host_name      www.monitoring-fr.org
	 address        127.0.0.1
}
~~~

### Création d'un service

La définition du service utilise le template external-service

~~~
define service {
	 service_description          checkmywebsite
	 use                          external-service
	 host_name                    www.monitoring-fr.org
	 check_command                check_mywebsite
	 check_interval               5
	 _CHECKMYID					   95c81e64-48af-4190-acb7-48bd659ea903
}
~~~

C'est dans le service que la macro personnalisée est déclarée pour être ensuite utilisée comme vu précédemment dans la commande Nagios.

### Configuration web

N'oubliez pas de passer le paramètre `escape_html_tags=0` à zéro dans le fichier de configuration `cgi.cfg` pour profiter des liens proposés par le mode étendu.

## Visualisation du résultat en console

![Vue globale des services dans Icinga Classic](../img/posts/checkmyws-nagios-icinga-shinken-plugin/adagios-icinga-services-view.png)

petit focus sur la ligne présentant le résultat du contrôle Check my Website.

![Détail de la ligne de statut dans Icinga Classic](../img/posts/checkmyws-nagios-icinga-shinken-plugin/icinga-services-checkmywebsite.png)

Enfin, le détail du service avec ses nombreuses données de performance présentées dans [Adagios](http://adagios.org/).

![Détail du service vu dans Adagios](../img/posts/checkmyws-nagios-icinga-shinken-plugin/adagios-service-detail-perfdata.png)

## Contribuer aux plugins

Nous sommes particulièrement intéressés par **tous les plugins qui permettent de connecter Check my Website à des logiciels, outils tiers**; que ce soite des services en ligne ou des outils internes. Un pack Shinken est d'ailleurs prêt et ne demande plus qu'à être répertorié sur [Shinken.io](http://shinken.io/).

Ce **premier plugin est bien sûr libre** et vous pouvez trouver le [dépôt Github](https://github.com/checkmyws/checkmyws-plugins) qui a été créé pour l'accueillir, lui et ses futurs nombreux congénères « je l'espère ».

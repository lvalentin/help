---
sharing: true
comments: true
layout: post
title:  "Le point sur la virtualisation Open Source"
date:   2014-06-27 08:00:00 +0100
tags:
- virtualisation
- opensource
author: Olivier Jan
post_img : looking-science.jpg
lead: "Tour guidé des logiciels vous permettant d'accéder à vos rêves les plus fous en matière de virtualisation."
---

La virtualisation et le cloud ont fait un sacré bonhomme de chemin dans l'Open Source depuis une dizaine d'années et les premières versions de Xen. Sont apparus depuis quelques temps; à côté des solutions historiques, un ensemble de nouvelles pièces, outils qui permettent aujourd'hui de penser que **la virtualisation Open Source arrive aujourd'hui à maturité. Revue de détail des possibilités offertes… Et elles sont nombreuses**.

## Virtualisation allégée sans matière grasse

Prenez le concept de « [chroot](http://fr.wikipedia.org/wiki/Chroot) » et portez le à son paroxysme, vous obtiendrez des conteneurs systèmes ou applicatifs en théorie complètement isolés du reste du système maître.

**Une seule instance du noyau Linux tourne pour l'ensemble des machines gérées**. Il n'est pas possible, par exemple, d'exécuter Microsoft® Windows® dans un environnement virtuel au-dessus d'un hôte de type Linux. C'est la forme de virtualisation la plus légère, dont « l'overhead » est le plus réduit.

### OpenVZ

<div class="pull-left img-thumbnail">
![OpenVZ](../img/posts/virtualisation-open-source/openvz-logo.png)
</div>

Quasi figure historique de ce type de virtualisation, OpenVZ est une solution de virtualisation basée sur les conteneurs pour Linux. OpenVZ crée plusieurs conteneurs Linux isolés et sécurisés (autrement connu comme VE ou VPS) sur un seul serveur physique permettant une meilleure utilisation du serveur. 

**Chaque conteneur fonctionne exactement comme un serveur autonome**. Il peut être redémarré indépendamment et a un accès root, des utilisateurs, des adresses IP, de la mémoire, des processus, des fichiers, des applications, des bibliothèques système et des fichiers de configuration.

### LXC

LXC est une interface en espace utilisateur pour confiner les fonctionnalités du noyau Linux. Grâce à une API puissante et des outils simples, LXC permet aux utilisateurs de Linux de créer et gérer facilement des systèmes ou des applications dans des conteneurs.

## Les hyperviseurs : Déjà plus lourd

Il s'agit ici de **para-virtualisation** ou **virtualisation dite complète, avec émulation du matériel sur la machine invitée**. Celles-ci ne partage alors que certains composants avec l'hyperviseur et ses techniques permettent de virtualiser n'importe quel type de systèmes d'exploitation.

### Para-virtualisation

Pour [wikipedia](http://fr.wikipedia.org/wiki/Paravirtualisation), la paravirtualisation est une technique de virtualisation qui présente une interface logicielle similaire à du matériel réel à une machine virtuelle mais optimisée pour ce type de fonctionnement, contrairement à l'émulation d'un périphérique matériel existant qui peut s'avérer laborieuse et surtout lente.

#### Xen Project

<div class="pull-left img-thumbnail">
![Xen](../img/posts/virtualisation-open-source/xen-logo.png)
</div>

Xen est l'hyperviseur historique sur Linux et a été acheté par Citrix depuis. [Xen Project](http://www.xenproject.org) version Open Source complète disponible. Xen est intégré nativement à Linux depuis sa version 3.

#### KVM

<div class="pull-left img-thumbnail">
![KVM](../img/posts/virtualisation-open-source/kvm-logo.png)
</div>

KVM « pour Virtual Machine Kernel-based » est une solution de virtualisation complète pour Linux sur du matériel x86 compatibles « Intel VT ou AMD-V ». Il se compose d'un module de noyau chargeable, `kvm.ko`, qui fournit l'infrastructure de virtualisation de base et un module, `kvm-intel.ko` ou `kvm-amd.ko`, spécifique au processeur utilisé.

Chaque machine virtuelle dispose d'un matériel privé virtualisé: une carte réseau, disque, carte graphique, etc.

KVM est le de-facto standard sur Linux puisque présent dans les sources du noyau depuis la ligne 2.6.20.

### Virtualisation complète

Toujours pour [Wikipedia](http://fr.wikipedia.org/wiki/Virtualisation#Diff.C3.A9rentes_techniques), la virtualisation consiste à faire fonctionner un ou plusieurs systèmes d'exploitation / applications comme un simple logiciel, sur un ou plusieurs ordinateurs - serveurs / système d'exploitation, au lieu de ne pouvoir en installer qu'un seul par machine. Ces ordinateurs virtuels sont appelés serveur privé virtuel (Virtual Private Server ou VPS) ou encore environnement virtuel (Virtual Environment ou VE).

#### Oracle VM VirtualBox

<div class="pull-left img-thumbnail">
![VirtualBox](../img/posts/virtualisation-open-source/virtualbox-logo.png)
</div>

VirtualBox tourne su Windows, Linux, Macintosh, et Solaris et support eun large choix de systèmes invités comme Windows (NT 4.0, 2000, XP, Server 2003, Vista, Windows 7, Windows 8), DOS/Windows 3.x, Linux (2.4, 2.6 and 3.x), Solaris et OpenSolaris, OS/2, et OpenBSD.

## Virtualiser le stockage, le réseau…

Virtualiser des systèmes et applications c'est bien mais pour construire un environnement virtuel complet, **il faut également virtualiser stockage et réseau**. Vous pouvez alors compter dans le monde Open Source sur [Openvswitch](http://openvswitch.org/), le switch virtuel ou [GlusterFS](http://www.gluster.org/about/) et [ceph](http://ceph.com/), les systèmes de gestion de stockage distribué.

## La glue

La principale fonctionnalités de ce que j'appelle « glue » est de **fournir des APIs aux programmeurs et scripteurs pour piloter de façon automatique les technos** de virtualisation vues précédemment.

### Libvirt

<div class="pull-left img-thumbnail">
![Libvirt](../img/posts/virtualisation-open-source/libvirt-logo.png)
</div>

Libvirt est une librairie d'abstraction pour la virtualisation. Celle-ci permet d'adresser d'une façon uniforme les différents hyperviseurs du marché, y compris commerciaux comme VMware.

### Vagrant

<div class="pull-left img-thumbnail">
![Vagrant](../img/posts/virtualisation-open-source/vagrant-logo.png)
</div>

[Vagrant](http://www.vagrantup.com/) est un outil pour créer des environnements de développement complets, privilégiant l'automatisation et le reproductibilité. Nous en avons parlé sur Wooster pour automatiser la création et le provsionnement de [machines pour faire du développement Wordpress](/2014/06/cms-dev-environnement/).<br /><br />

### Docker

<div class="pull-left img-thumbnail">
![Docker](../img/posts/virtualisation-open-source/docker-logo.png)
</div>

[Docker](http://docker.io); dont [nous avons déjà parlé](/2014/03/docker-automatisation-container/), s'appuie sur LXC et propose entre autres de versionner, provisionner les conteneurs gérés.<br /><br />

## Des solutions complètes

Ces solutions, en plus de gérer des machines virtuelles, **gèrent également la partie virtualisation du stockage, du réseau, la haute disponibilité**, bref de tout ce qu'il faut pour arrviver à proposer des services dans le nuage « cloud computing »; que ce soit du [PaaS](http://fr.wikipedia.org/wiki/Plate-forme_en_tant_que_service), [SaaS](http://fr.wikipedia.org/wiki/Logiciel_en_tant_que_service), [IaaS](http://fr.wikipedia.org/wiki/Infrastructure_as_a_service) ou [DaaS](http://fr.wikipedia.org/wiki/Data_as_a_Service) !

Et bien évidemment, elles s'appuient pour le fonctionnmeent des machines virtuelles sur les couches précédemment vues, que ce soit KVM, LXC…

### OpenStack

<div class="pull-left img-thumbnail">
![Openstack](../img/posts/virtualisation-open-source/openstack-logo.png)
</div>

[OpenStack](https://www.openstack.org/) est un logiciel libre qui permet la construction de cloud privé et public. OpenStack est aussi une communauté et un projet en plus d'un logiciel qui a pour but d'aider les organisations à mettre en œuvre un système de serveur et de stockage virtuel.

OpenStack est composé d'une série de logiciels et de projets qui sont maintenu par la communauté incluant: 

- OpenStack Compute (nommé Nova),
- OpenStack Object Storage (nommé Swift),
- OpenStack Image Service (nommé Glance).

### Open Nebula

<div class="pull-left img-thumbnail">
![Open Nebula](../img/posts/virtualisation-open-source/opennebula-logo.png)
</div>

[OpenNebula](http://opennebula.org/) à la différence des solutions de Cloud Computing classiques, fournit une boîte à outils complète permettant de gérer de façon centralisée une infrastructure virtuelle hétérogène.

L’outil est compatible avec les hyperviseurs classiques : Vmware, Xen, KVM. OpenNebula opère comme un ordonnanceur des couches de stockage, réseau, supervision et de sécurité.

C'est une solution adaptée à la conversion d'une infrastructure virtuelle en Plateforme IaaS. Cette fonction d'orchestration centralisée, d'environnements hybrides est le cœur de l'outil.

### Archipel Project

<div class="pull-left img-thumbnail">
![Archipel](../img/posts/virtualisation-open-source/archipel-logo.png)
</div>

Ce qui fait la particularité de [Archipel Project](http://archipelproject.org/) est d'utiliser le **protocole XMPP pour orchestrer les machines virtuelles** et dialoguer avec les différentes pièces du logiciel. Archipel Project s'appuie sur Libvirt et est un projet français tout droit venu de Montpellier.

### Proxmox VE

<div class="pull-left img-thumbnail">
![Proxmox](../img/posts/virtualisation-open-source/proxmox-logo.png)
</div>

[Proxmox](http://www.proxmox.com/fr/) est une solution de gestion de la virtualisation complète pour les serveurs. Elle est basée sur la virtualisation KVM et la virtualisation basée sur des conteneurs OpenVZ. Elle gère les machines virtuelles, stockage, réseaux virtualisés, et HA cluster.

Cette solution est intéressante pour virtualiser rapidement un serveur et offrir la possibilité de le configurer via une interface web graphique. Un plus pour ceux que la ligne de commande rebute.

## Trouver chaussure à son pied

Le plus dur finalement est de **trouver la bonne combinaison pour le contexte à virtualiser**. Si vous ne manipuler que des hôtes Linux comme nous chez Check my Website, le conteneur est certainement un très bon choix.

VMware a fini de manger son pain blanc ! Les logiciels Open Source sont prêts à en découdre avec une solution qui pèse de plus en plus lourd sur le budget des SI.

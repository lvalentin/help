---
sharing: true
comments: true
layout: post
title:  "Packer, Vagrant, VirtualBox : Trio gagnant pour le développement"
date:   2014-06-03 09:00:00 +0100
tags:
- opensource
- automatisation
author: Olivier Jan
post_img : wonderfull-world.jpg
lead: "Comment se mitonner un environnement de développement aux petits oignons pour Wordpress, Drupal, Joomla ou tout autre CMS ?"
---

S'il y a bien un **défi quotidien auquel doit faire face tout développeur, designer web, c'est son environnement de développement**. Comment retrouver un environnement consistant, que vous travailliez sur Windows, OSX ou Linux ? Et quand les équipes de développement s'aggrandissent, comment être certain que tous les **développeurs travaillent sur un environnement identique** ?

Je vais donc vous présenter un workflow composé d'outils Open Source vous permettant de **construire automatiquement et de façon reproductible un environnement de développement consistant** pour l'ensemble de vos développeurs.

Je précise que je découvre ces outils et qu'il y a sûrement moyen de faire mieux que ce qui suit. Il faut donc considérer ceci comme une base à améliorer. Les configurations étant partagées sur [Github](https://github.com/checkmyws/v-apps), vous pouvez participer.

Je vais illustrer le propos en prenant l'exemple d'un blog Wordpress.

## Les logiciels nécessaires

Au rayon des logiciels nécessaires, vous allez devoir mettre la main sur :

- [VirtualBox](https://www.virtualbox.org) est un système de virtualisation tombé dans l'escarcelle de Oracle et qui permet de virtualiser à peu près n'importe quel type de système d'exploitation. C'est le VMware du desktop !
- [Packer](http://www.packer.io/) est un logiciel pour créer des images machines identiques pour différentes plate-formes à partir d'un unique fichier de configuration. Il a été créé par la même personne à qui nous devons Vagrant.
- [Vagrant](http://www.vagrantup.com/) permet de créer et de configurer des environnements de développement légers, portables et reproductibles.

La nature étant bien faite, ces **trois logiciels fonctionnent sur les tous les OS majeurs**, ce qui fait que quelque chose de commencé sur Windows pourra être continué sur Linux ou OSX. De plus, l'installation est sans souci. N'oubliez pas l'indispensable Git pour versionner votre code, mais cela va de soi !

## Préparer un système type avec Packer

Wordpress fonctionne plutôt nativement sur Linux même si c'est possible de faire autrement en utilisant tout un tas d'artifice. Nous allons donc **préparer une machine contenant un système Ubuntu 14.04 64 bits fraîchement installé**.

C'est Packer qui va nous assurer :

1. L'installation automatique de Ubuntu à partir de l'ISO officielle. Ce type d'installation porte le doux nom de « unattended installation ».
2. L'adapation de cette installation à nos exigences personnelles ou à des contraintes d'entreprise.
3. La préparation d'une « box » au format Vagrant qui nous servira de base pour constituer notre machine virtuelle Wordpress.

Vous pouvez suivre la [doc d'installation Packer](/doc/packer/) sur linux si vous le souhaitez. Cette partie est optionnelle, vous pouvez utiliser des systèmes types prêts à l'emploi sur [Vagrant Cloud](https://vagrantcloud.com/) comme nous le verrons plus bas.

### Configuration de la construction de la machine

Voici le fichier trusty64.json qui doit se trouver à la racine du dossier qui va servir pour le « build », la construction de notre machine virtuelle Ubuntu.

~~~
{
  "variables": {
  },
  "builders": [{
    "type": "virtualbox-iso",
    "name": "trusty64",
    "guest_os_type": "Ubuntu_64",
    "iso_url": "http://releases.ubuntu.com/trusty/ubuntu-14.04-server-amd64.iso",
    "iso_checksum": "01545fa976c8367b4f0d59169ac4866c",
    "iso_checksum_type": "md5",
    "guest_os_type": "Ubuntu_64",
    "http_directory": "http",
    "disk_size": "20000",
    "hard_drive_interface": "sata",
    "ssh_username": "vagrant",
    "ssh_password": "vagrant",
    "ssh_wait_timeout": "1200s",
    "shutdown_command": "echo 'vagrant' | sudo -S shutdown -P now",
    "boot_command": [
        "<esc><esc><enter><wait>",
        "/install/vmlinuz noapic ",
        "preseed/url=http://{{ .HTTPIP }}:{{ .HTTPPort }}/preseed.cfg ",
        "debian-installer=en_US auto locale=en_US kbd-chooser/method=USA ",
        "hostname={{ .Name }} ",
        "fb=false debconf/frontend=noninteractive ",
        "keyboard-configuration/modelcode=SKIP keyboard-configuration/layout=USA ",
        "keyboard-configuration/variant=USA console-setup/ask_detect=false ",
        "netcfg/choose_interface=auto ",
        "initrd=/install/initrd.gz -- <enter>"
    ],
    "vboxmanage": [
        ["modifyvm", "{{.Name}}", "--memory", "512"],
        ["modifyvm", "{{.Name}}", "--cpus", "1"],
        ["modifyvm", "{{.Name}}", "--natpf1", "ssh,tcp,127.0.0.1,2222,,22"],
        ["modifyvm", "{{.Name}}", "--macaddress2", "auto"],
        ["modifyvm", "{{.Name}}", "--nic2", "hostonly"],
        ["modifyvm", "{{.Name}}", "--hostonlyadapter2", "vboxnet2"]

    ]
  }],
    "provisioners": [{
    "type": "shell",
    "execute_command": "echo 'vagrant' | {{ .Vars }} sudo -E -S sh '{{ .Path }}'",
    "script": "./post-install.sh"
  }],
  "post-processors": [{
    "type": "vagrant",
    "compression_level": "4",
    "keep_input_artifact": true
  }]
}
~~~

Il est découpé en 4 grandes parties :

- `variables` permet comme son nom l'indique d'assigner des variables qui seront ensuite utilisées pendant le build. Non utilisé dans notre exemple.
- `builders` permet de préciser le type de machines qui va être construite. Dasn cet exemple, nous construisons une machine `virtualbox-iso` portant le nom de `trusty64`.
- `provisioners` permet de préciser comment la machine va être provisionnée. Dans le contexte qui nous intéresse, le provisionnement permet d'adapter l'installation standard de Ubuntu à nos goûts et couleurs. C'est un script externe appelé `post-install.sh` qui va être utilisé.
- `post-processors` permet de préciser des traitements à effectuer sur la machine virtuelle construite. Dans cet exemple, packer va construire une machine virtuelle VirtualBox et ensuite, construire à partir de celle-ci une image de base pour Vagrant.

Packer va donc démarrer une machine virtuelle dans VirtualBox, installer l'OS depuis l'ISO, rebooter la machine et procéder au provisionnement de celle-ci via le script [post-install.sh](https://github.com/checkmyws/v-apps/blob/master/ubuntu-trusty64/post-install.sh).

### Construction du socle de base

Une fois ce fichier en place, la magie opère :

	packer validate trusty64.json
	
permet comme son nom l'indique de valider la syntaxe du fichier de configuration de la machine à construire.

Enfin un

	packer build trusty64.json
	
vous fait tout le boulot d'une installation Ubuntu depuis l'ISO en automatique. Il n'y a **qu'à s'assoir et regarder le job se faire**. Et ça, c'est bien ! Il n'y a plus acune raison de préparer une machine virtuelle à la main avec ceci.

Vous obtenez alors au bout de 5, 10mn un dossier `output-trusty64` dans votre répertoire de départ contenant un fichier `packer-trusty64.ovf` et le disque dur associé `packer-trusty64-disk1.vmdk`. Vous pouvez importer cette machine dans VirtualBox tel que si vous le souhaitez.

Néanmoins, notre post-processor nous a également générer un fichier `packer_trusty64_virtualbox.box` qui peut servir d'image de base à Vagrant. Et il serait dommage de se priver de la puissance de celui-ci pour gérer notre environnement au quotidien.

## Installer et gérer Wordpress avec Vagrant

Vagrant **va utiliser cette base générée par Packer et la compléter pour arriver à une machine virtuelle Wordpress** qui n'attend plus que vos renseignements personnels pour commencer à être utilisée.

Vagrant va assurer :

1. Le démarrage d'une machine virtuelle VirtualBox correctement configurée avec les VBox Additions à partir d'une image générée par Packer ou directement depuis les dépôts publics.
2. Le provisionnement de cette machine virtuelle avec une installation prête à l'emploi de Wordpress.

Vagrant va aussi permettre de gérer la vie de cette machine virtuelle de façon simple comme nous allons le voir.

### Configuration de Vagrant à partir de votre image Packer

Il faut commencer par **créer un squelette de fichier de configuration** en indiquant à Vagrant à partir de quelle image initialiser celui-ci.
	
	vagrant init packer_trusty64_virtualbox.box
	
Vous avez alors un fichier `Vagrantfile` à la racine de votre dossier de départ comme dans le [dossier du projet sur Github](https://github.com/checkmyws/v-apps/tree/master/wordpress).

J'ai modifié ce fichier afin d'obtenir au final ce qui suit, débarassé des lignes commentées.

~~~
VAGRANTFILE_API_VERSION = "2"

Vagrant.configure(VAGRANTFILE_API_VERSION) do |config|
  config.vm.box = "./packer_trusty64_virtualbox.box"
  config.vm.hostname = "cmws-wordpress"
  config.vm.network "private_network", ip: "192.168.56.100"
  config.vm.provision :file do |file|
    file.source      = './files'
    file.destination = '/home/vagrant/'
  end
  config.vm.provision "shell", path: "post-install.sh"
end
~~~

La syntaxe est celle de Ruby puisque Vagrant est construit en Ruby. Peu de choses en fait dans ce fichier.

- `config.vm.box` indique l'image de base à utiliser pour construire une nouvelle machine virtuelle.
- `config.vm.hostname` indique le nom de cette machine.
- `config.vm.network` permet de préciser les réglages réseaux souhaité pour la machine. Dans cet exemple, nous démarrons un réseau privé hôte avec une assignation d'IP fixe à `192.168.56.100`.

**Deux lignes un peu plus particulières permettent de préciser comment va être fait le provisionnement de la machine**. Dans un premier temps, le dossier `files` présent à la racine du dossier projet va être transféré vers la machine virtuelle et ensuite le script `post-install.sh` sera exécuté dans la machine. C'est finalement la même logique que Packer exprimé différemment.

Le dossier `files` contient les fichiers de configuration pour Nginx et Wordpress et le script `post-install.sh` se charge de faire une installation basique de Wordpress.

###  Configuration de Vagrant à partir d'une image publique

Si **vous ne souhaitez pas construire le socle de base avec Packer**, vous pouvez pointer le paramètre `config.vm.box` vers une des nombreuses machines mises à disposition sur le [dépôt publique Vagrant](https://vagrantcloud.com/) comme l'exemple ci-dessous.

	config.vm.box = "ubuntu/trusty64"

Vous allez alors utiliser l'image officielle Ubuntu Trusty64 du dépôt publique Vagrant. Le reste du fichier `Vagrantfile` ne change pas.

### Gestion du cycle de vie de la machine

Le fichier Vagrantfile d'applomb, ne reste plus qu'à démarrer la machine virtuelle avec

	vagrant up
	
Cett simple commande va :

1. Aller chercher une image de base pour préparer une nouvelle machine.
2. Mettre en place la configuration réseau pour la machine
3. Installer les VirtualBox Additions
4. Provisionner la machine
5. Démarrer la machine en mode headless par défaut.

Il suffit ensuite de faire 

	vagrant ssh
	
pour se connecter en SSH sur la machine.

Pour vérifier que l'installation et le provisionnement se sont bien passés, rendez-vous sur `http://192.168.56.100`.

![Wordpress prêt à être utilisé](../img/posts/cms-dev-environnement/wordpress-install-screen.png)

Vous n'avez plus qu'à renseigner l'installation de Wordpress pour commencer à bloguer. Elle est pas belle la vie ?

Pour stopper une machine virtuelle, un simple

	vagrant halt
	
peut suffire et enfin un 

	vagrant destroy
	
vous permet de supprimer complètement la machine virtuelle après usage.

## Conclusion

Si vous en avez **marre de toujours construire des machines virtuelles « from scratch »** pour chacun de vos projets; alors Packer, Vagrant sont faits pour vous.

D'autant que Vagrant **peut se marier avec [Docker](/2014/03/docker-automatisation-container/), Puppet, Chef, Salt, CFEngine ou Ansible pour le provisionnement**. Bref, tout ce qui existe en matière de provisionnement Open Source !

Enfin, rien n'empêche d'embarquer dans cette machine le workflow [Yeoman](/2013/12/yeoman-grunt-bower-workflow/) déjà vu sur Wooster pour toujours plus de puissance et performance.

Je pense améliorer la machine virtuelle Wordpress en ce sens et proposer dans le cadre de la reprise d'un ancien projet des **machines prêtes à l'emploi pour les principaux CMS du marché** (Joomla, Drupal, Prestashop, Magento…). N'hésitez pas à me rejoindre si le cœur vous en dit !

Vous n'avez pas fini d'entendre parler de ces technos sur Wooster !

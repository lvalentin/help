---
sharing: true
comments: true
layout: post
title:  "Les scénarios applicatifs : Selenium, Watir, Slimerjs and cie"
date:   2014-07-04 08:00:00 +0100
tags:
- eue
- opensource
- checkmyws
author: Olivier Jan
post_img : win1.png
lead: "La capacité d'exécuter des scénarios fonctionnels dans un navigateur est la fonctionnalité la plus demandée."
---

Partout ou nous passons, partout ou nous faisons des démonstrations de Check my Website et de sa console, partout la même question :

> Quand pourrons-nous exécuter des scénarios utilisateur avec Check my Website ?

A question simple, réponse pas si simple que cela comme nous allons le voir.

## Scénario fonctionnel : De quoi parle t'on ?

Par scénario fonctionnel, applicatif ou utilisateur, il est d'usage de désigner l'**ensemble des mécanismes et technologies permettant de scripter un navigateur de façon à le faire rejouer des séquences d'actions sur un site web automatiquement**.

C'est un peu comme si **vous passiez sur votre site web toutes les heures** pour vérifier que la recherche fonctionne, que les clients peuvent mettre un produit dans le panier, et plus important l'acheter et le payer, etc.

## Piloter un navigateur : La technique est une chose

Côté technique, une fois de plus dans l'Open Source, il y a de quoi faire. Du plus connu comme [Selenium HQ](http://docs.seleniumhq.org/) au petit dernier comme [Dalek.js](http://dalekjs.com/) ou [Slimer.js](http://slimerjs.org/), qui est le pendant Firefox de [PhantomJS](http://phantomjs.org/) pour Webkit. Ces deux derniers se pilotent avec [CasperJS](http://casperjs.org/).

Si vous êtes plutôt Ruby que Javascript, regardez du côté du désormais classique [Watir](http://watir.com/).

Certains de ces logiciels fonctionnent en mode dit "headless", c'est à dire sans lancer réellement un navigateur mais en utlisant son moteur de rendu alors que **d'autres nécessitent un serveur graphique pour fonctionner**. Le navigateur est alors rééllement exécuté sur le robot de test.

Heureusement, il existe pour Linux [Xvfb](http://www.x.org/archive/X11R7.7/doc/man/man1/Xvfb.1.xhtml) « X virtual framebuffer ». Contrairement à d'autres serveurs d'affichage, **Xvfb effectue toutes les opérations graphiques en mémoire sans montrer aucune sortie écran**. Vous n'avez donc pas besoin d'installer un serveur X complet pour lancer le navigateur.

### Nos premiers essais

Nous commençons à tester certains des logiciels cités ci-dessus et la vidéo suivante est **un test fonctionnel de la console Check my Website réalisé avec CasperJS + Slimer.js**.

<video width="720" height="480" controls>
  <source src="/assets/video/posts/casper-slimer.mp4" type="video/mp4">
  <source src="/assets/video/posts/casper-slimer.webm" type="video/webm">
Your browser does not support the video tag.
</video>

C'est ce genre de vidéo que vous pourriez retrouver un jour directement dans la console Check my Website !

## Et la facilité d'utilisation une autre

Mais avant que cela ne se produise, nous devons réussir **le challenge de vous permettre d'utiliser ses logiciels sans vous transformer en expert DOM, HTML, Javascript**. Et ça, c'est une autre paire de manches !

### L'enregistrement automatiques des actions

Nous pourrions, à l'instar de Selenium HQ, proposer une **extension au navigateur permettant d'enregistrer toutes les actions faites dans le navigateur**.

Cette méthode présente souvent l'inconvénient de devoir éditer les scripts générés par l'enregistrement fait dans le navigateur afin de les nettoyer ou de les enrichir.

Alors, pourquoi ne pas tout faire à la main ?

### Le codage à la main des actions

Nous pourrions vous proposer **l'upload d'un script rédigé à la main, avec amour, pour être exécuté sur nos robots**.

Voici un extrait du script utilisé pour tester une recherche sur Google (source: [CasperJS](http://docs.casperjs.org/en/latest/quickstart.html#now-let-s-scrape-google)).

~~~
var links = [];
var casper = require('casper').create();

function getLinks() {
    var links = document.querySelectorAll('h3.r a');
    return Array.prototype.map.call(links, function(e) {
        return e.getAttribute('href');
    });
}

casper.start('http://google.fr/', function() {
    // search for 'casperjs' from google form
    this.fill('form[action="/search"]', { q: 'casperjs' }, true);
});

casper.then(function() {
    // aggregate results for the 'casperjs' search
    links = this.evaluate(getLinks);
    // now search for 'phantomjs' by filling the form again
    this.fill('form[action="/search"]', { q: 'phantomjs' }, true);
});

casper.then(function() {
    // aggregate results for the 'phantomjs' search
    links = links.concat(this.evaluate(getLinks));
});

casper.run(function() {
    // echo results in some pretty fashion
    this.echo(links.length + ' links found:');
    this.echo(' - ' + links.join('\n - ')).exit();
});
~~~

Pas forcément super trivial à écrire !

### Couper la poire en deux

La dernière méthode qui pourrait être proposée est à mi-chemin entre les deux autres : **Proposer un environnement d'édition dédié aux scripts de type scénarios web**.

Il vous resterait alors à préciser uniquement les actions et les objets sur lesquels celles-ci s'appliquent comme cet écran ci-dessous que j'ai trouvé sur le service en ligne [Ghost Inspector](https://ghostinspector.com/).

![Édition d'un script dans l'IDE](../img/posts/end-user-monitoring-scenarios/ide-edition.gif)

## Conclusion temporaire

**Les scénarios sont une fonctionnalité importante pour tous ceux voulant tester les fonctionnalités, le bon fonctionnement d'un site web**. Il est donc normal que Check my Website, dont la vocation est de vous fournir tous les outis nécessaires au monitoring complet de votre site aille vers ce type de "produit", au même titre que le « Real User Monitoring » qui fera l'objet d'un autre billet sur Wooster.

**Reste à savoir comment nous allons vous proposer cette fonctionnalité** pour qu'elle soit facilement utilisable. Extension au navigateur ? Upload de scripts faits à la main ? Un mix des deux ? Seul l'avenir nous le dira. D'ici là, **n'hésitez pas à exprimer vos souhaits en la matière**, les commentaires sont faits pour ça !

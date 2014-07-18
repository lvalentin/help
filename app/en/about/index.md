---
layout: page
title: "À propos de Wooster"
lead: "Wooster est un blog pour wooster vos sites web, vos web apps et vos services web."
locale: "en"
---

## Wooster ?

Wooster est un blog, un magazine traitant de tout ce qui peut permettre à votre site, application, service web d'être "[harder, faster, stronger](http://www.youtube.com/watch?v=PsO6ZnUZI0g)". En clair et dans la langue de Molière, un site **plus rapide, plus disponible, plus sûr, plus agréable pour vos visiteurs**, plus, plus… ! 

*Wooster est une expression* que nous avons inventée à cet effet: **Woost**. Vous woostez quand vous b**oost**ez votre site **w**eb. Wooster a ouvert ses portes le *20 novembre 2013*.

- premier
- deuxième
- troisième

## Check my Website ?

Wooster est publié par la société en cours de création [Check My Website](http://www.checkmy.ws), spécialisée dans le **monitoring, la performance et la supervision des sites, apps et services web**.

Check My Website a été fondé par William Pain et [Olivier Jan](https://plus.google.com//u/0/+OlivierJan), tous deux experts reconnus dans le monde de la supervision et de l'administration système et réseaux. Olivier est notamment le co-fondateur de la [Communauté Francophone de la Supervision Libre](http://www.monitoring-fr.org) et l'auteur du [premier livre en français sur Nagios](http://www.editions-eni.fr/livres/nagios-au-coeligur-de-la-supervision-open-source-de-l-installation-a-l-optimisation/.65970a2f611efce1b92dfd6996cf2ef5.html).

## Que propose Wooster ?

Des **news, articles de fond, analyses, tests et essais, retours d'expériences** autour des sujets qui nous passionnent, préoccupent chez Check My Website; et ils sont nombreux. 

Que ce soient les **logiciels Open Source, les services de type SAAS**, la construction de site web, les systèmes de publication en ligne, les systèmes de gestion de contenu, l'automatisation des infrastructures… 

Vous pourrez également retrouver régulièrement **des nouvelles sur les services en ligne que nous proposons** depuis le *13 février 2014* ainsi que les trucs et astuces pour les utiliser au mieux…

### Pourquoi des visuels « vintage » ?

Même un blog orienté contenu textuel comme Wooster se doit de nos jours d'avoir des visuels pour égayer ses pages. 

<pre><code class="language-text" data-lang="text">var links = [];
var casper = require(&#39;casper&#39;).create();

function getLinks() {
    var links = document.querySelectorAll(&#39;h3.r a&#39;);
    return Array.prototype.map.call(links, function(e) {
        return e.getAttribute(&#39;href&#39;);
    });
}

casper.start(&#39;http://google.fr/&#39;, function() {
    // search for &#39;casperjs&#39; from google form
    this.fill(&#39;form[action=&quot;/search&quot;]&#39;, { q: &#39;casperjs&#39; }, true);
});

casper.then(function() {
    // aggregate results for the &#39;casperjs&#39; search
    links = this.evaluate(getLinks);
    // now search for &#39;phantomjs&#39; by filling the form again
    this.fill(&#39;form[action=&quot;/search&quot;]&#39;, { q: &#39;phantomjs&#39; }, true);
});

casper.then(function() {
    // aggregate results for the &#39;phantomjs&#39; search
    links = links.concat(this.evaluate(getLinks));
});

casper.run(function() {
    // echo results in some pretty fashion
    this.echo(links.length + &#39; links found:&#39;);
    this.echo(&#39; - &#39; + links.join(&#39;\n - &#39;)).exit();
});
</code></pre>

Alors plutôt que d'illustrer nos billets et articles d'images « passe partouts », nous avons pris le parti d'illustrer nos billets avec des **objets, personnages venant d'années où l'avenir rempli de robots et de mécaniques était vu comme le fantasme** ultime d'une société en pleine évolution… 

Les années 1950 à 1970 en quelque sorte ! C'est aussi l'occasion de rappeler que si nous sommes tourné vers l'avenir, nous n'en oublions pas le passé.

### Sous quelles conditions ?

<a rel="license" href="http://creativecommons.org/licenses/by-nc-sa/3.0/deed.fr"><img alt="Licence Creative Commons" class="pull-left img-thumbnail image" src="http://i.creativecommons.org/l/by-nc-sa/3.0/88x31.png" /></a><span xmlns:dct="http://purl.org/dc/terms/" property="dct:title">Wooster</span> de <a xmlns:cc="http://creativecommons.org/ns#" href="http://www.checkmy.ws" property="cc:attributionName" rel="cc:attributionURL">Check My Website</a> est mis à disposition selon les termes de la <a rel="license" href="http://creativecommons.org/licenses/by-nc-sa/3.0/deed.fr">licence Creative Commons Attribution - Pas d’Utilisation Commerciale - Partage dans les Mêmes Conditions 3.0 non transposé</a>.

N'hésitez pas à nous contacter si vous souhaitez utiliser un des contenus présents sur ce site.

### L’information est-elle à jour ?

Nous faisons notre maximum pour maintenir les informations de ce site à jour. N'hésitez pas à nous signaler tout contenu qui ne vous semblerait pas exact ou à jour.

### Colophon

Wooster n'est constitué qu'à partir d'ingrédients soigneusement sélectionnés comme Jekyll, le générateur de sites statiques; JQuery, Twitter Booststrap, HTML5.

Nous utilisons pour Wooster des photos et illustrations que nous pensons libres de droits. Si vous trouvez une photo ou illustration qui ne l'est pas à votre connaissance, merci de nous le signaler afin que nous puissions prendre les dispositions qui s'imposent.

## Comment participer à Wooster ?

Tout le monde peut participer à Wooster. Il suffit d'avoir un compte Github. Le dépôt sur lequel vous devez vous baser est [Wooster de Check my Website](https://github.com/checkmyws/wooster). 

Ce dépôt est public et vous permet de demander un « pull request » de ce que vous avez écrit et que vous aimeriez voir publier sur Wooster.

### Prenez part à la conversation ! 

Si vous ne vous sentez pas l'âme d'un auteur, un commentaire permet toujours d'enrichir un billet par des exemples vécus, des compléments d'informations, des liens en relation, des avis partagés ou contraires.

N'hésitez pas à entrer en contact avec nous pour plus d'informations sur comment participer.

## Comment contacter les auteurs du site ?

Nous sommes par nature des êtres sociaux et sommes toujours ravis d'échanger avec vous, sur quelque sujet que ce soit. Vous pouvez nous joindre à l'adresse <a href="http://www.google.com/recaptcha/mailhide/d?k=01magYtAcWm9WYtQGdfnI-eg==&amp;c=eltGu3aXUz1PdmzQSlBi0LBoC7JS4XCL_pZBfa9kp4A=" onclick="window.open('http://www.google.com/recaptcha/mailhide/d?k\07501magYtAcWm9WYtQGdfnI-eg\75\75\46c\75eltGu3aXUz1PdmzQSlBi0LBoC7JS4XCL_pZBfa9kp4A\075', '', 'toolbar=0,scrollbars=0,location=0,statusbar=0,menubar=0,resizable=0,width=500,height=300'); return false;" title="Voir l'adresse e-mail">woo…</a>@checkmy.ws ou nous contacter via le site [Check My Website](http://www.checkmy.ws).

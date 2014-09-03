---
sharing: true
comments: true
layout: page
title:  "YSlow"
date:   2014-06-12 08:00:00 +0100
locale: "fr"
permalink: /fr/console/website-yslow/
lead: "Page qui propose de montrer comment votre site web performe par rapport aux règles YSlow. Les régles YSlow sont un ensemble de bonnes pratiques pour améliorer la performance de son site web."
weight: "007"
---

## Qu'est-ce que sont les règles YSlow ?

Comme mentionné sur le [site officiel YSlow](http://yslow.org/),

> Yahoo!'s Exceptional Performance team has identified 34 rules that affect web page performance. YSlow's web page analysis is based on the 23 of these 34 rules that are testable. Studies have shown that web page response time can be improved by 25% to 50% by following these rules.

Les règle ssont organisées en jeux de règles. Il y a trois jeux de règles pour le moment :

- YSlow(V2) - Ce jeu de règles comporte 23 règles énumérées ci-dessous.
- Classic(V1) - Ce jeu de règles comporte 13 règles énumérées ci-dessous.
- Petit Site ou Blog - Ce jeu de règles comporte 14 règles énumérées ci-dessous et applicable à un petit site ou un blog.

Ce tableau résume quelle règle dans quel jeu de règles. Cliquez une règle pour avoir le détail de cette règle.

<table class="table table-striped"><thead><tr><th align=left>Règle</th><th align=center>YSlow V2</th><th align=center>YSlow V1</th><th align=center>Small site/blog</th></tr></thead><tbody><tr><td align=left><a target="_blank" href=http://checkmyws.github.io/yslow-rules/fr/#ynumreq>Réduire le nombre de requêtes HTTP</a></td><td align=center><i class="fa fa-check-circle"></i></td><td align=center><i class="fa fa-check-circle"></i></td><td align=center><i class="fa fa-check-circle"></i></td></tr><tr><td align=left><a target="_blank" href=http://checkmyws.github.io/yslow-rules/fr/#ycompress>Compresser avec Gzip les composants</a></td><td align=center><i class="fa fa-check-circle"></i></td><td align=center><i class="fa fa-check-circle"></i></td><td align=center><i class="fa fa-check-circle"></i></td></tr><tr><td align=left><a target="_blank" href=http://checkmyws.github.io/yslow-rules/fr/#yexpressions>Éviter les expressions CSS</a></td><td align=center><i class="fa fa-check-circle"></i></td><td align=center><i class="fa fa-check-circle"></i></td><td align=center><i class="fa fa-check-circle"></i></td></tr><tr><td align=left><a target="_blank" href=http://checkmyws.github.io/yslow-rules/fr/#yminify>Minimifier JavaScript et CSS</a></td><td align=center><i class="fa fa-check-circle"></i></td><td align=center><i class="fa fa-check-circle"></i></td><td align=center><i class="fa fa-check-circle"></i></td></tr><tr><td align=left><a target="_blank" href=http://checkmyws.github.io/yslow-rules/fr/#yetags>Configurer les ETags</a></td><td align=center><i class="fa fa-check-circle"></i></td><td align=center><i class="fa fa-check-circle"></i></td><td align=center></td></tr><tr><td align=left><a target="_blank" href=http://checkmyws.github.io/yslow-rules/fr/#ymindom>Réduire le nombre d’éléments du DOM</a></td><td align=center><i class="fa fa-check-circle"></i></td><td align=center></td><td align=center><i class="fa fa-check-circle"></i></td></tr><tr><td align=left><a target="_blank" href=http://checkmyws.github.io/yslow-rules/fr/#ycookiefree>Utiliser des domaines sans cookies</a></td><td align=center><i class="fa fa-check-circle"></i></td><td align=center></td><td align=center></td></tr><tr><td align=left><a target="_blank" href=http://checkmyws.github.io/yslow-rules/fr/#yfavicon>Faire un petit favicon.ico et le rendre cachable</a></td><td align=center><i class="fa fa-check-circle"></i></td><td align=center></td><td align=center><i class="fa fa-check-circle"></i></td></tr><tr><td align=left><a target="_blank" href=http://checkmyws.github.io/yslow-rules/fr/#cdn>Utiliser un réseau de diffusion de contenu (CDN)</a></td><td align=center><i class="fa fa-check-circle"></i></td><td align=center><i class="fa fa-check-circle"></i></td><td align=center></td></tr><tr><td align=left><a target="_blank" href=http://checkmyws.github.io/yslow-rules/fr/#ycsstop>Mettre les feuilles de style en début de page</a></td><td align=center><i class="fa fa-check-circle"></i></td><td align=center><i class="fa fa-check-circle"></i></td><td align=center><i class="fa fa-check-circle"></i></td></tr><tr><td align=left><a target="_blank" href=http://checkmyws.github.io/yslow-rules/fr/#yexternal>Rendre JavaScript et les CSS externes</a></td><td align=center><i class="fa fa-check-circle"></i></td><td align=center><i class="fa fa-check-circle"></i></td><td align=center></td></tr><tr><td align=left><a target="_blank" href=http://checkmyws.github.io/yslow-rules/fr/#yredirects>Éviter les redirections</a></td><td align=center><i class="fa fa-check-circle"></i></td><td align=center><i class="fa fa-check-circle"></i></td><td align=center><i class="fa fa-check-circle"></i></td></tr><tr><td align=left><a target="_blank" href=http://checkmyws.github.io/yslow-rules/fr/#yxhr>Rendre les requêtes Ajax cachables</a></td><td align=center><i class="fa fa-check-circle"></i></td><td align=center></td><td align=center></td></tr><tr><td align=left><a target="_blank" href=http://checkmyws.github.io/yslow-rules/fr/#yno404>Éviter les erreurs 404</a></td><td align=center><i class="fa fa-check-circle"></i></td><td align=center></td><td align=center><i class="fa fa-check-circle"></i></td></tr><tr><td align=left><a target="_blank" href=http://checkmyws.github.io/yslow-rules/fr/#ynofilter>Éviter les filtres</a></td><td align=center><i class="fa fa-check-circle"></i></td><td align=center></td><td align=center><i class="fa fa-check-circle"></i></td></tr><tr><td align=left><a target="_blank" href=http://checkmyws.github.io/yslow-rules/fr/#yemptysrc>Éviter les balises image src vides</a></td><td align=center><i class="fa fa-check-circle"></i></td><td align=center></td><td align=center><i class="fa fa-check-circle"></i></td></tr><tr><td align=left><a target="_blank" href=http://checkmyws.github.io/yslow-rules/fr/#yexpires>Ajouter des en-têtes Expires</a></td><td align=center><i class="fa fa-check-circle"></i></td><td align=center><i class="fa fa-check-circle"></i></td><td align=center></td></tr><tr><td align=left><a target="_blank" href=http://checkmyws.github.io/yslow-rules/fr/#yjsbottom>Mettres les scripts en bas de page</a></td><td align=center><i class="fa fa-check-circle"></i></td><td align=center><i class="fa fa-check-circle"></i></td><td align=center><i class="fa fa-check-circle"></i></td></tr><tr><td align=left><a target="_blank" href=http://checkmyws.github.io/yslow-rules/fr/#ydns>Réduire le nombre de résolutions DNS</a></td><td align=center><i class="fa fa-check-circle"></i></td><td align=center><i class="fa fa-check-circle"></i></td><td align=center><i class="fa fa-check-circle"></i></td></tr><tr><td align=left><a target="_blank" href=http://checkmyws.github.io/yslow-rules/fr/#ydupes>Supprimer les scripts en doublons</a></td><td align=center><i class="fa fa-check-circle"></i></td><td align=center><i class="fa fa-check-circle"></i></td><td align=center><i class="fa fa-check-circle"></i></td></tr><tr><td align=left><a target="_blank" href=http://checkmyws.github.io/yslow-rules/fr/#yxhrmethod>Utiliser GET pour les requêtes Ajax</a></td><td align=center><i class="fa fa-check-circle"></i></td><td align=center></td><td align=center></td></tr><tr><td align=left><a target="_blank" href=http://checkmyws.github.io/yslow-rules/fr/#ymincookie>Réduire la taille des cookies</a></td><td align=center><i class="fa fa-check-circle"></i></td><td align=center></td><td align=center></td></tr><tr><td align=left><a target="_blank" href=http://checkmyws.github.io/yslow-rules/fr/#yimgnoscale>Ne pas mettre à l’échelle les images en HTML</a></td><td align=center><i class="fa fa-check-circle"></i></td><td align=center></td><td align=center><i class="fa fa-check-circle"></i></td></tr></tbody></table>

## Les règles YSlow dans la console Check my Website

Cette page montre comment votre site web se comporte au regard de ces règles.

![Règles YSlow dans la console Check my Website](/assets/img/fullsize/en/console/website-yslow/yslow.png)

Il y a trois parties que nous allons détailler maintenant.

### Le score et le graphique de score

Le badge à gauche indique le score qu ele site web obtient au regard des règles YSlow, par exemple *95*, et le grade, par exemple *A*.

La couleur du badge est verte quand le score est bon, orange quand il y a de la place aux améliorations et rouge quand le site ne devrait meêm **pas être mis** en production. C'est une juste une expression, ne la prenez pas trop au sérieux !
Cela dit, vous devriez demander à vos développeurs de bosser sur l'optimisation de votre site web si votre score est sous *C*.

Regardez la page de la matrice de référence pour comprendre comment le score et le grade sont calculés.

![Score YSlow dans la console Check my Website](/assets/img/fullsize/en/console/website-yslow/score-graph.png)

Le graphique montre l'évolution du score au cours du temps. Pratique pour voir une régression faîte au niveau du code du site web… Ou mieux, les améliorations apportées !

### Le panneau général

Le panneau général est une vue rapide sur la distribution des différents composants par famille « CSS, HTML, medias and Javascript ».

![Panneau général YSlow dans la console Check my Website](/assets/img/fullsize/en/console/website-yslow/general.png)

Pour chaque famille de composants, vous avez le nombre de composants requêtés et le poids total de ces composants.

### Le résumé des règles

Ce résumé des règles vous permet de voir les améliorations qui peuvent être faites pour augmenter votre score et grade YSlow au regard du jeu de règles sélectionné. Vous pouvez changer de jeu de règles dans la [page des préférences](/fr/console/website-settings/) de votre site web.

![Résumé des règles YSlow dans la console Check my Website](/assets/img/fullsize/en/console/website-yslow/rules.png)

Il y a principalement deux améliorations qui peuvent être à cette page pour viser le score parfait, qui est 100. Réduire le nombre de requêtes HTTP et un coup de GZip sur les composants côté serveur peut aider. Cliquez sur une règle pour avoir des explications complètes de ce qui peut être fait pour cette règle. Voyez dessous pour une exemple.

Cliquez sur `Afficher la liste entière…` pour voir toutes les règles applicables à un jeu de règles.

![Résumé (détail) des règles YSlow dans la console Check my Website](/assets/img/fullsize/en/console/website-yslow/rules-expanded.png)

Cliquez sur `Afficher uniquement les mauvais scores…` pour focaliser sur les choses à faire.

#### Explication d'une règle

Comme expliqué ci-dessus, cliquez sur sur une règle vous montre toutes les explications sur cette règle.

![Check my Website console website YSlow rule epxlained](/assets/img/fullsize/en/console/website-yslow/rules-explained.png)

La référence complète des règles YSlow peut être trouvée [en ligne](http://checkmyws.github.io/yslow-rules/fr/) et/ou au format [EPUB](https://www.gitbook.io/download/epub/book/olivjan/yslow?lang=fr), [MOBI](https://www.gitbook.io/download/mobi/book/olivjan/yslow?lang=fr) ou [PDF](https://www.gitbook.io/download/pdf/book/olivjan/yslow?lang=fr) Gitbook.
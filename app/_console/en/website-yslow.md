---
sharing: true
comments: true
layout: page
title:  "Website YSlow"
date:   2014-06-12 08:00:00 +0100
locale: "en"
permalink: /en/console/website-yslow/
lead: "This page shows you how you website performs regarding the YSlow rules. YSlow rules are best practices for speeding up Your website."
weight: "007"
---

## What are the YSlow rules?

As mentioned on The [YSlow offical website](http://yslow.org/),

> Yahoo!'s Exceptional Performance team has identified 34 rules that affect web page performance. YSlow's web page analysis is based on the 23 of these 34 rules that are testable. Studies have shown that web page response time can be improved by 25% to 50% by following these rules.

Rules are organised in rulesets. There are three rulesets at the moment:

- YSlow(V2) - this ruleset contains the 23 rules listed below.
- Classic(V1) - this ruleset contains the first 13 rules listed below.
- Small Site or Blog - this ruleset contains 14 rules that are applicable to small web sites or blogs.

This table resumes which rule is applied in a ruleset. Click on a rule to see details of the rule.

<table class="table table-striped"><thead><tr><th align=left>Rule</th><th align=center>YSlow V2</th><th align=center>YSlow V1</th><th align=center>Small site/blog</th></tr></thead><tbody><tr><td align=left><a target="_blank" href=http://checkmyws.github.io/yslow-rules/en/#ynumreq>Make fewer HTTP Requests</a></td><td align=center><i class="fa fa-check-circle"></i></td><td align=center><i class="fa fa-check-circle"></i></td><td align=center><i class="fa fa-check-circle"></i></td></tr><tr><td align=left><a target="_blank" href=http://checkmyws.github.io/yslow-rules/en/#ycompress>Compress components with gzip</a></td><td align=center><i class="fa fa-check-circle"></i></td><td align=center><i class="fa fa-check-circle"></i></td><td align=center><i class="fa fa-check-circle"></i></td></tr><tr><td align=left><a target="_blank" href=http://checkmyws.github.io/yslow-rules/en/#yexpressions>Avoid CSS expressions</a></td><td align=center><i class="fa fa-check-circle"></i></td><td align=center><i class="fa fa-check-circle"></i></td><td align=center><i class="fa fa-check-circle"></i></td></tr><tr><td align=left><a target="_blank" href=http://checkmyws.github.io/yslow-rules/en/#yminify>Minify Javascript and CSS</a></td><td align=center><i class="fa fa-check-circle"></i></td><td align=center><i class="fa fa-check-circle"></i></td><td align=center><i class="fa fa-check-circle"></i></td></tr><tr><td align=left><a target="_blank" href=http://checkmyws.github.io/yslow-rules/en/#yetags>Configure Entity tags (ETags)</a></td><td align=center><i class="fa fa-check-circle"></i></td><td align=center><i class="fa fa-check-circle"></i></td><td align=center></td></tr><tr><td align=left><a target="_blank" href=http://checkmyws.github.io/yslow-rules/en/#ymindom>Reduce the number of DOM elements</a></td><td align=center><i class="fa fa-check-circle"></i></td><td align=center></td><td align=center><i class="fa fa-check-circle"></i></td></tr><tr><td align=left><a target="_blank" href=http://checkmyws.github.io/yslow-rules/en/#ycookiefree>Use cookie-free domains</a></td><td align=center><i class="fa fa-check-circle"></i></td><td align=center></td><td align=center></td></tr><tr><td align=left><a target="_blank" href=http://checkmyws.github.io/yslow-rules/en/#yfavicon>Make favicon small and cacheable</a></td><td align=center><i class="fa fa-check-circle"></i></td><td align=center></td><td align=center><i class="fa fa-check-circle"></i></td></tr><tr><td align=left><a target="_blank" href=http://checkmyws.github.io/yslow-rules/en/#cdn>Use a Content Delivery Network (CDN)</a></td><td align=center><i class="fa fa-check-circle"></i></td><td align=center><i class="fa fa-check-circle"></i></td><td align=center></td></tr><tr><td align=left><a target="_blank" href=http://checkmyws.github.io/yslow-rules/en/#ycsstop>Put CSS at top</a></td><td align=center><i class="fa fa-check-circle"></i></td><td align=center><i class="fa fa-check-circle"></i></td><td align=center><i class="fa fa-check-circle"></i></td></tr><tr><td align=left><a target="_blank" href=http://checkmyws.github.io/yslow-rules/en/#yexternal>Make JavaScript and CSS external</a></td><td align=center><i class="fa fa-check-circle"></i></td><td align=center><i class="fa fa-check-circle"></i></td><td align=center></td></tr><tr><td align=left><a target="_blank" href=http://checkmyws.github.io/yslow-rules/en/#yredirects>Avoid URL redirects</a></td><td align=center><i class="fa fa-check-circle"></i></td><td align=center><i class="fa fa-check-circle"></i></td><td align=center><i class="fa fa-check-circle"></i></td></tr><tr><td align=left><a target="_blank" href=http://checkmyws.github.io/yslow-rules/en/#yxhr>Make Ajax cacheable</a></td><td align=center><i class="fa fa-check-circle"></i></td><td align=center></td><td align=center></td></tr><tr><td align=left><a target="_blank" href=http://checkmyws.github.io/yslow-rules/en/#yno404>Avoid HTTP 404 (Not Found) error</a></td><td align=center><i class="fa fa-check-circle"></i></td><td align=center></td><td align=center><i class="fa fa-check-circle"></i></td></tr><tr><td align=left><a target="_blank" href=http://checkmyws.github.io/yslow-rules/en/#ynofilter>Avoid AlphaImageLoader filter</a></td><td align=center><i class="fa fa-check-circle"></i></td><td align=center></td><td align=center><i class="fa fa-check-circle"></i></td></tr><tr><td align=left><a target="_blank" href=http://checkmyws.github.io/yslow-rules/en/#yemptysrc>Avoid empty src or href</a></td><td align=center><i class="fa fa-check-circle"></i></td><td align=center></td><td align=center><i class="fa fa-check-circle"></i></td></tr><tr><td align=left><a target="_blank" href=http://checkmyws.github.io/yslow-rules/en/#yexpires>Add Expires headers</a></td><td align=center><i class="fa fa-check-circle"></i></td><td align=center><i class="fa fa-check-circle"></i></td><td align=center></td></tr><tr><td align=left><a target="_blank" href=http://checkmyws.github.io/yslow-rules/en/#yjsbottom>Put Javascript at bottom</a></td><td align=center><i class="fa fa-check-circle"></i></td><td align=center><i class="fa fa-check-circle"></i></td><td align=center><i class="fa fa-check-circle"></i></td></tr><tr><td align=left><a target="_blank" href=http://checkmyws.github.io/yslow-rules/en/#ydns>Reduce DNS lookups</a></td><td align=center><i class="fa fa-check-circle"></i></td><td align=center><i class="fa fa-check-circle"></i></td><td align=center><i class="fa fa-check-circle"></i></td></tr><tr><td align=left><a target="_blank" href=http://checkmyws.github.io/yslow-rules/en/#ydupes>Remove duplicate JavaScript and CSS</a></td><td align=center><i class="fa fa-check-circle"></i></td><td align=center><i class="fa fa-check-circle"></i></td><td align=center><i class="fa fa-check-circle"></i></td></tr><tr><td align=left><a target="_blank" href=http://checkmyws.github.io/yslow-rules/en/#yxhrmethod>Use GET for AJAX request</a></td><td align=center><i class="fa fa-check-circle"></i></td><td align=center></td><td align=center></td></tr><tr><td align=left><a target="_blank" href=http://checkmyws.github.io/yslow-rules/en/#ymincookie>Reduce cookie size</a></td><td align=center><i class="fa fa-check-circle"></i></td><td align=center></td><td align=center></td></tr><tr><td align=left><a target="_blank" href=http://checkmyws.github.io/yslow-rules/en/#yimgnoscale>Do not scale images in HTML</a></td><td align=center><i class="fa fa-check-circle"></i></td><td align=center></td><td align=center><i class="fa fa-check-circle"></i></td></tr></tbody></table>

## YSlow rules in the Check my Website console

This page shows you how your website performs regarding those rules.

![Check my Website console website YSlow rules](/assets/img/fullsize/en/console/website-yslow/yslow.png)

There are three panels that we're going to detail now.

### The score and the score graph

The badge on the left indicates the score, i.e. *95*, and the grade, i.e *A*, that the website gets with YSlow rules.

The color of badge is green when the score is good enough, orange when there is room for improvements and red when the website should **not** be in production. It's just an expression. Don't take those words for granted! That said, you should ask your developpers to do some more work, optimisations on your website is your score is under *C*.

To understand how the score and grade are computed, see the [matrix reference page](http://yslow.org/ruleset-matrix/).

![Check my Website console website YSlow score](/assets/img/fullsize/en/console/website-yslow/score-graph.png)

The graph shows you the evolution of the score. Handy to trace regressions done in the website code… Or better, improvements done!

### The general panel

The general panel is a quick overview on how the differents components families « CSS, HTML, medias and Javascript » are distributed.

![Check my Website console website YSlow general panel](/assets/img/fullsize/en/console/website-yslow/general.png)

For each component family, you get the number of components requested and the total weight of those components.

### The rules summary panel

This panel show you the improvements that can be done to higher your YSlow score and grade regarding the ruleset used. You can change the ruleset used in the [settings panel](/en/console/website-settings/) of the website.

![Check my Website console website YSlow rules summary panel](/assets/img/fullsize/en/console/website-yslow/rules.png)

This website has mainly two improvements to be done to go to perfect score, which is 100. Reduce the number of HTTP request and GZip components on the server side. Click on a rule to have full explanations of what can be done for that rule. See below for an exmaple.

Click on `See full list…` to see all rules used in the chosen ruleset.

![Check my Website console website YSlow rules summary panel expanded](/assets/img/fullsize/en/console/website-yslow/rules-expanded.png)

Click on `See only bad scores…` to focus on what you have to do.

#### Explanation of a rule

As explained above, clicking on a rule shows you the complete explanation of that rule.

![Check my Website console website YSlow rule epxlained](/assets/img/fullsize/en/console/website-yslow/rules-explained.png)

full reference of the YSlow rules can be found [online](http://checkmyws.github.io/yslow-rules/en/) or/and as an [EPUB](https://www.gitbook.io/download/epub/book/olivjan/yslow?lang=en), [MOBI](https://www.gitbook.io/download/mobi/book/olivjan/yslow?lang=en) or [PDF](https://www.gitbook.io/download/pdf/book/olivjan/yslow?lang=en) Gitbook.
---
sharing: true
comments: true
layout: page
title:  "Website overview"
date:   2014-06-12 08:00:00 +0100
locale: "en"
permalink: /en/console/website-overview/
lead: "Just like the global overview but for each of the website you monitor."
weight: "003"
---

You have a site overview screen for every website you monitor with the Check my Website service.

![Check my Website console website overview](/assets/img/fullsize/en/console/website-overview/website-overview.png)

There are 10 parts in this website overview that we are going to detail now.

## Website identity

Nothing fancy with this one. it's just the website address you monitor.

![Check my Website console website identity](/assets/img/fullsize/en/console/website-overview/website-url.png)

The badge on the left tells you about the [state](/en/terms-definitions/) the monitored website is at the moment.

If your website has a [favicon file](http://en.wikipedia.org/wiki/Favicon), it will honored and presented as well. Clicking on the website takes you to that website… Logic ! If no favicon is present, the Check my Website logo is shown just like the example at the top of this page.

## Website menu

Like the menu bar but for the website. Click on any menu tabulation to go to that particular screen.

![Check my Website console website menu](/assets/img/fullsize/en/console/website-overview/website-menu.png)

- [`Overview`](/en/console/website-overview/) gives you an overview of your website. This is where we are at the moment.
- [`Logs`](/en/console/website-events/) gives you all events that occured for a website. This can be an `Ok` to `Warning` state, a `Critical` to `Ok` state…
- [`Metrics`](/en/console/website-metrics/) are nice graphs to show response time, YSlow notation and so on…
- [`Timeline`](/en/console/website-timeline/) shows you how the website is loading in the browser, based on the [HAR](http://www.softwareishard.com/blog/har-12-spec/) standard.
- [`YSlow`](/en/console/website-yslow/) are recommandations from the Yahoo performance team to have faster websites. Don't miss this one if you **do** care about your website speed and compliance.
- [`Settings`](/en/console/website-settings/) allows you to modify every parameters about checks involved for a website.

## State duration

Your website has a current state, `Ok` in this example screenshot. Thispanel tells me for how long it has been in that particular state. In other words, it's the ime elapsed since the last state change. 

![Check my Website console website state duration](/assets/img/fullsize/en/console/website-overview/state-duration.png)

The date just under this value is the date of the last sate change.

## States by location

The state you've got on the overview screen is a computed one. It's `Ok` if the majority of the locations from where checks occured are in this state. But what about the details for every location? This panel gives you just that.

![Check my Website console website states by location](/assets/img/fullsize/en/console/website-overview/states.png)

Form left to right:

- The state the website is for that particular location, i.e. *`Ok`* from Paris.
- The name of the location, i.e *Paris*.
- The [response time](/en/terms-definitions/#response-time) from that location, i.e. *14ms* from Paris.

## Informations

This panel gives you some general informations about the response received from the server for the website.

![Check my Website console website informations](/assets/img/fullsize/en/console/website-overview/informations.png)

On each information, you get a changing color badge at the right. The color is based on best practices generally admitted by the community.

- Green badge is good.
- Orange badge is not so good.
- Red badge is bad ;) 

What about the informations contained:

- The Number of [HTTP requests](/en/terms-definitions/#http-request) done for rendering the complet page. Less is better in this case ! In this example, *82* request are made, which is considered a bit too much.
- The `Number of HTTP 404 responses` is the number of elements requested but not found in the page. Zero is the only viable option for a good website ! That's why there's a red badge in this example; *1* 404 detected.
- The `Number of Javascript errors` is the number of errors found in the Javascript code involved for that page.
- The Number of [HTTP redirects](/en/terms-definitions/#http-redirect) (301 or 302) is the number of HTTP redirections involved for rendering the page. Once again, the less is best ! Everytime you make a redirection, you add a new request, latency to contact the new requested component… In short, **you add time to the page rendering**.

## YSlow notation

This panel show you the notation for the website, based on the [YSlow rules](http://checkmyws.github.io/yslow-rules/en/). The maximum is 100.

![Check my Website console website YSlow notation](/assets/img/fullsize/en/console/website-overview/yslow.png)

This website, despite some errors shown in the informations panel, is performing well regarding the YSlow rules with a *95* score and *A* grade notation.

## Availability for the last 24 hours

This panel gives you answer to that question: Does this website got [availability](/en/terms-definitions/#availability) problem in the last 24 hours ?

![Check my Website console website availability for the last 24 hours](/assets/img/fullsize/en/console/website-overview/availability.png)

This one didn't have any availability problem wth a *100%* online availability. Nice ! This value can be used for [SLA](/en/terms-definitions/#service-level-agreement) calculation.

## Last response time

The last [response time](/en/terms-definitions/#response-time) panel shows you the average latest response time from all the locations selected, i.e *43ms* in this case.

![Check my Website console website last response time](/assets/img/fullsize/en/console/website-overview/last-response-time.png)

## Mean time for the last 24 hours

The mean time indicator gives you the average response time from all locations for the last 24 hours, i.e. *45ms*.

![Check my Website console website mean time for the last 24 hours](/assets/img/fullsize/en/console/website-overview/mean-time.png)

The indicator in blue is a trend indicator telling you if the mean time for the last 24 hours is better or worse the latest reposnse time.

## Logs, events for the last 24 hours

All the events occured in the last 24 hours for the website shown. Events are fired mainly when there's a [state](/en/terms-definitions/) change, so this panel can be empty.

![Check my Website console website logs and events for the last 24 hours](/assets/img/fullsize/en/console/website-overview/logs.png)

In this example screen, the website has passed from a `Warning state` to an `Ok` state, which is a good news !
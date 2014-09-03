---
sharing: true
comments: true
layout: page
title:  "Website timeline"
date:   2014-06-12 08:00:00 +0100
locale: "en"
permalink: /en/console/website-timeline/
lead: "The timeline page gives you a whole detailed view on how the page is loaded, component by component."
weight: "006"
---

## What is a timeline and HAR ?

A timeline represents the loading of a webpage components in the browser.

The HTTP Archive Format (HAR) is an open format for exporting and exchanging data collected by monitoring tools. Originally designed by Jan Odvarko and Simon Perkins, this format is based on a JSON structure. Its current version is 1.22.

Read the [complete specification](http://www.softwareishard.com/blog/har-12-spec/) if you want to know more about the HAR format.

## The filmstrip panel

Above the timeline, you have what we call a filmstrip. It is certainly the easiest and the most visual appealing way to understand how a website is loaded, should i say painted, in the end-user browser.

![Check my Website console timeline filmstrip panel](/assets/img/fullsize/en/console/website-timeline/filmstrip.png)

In this case, there's only three screenshots taken:

1. One blank at *2ms*; the page begins to render.
2. One at *167ms*; all text and CSS seems to be loaded. It just lack some images.
3. The complete rendered page at *1.45 s*. Not so bad!

## Timeline in the Check my Website console

The timeline page show you the time it takes to load each components of the website from the server **without any browser cache**.

![Check my Website console timeline screen](/assets/img/fullsize/en/console/website-timeline/timeline.png)

The screenshot has been truncated due to exceptionnal length!

At the end of the timeline is a special line which is a total line. It represents the total number requests « *82* » done on the server, the total size « *980 KB* » and the total time « *468ms* » it takes to load the full page.


There are two special lines at the right of the timeline.

- The blue one indicates how long it takes to have the `DOMContentLoaded` event fired in the browser. *419ms* in this example.
- The red one is the time it takes for the `Load` event to be fired. *468ms* in this example.

See the [Navigation Timing specs](https://dvcs.w3.org/hg/webperf/raw-file/tip/specs/NavigationTiming/Overview.html) to know exactly what are these events.

### Detail of a component in the timeline

Each line of the timeline has five columns which are:

![Check my Website console timeline component detail](/assets/img/fullsize/en/console/website-timeline/component-detail.png)

1. The HTTP `Method` used, `GET` in this case as opposed to `POST` for example.
2. The `Path` of the component. If you want the complete path of the component, see below the even more details section.
3. The `Status` of the component, which is in fact the HTTP response code. See [this](http://en.wikipedia.org/wiki/List_of_HTTP_status_codes) to get a full list of HTTP response code.
4. The `Size` of the component in KB. *11 KB* in this example.
5. The `Timeline` of the component, composed of the time to wait « grey part » and the time to receive the component « green part ».

When you put your mouse over a component, it shows you exact value of the time elapsed to wait and receive the component.

![Check my Website console timeline component detail on mouseover](/assets/img/fullsize/en/console/website-timeline/component-detail-mouseover.png)

The `Mashup-571x348.png` is loaded at *123ms*, has a waiting time of *11ms* and a receive time of *56ms* giving a total *67ms* to load in the browser.

### Even more details for a component

You want more details? No problem! Here's the **complete header response received from the server for a component**. You can get this by clicking each component in the timeline.

![Check my Website console timeline component complete detail](/assets/img/fullsize/en/console/website-timeline/component-complete-detail.png)

Click the <i class="fa fa-times-circle"></i> icon to close the complete details of a component.
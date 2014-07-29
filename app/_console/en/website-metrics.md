---
sharing: true
comments: true
layout: page
title:  "Website metrics"
date:   2014-06-12 08:00:00 +0100
locale: "en"
permalink: /en/console/website-metrics/
lead: "This screen shows you graphs about response time, availability and page load time for a website."
weight: "005"
---

![Check my Website console website metrics](/assets/img/fullsize/en/console/website-metrics/metrics.png)

## Graph navigation

On top of each graph, you can navigate in the graph shown.

![Check my Website console website graph navigation](/assets/img/fullsize/en/console/website-metrics/graph-navigation.png)

From left to right:

- The <i class="fa fa-backward"></i> icon takes you to the previous time window. See below for time window.
- The <i class="fa fa-fw fa-hand-o-right"></i> icon indicates the scope of the graph. See below for explanation of the scope.
- The <i class="fa fa-refresh"></i> icon is just to refresh the logs, like every screen.
- The <i class="fa fa-forward"></i> icon takes you to the next time window.

### Time window

For every graph, you can choose the time window that is displayed.

![Check my Website console website graph time window](/assets/img/fullsize/en/console/website-metrics/graph-time-window.png)

You can choose from:

- One hour
- One day
- One week
- One month
- Three months

### Graph sampling

The graph sampling works in pair with the time window.

![Check my Website console website graph sampling](/assets/img/fullsize/en/console/website-metrics/graph-sampling.png)

Choose auto to let the console choose automatically for you what a point on a graph represents. On this example screen, each point represents a minute value. You can pass your cursor on the graph to see each point details.

![Check my Website console website graph point detailsg](/assets/img/fullsize/en/console/website-metrics/graph-point-details.png)

You can pass your cursor on the graph to see each point details.

## Response time graph

This graph represents the [response time](/en/terms-definitions/#response-time) from chosen locations for the website. What you see depends on the chosen period and interval.

![Check my Website console website response time graph](/assets/img/fullsize/en/console/website-metrics/response-time-graph.png)

### What the response time means in this graph ?

The response time in this graph is the time it takes for the webserver to send the page.

When your browser connects to a web server, the browser must execute a number of steps. These can be broken down into:

- DNS Lookup.
- Initial Connection.
- Waiting.
- Receiving Data. For a web page, this is the content of the file requested without any additionnal request done. CSS and other medias files are then not taken into account.
- Closing Connection.

<p class="alert alert-info" role="alert">Note that the DNS Lookup is <strong>cached</strong> with the Check my Website service.</p>

### Response time graph scope

Clicking the <i class="fa fa-fw fa-hand-o-right"></i> icon gives you several possibilities that we're gonna explain.

![Check my Website console website response time graph scope](/assets/img/fullsize/en/console/website-metrics/graph-scope.png)

`Global` indicates the average response time from all chosen locations.

### Respons time graph split

Apart from the `Global` scope, you can choose the `Split` item in the <i class="fa fa-fw fa-hand-o-right"></i> menu to have the response time graph by location, all in one graph. 

![Check my Website console website response time graph split](/assets/img/fullsize/en/console/website-metrics/graph-split.png)

Each location is then represented by its own color.

### Response time graph for one location

Clicking a location in the <i class="fa fa-fw fa-hand-o-right"></i> menu gives you the possibility to focus on that particular location.

![Check my Website console website response time graph for one location](/assets/img/fullsize/en/console/website-metrics/graph-location-detail.png)

In this example, the graph represents the response time from `Gravelines (59)` location, in north of France.

## Availability graph

This graph represents the [availability](/en/terms-definitions/#availability) of the website for the chosen period and interval.

![Check my Website console website response time graph](/assets/img/fullsize/en/console/website-metrics/availability-graph.png)

This website had no problem during the last day. Each point represents one hour (`Auto`).

## Page load time graph

This graph represents the page load time for the chosen period and interval. By page load time, we mean real page load time, rendered in the browser. This is what your end user perceive.

![Check my Website console website page load time graph](/assets/img/fullsize/en/console/website-metrics/page-load-time-graph.png)

In this graph, it seems that the website has been overloaded on the *07/23/2014* at *18:02* with a page load time around *5 seconds* compared to the ususal value of *500ms*. Administrators making some maintenance on the website maybe ?

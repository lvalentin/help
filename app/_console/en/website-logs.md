---
sharing: true
comments: true
layout: page
title:  "Website logs and events"
date:   2014-06-12 08:00:00 +0100
locale: "en"
permalink: /en/console/website-logs/
lead: "This screen shows you all events that have occured for a website."
weight: "004"
---

## definition of a log

The concept of historical events or logging refers to the sequential recording in a file or a database of all events affecting a particular process « application, website… ».

![Check my Website console website logs](/assets/img/fullsize/en/console/website-logs/logs.png)

## Logs navigation

On top of the events themselves, you can navigate in the logs shown.

![Check my Website console website logs navigation](/assets/img/fullsize/en/console/website-logs/logs-navigation.png)

From left to right:

- The <i class="fa fa-backward"></i> icon takes you to the previous logs page based on the time windows selected. See below for time window.
- The <i class="fa fa-refresh"></i> icon is just to refresh the logs, like every screen.
- The <i class="fa fa-trash-o"></i> icon makes it possible to purge logs, ersae them.
- The <i class="fa fa-forward"></i> icon takes you to the next logs page based on the time windows selected.

Like all the graphs, you can choose the time window that is displayed.

![Check my Website console website logs time window](/assets/img/fullsize/en/console/website-logs/logs-time-window.png)

You can choose from:

- One hour
- One day
- One week
- One month

## Logs, events

Logs are showing events but when does a event occur ?

- Changing state.
- Notification.

![Check my Website console website logs detail](/assets/img/fullsize/en/console/website-logs/logs-line.png)

From left to right:

- A badge indicates the [state](/en/terms-definitions/) of the event. Green for `Ok`, orange for `Warning`, red for `Critical`.
- The date and time the event occured.
- A <i class="fa fa-fw fa-hand-o-right"></i> icon indicating the scope of the event. The scope can be Global as opposed to a location for example.
- The event itself, the message.
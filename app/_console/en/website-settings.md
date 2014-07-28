---
sharing: true
comments: true
layout: page
title:  "Website settings"
date:   2014-06-12 08:00:00 +0100
locale: "en"
permalink: /en/console/website-settings/
lead: "Yuo can edit and modify any website monitored on the settings page, both in basic and advanced mode."
weight: "008"
---

You change, edit any settings, preferences for a website checks on this screen.

![Check my Website console settings view](/assets/img/fullsize/en/console/website-settings/settings.png)

We try to make our best to provide settings and checks with sensitive default values. That's mean less things to do for you. You cant trust the default values to ensure maximum value of the Check my Website service.

You can change any setting by clicking on the value of the setting to change it.

## The settings menu

Just under the navigation tabulations, you can find the settings menu.

![Check my Website console settings menu](/assets/img/fullsize/en/console/website-settings/settings-menu.png)

From left to right, you can find;

1. The `Disable` button to temporaly or defintively disable a website check. When clicked, the website will **not** be monitored anymore.
2. The `Remove` button to just do that. A removed website will **not** appear anymore in the console.
3. The `Rechedule check` button. You can ask an immediate reschedule for a check by clicking on this button.
4. The `Advanced mode` lets you switch to the Advanced settings page. This is in fact the same page with more options.

## The general panel

The general panel helps you enter a URL for the website to check and a few other options.

![Check my Website console settings general panel](/assets/img/fullsize/en/console/website-settings/general.png)

- The `Creation Time` can't be modified of course. This is the date and time the check wa created.
- The `URL` is the Internet address of the website, page you want to monitor.
- The `Interval` lets you set the frequency of the check. This is every minute by default, except in free account which is 5 mn.
- The `Tags` setting helps you classify your websites by any words you want.

### The general panel in advanced mode

Four new settings appear in the general panel in advanced mode.

![Check my Website console settings advanced general panel](/assets/img/fullsize/en/console/website-settings/advanced-general.png)

- `HTTP Method` is the method used to talk to the server. Usually `GET` or `POST`.
- `Parameters` allows you to pass parameters in the string query of the URL.
- `Headers` allow you to manipulate `headers` of the request dont to the server.
- `Body` is the just the same for the `body` of the request.

## The locations panel

The locations panel makes it easy to choose locations from where the checks will be executed. On Check my Website, checks are done in parrallel on these locations.

The maximum number of locations you can choose depends on the subscription level you have with the service. Check the [plans](/http://www.checkmy.ws/en/pricing/) to see available options.

![Check my Website console settings locations panel](/assets/img/fullsize/en/console/website-settings/locations.png)

## The checks panel

You can tweak main options of a website check in the check panel.

![Check my Website console settings general panel](/assets/img/fullsize/en/console/website-settings/checks.png)

- `Last Check` is the date and time of the latest executed check.
- `YSlow ruleset` lets you choose a ruleset for YSlow notation. See [YSlow](/en/console/website-yslow/) for more informations on that.

### The checks panel in advanced mode

Three new options appear in the checks panel advanced mode.

![Check my Website console settings advanced general panel](/assets/img/fullsize/en/console/website-settings/advanced-checks.png)

- `HTTP Response code` is the response code you're waiting for in the server response. This is usually `200`.
- `HTTP Time limit (ms)` lets you put a limit in time for what you think your website should responds. If you enter *500* here, you want your website response under 5 seconds. If it goes above this value, you'll be notified. 
- `Pattern` gives you the possibility to check a characters pattern in the server response. Handy to check that a website has not been defaced.

## The notifications panel

All the setting regarding notifications, alerts are in the notification paneL.

![Check my Website console settings notifications panel](/assets/img/fullsize/en/console/website-settings/notifications.png)

- `Email notification` enables or disables email notification for a wabsite.
- `Email recipients` is a list of persons notified in case of problem on the website.

### The notifications panel in advanced mode

Two new settings are available in the notifications panel advanced mode.

![Check my Website console settings advanced notfications panel](/assets/img/fullsize/en/console/website-settings/advanced-notifications.png)

- `Confirmation checks` is the maximum number of confirmation checks to do before sending notifications. The more confirmation checks you use, the less « false positive » notifications you'll have. But the delay before sending a notification will be longer. *3* is a good value to be notified for with a decent delay.
- `States` lets you choose the states on wich you want to be notified. Choosing `Ok` and `Critical` will send notifications for a `Ok` to `Criticial` state change but also for a `Critical` to `Ok` state change. 

## The status panel

The status panel lets you build a [status page](/en/console/website-status-page/) for communicating to your visitors or/and collaborators on your website health.

![Check my Website console settings status panel](/assets/img/fullsize/en/console/website-settings/status.png)

- `Public` lets you choose to make you website status page publicly available or not.
- `Alias` is alias Internet address where you status page can be found. Handy to have the status page on yourd domain rather than an address on the checkmy.ws domain.
- `Page link` is the alias + the protocol string. You must have a CNAME entry in your DNS zone file for having this to work.
- `Sharing page` lets your visitor share your status page on various social networks.

### The status panel in advanced mode

Two new settings are available in the status panel in advanced mode.

![Check my Website console settings advanced status panel](/assets/img/fullsize/en/console/website-settings/advanced-status.png)

- `Social links` lets you communicate on your status page your social profiles links.
- `Description` lets you describe your activity, website right on the status page.

More information on the status page can be found on the [status page documentation](/en/console/website-status-page/) page.
---
layout: documentation
title: Editor - Special actions
category: V-director
order: 3
---

Discover some tips and tricks with the content editor. Directly from an AR content, you can trigger phone calls, emails, etc. using the "Webpage" annotation. For example, you can create the following scenario where the user can trigger several different actions (here: phone call, email, SMS, and system browser).

![External actions scenario]({{ site.url }}/img/editor/external-actions-scenario.png))

## Make a phone call

In your AR content, add a "Webpage" annotation and enter the following special text: `externaltel:<phone number>`

![External phone call]({{ site.url }}/img/editor/external-telephone.png))

## Send an email

In your AR content, add a "Webpage" annotation and enter the following special text: `externalmailto:<email address>`

![External email]({{ site.url }}/img/editor/external-mailto.png))

## Send a SMS

In your AR content, add a "Webpage" annotation and enter the following special text: `externalsms:<phone number>`

![External SMS]({{ site.url }}/img/editor/external-sms.png))

## Open a link in the system web browser

Instead of opening a web link in the application, it is also possible to open a web link in the default system browser (Safari on iOS and usually Chrome in Android)
In your AR content, add a "Webpage" annotation and enter the following special text: `externalhttp:<website address>`

![External phone call]({{ site.url }}/img/editor/external-web-browser.png))

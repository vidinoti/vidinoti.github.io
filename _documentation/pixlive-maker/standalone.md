---
layout: documentation
title: Standalone content
category: V-director
order: 4
---

The contents can have two different modes of synchronization; the **default** mode and the **standalone** mode. These modes define how the contents are synchronized and used by the application.

These two modes are also sometimes called the "online" and "offline" modes.

## Difference between the two modes

The standard mode is the "default" mode. The content is streamed to the application once the image has been recognized. For example, if a video should start once the image is recognized, the video will be streamed from the server and thus requires the user to have an internet connection.

The standalone mode embeds all the assets of the content from the beginning and the assets will be downloaded during the application start (when the application synchronizes with the server). When the image is recognized, the application has directly all the assets locally available. For example, if a video should start once the image is recognized, the video will start directly without any internet connection.

## Comparison

| Default mode | Standalone mode |
|--------------|-----------------|
| + fast synchronization | - slower synchronization |
| + assets are downloaded only when needed | - the assets are downloaded even if the content is never recognized |
| - requires an internet connection when the content is recognized | + assets are directly available when a content is recognized |
| - poor internet connection causes latency | + no latency |

## How to select the mode

1) Connect to [V-Director](https://armanager.vidinoti.com)

2) Open the content (e.g. click the name of the content from the "Content list")

3) Locate the content details at the top right of the page

![Content details]({{ site.url }}/img/cms/content-details-standalone.png))

4) Click the "Yes/No" link of the *Standalone* property and choose the appropriate content mode

![Content mode]({{ site.url }}/img/cms/content-mode.png)
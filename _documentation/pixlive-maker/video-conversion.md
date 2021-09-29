---
layout: documentation
title: Video conversion
category: V-director
order: 14
---

For having the best possible experience, videos usually need to be optimized before using them in V-Director. Not all video formats are supported on mobile devices and it may be necessary to convert them.
In this page, we explain how to convert your video with the optimal settings.

## Video recommendation

* **Codec/Container**: H.264 / MP4
* **Resolution**: 720p (e.g. 1280x720)
* **Framerate**: 30 fps

We recommend to use videos with resolution at most 720p. It represents a good compromise between quality and size. If the video is long, prefer to use smaller resolution.

## Step-by-step guide

First, download and install [Handbrake](https://handbrake.fr) which is a great open source tool for converting videos.

Open Handbrake and select your video file.

![Handbrake - open video file]({{ site.url }}/img/video_conversion/handbrake1.png)

Open the preset dropdown and select "Fast 720p30".

![Handbrake - choose preset]({{ site.url }}/img/video_conversion/handbrake2.png)

Check the "Web Optimized" option, it improves the streaming capability of the video.

![Handbrake - select web optimized]({{ site.url }}/img/video_conversion/handbrake3.png)

If the video has a ratio different than 16/9, edit the "Storage Size" such that it corresponds to the "Display Size".

![Handbrake - ]({{ site.url }}/img/video_conversion/handbrake4.png)

Finally, select the destination of the file and click the "Start" button. The application starts converting the video; the process can take some time.

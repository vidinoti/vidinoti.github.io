---
layout: documentation
title: Image trigger
category: V-director
order: 3
permalink: /documentation/image-trigger
---

# Image trigger guidelines

This page give you some hints about how to choose your image trigger in order to improve the image detection and tracking.

Here are a few points on how to choose a good image trigger

* The image must be at least 480x480 pixels.
* The image must corresponds to a physical flat object (e.g. a picture, painting versus a bottle or sculpture).
* Avoid reflective material like glass or metal.
* The image must be rich in details.
* The image must have a good contrast.
* Avoid repetitive patterns in the image.
* The system does not use colors, it works on grayscale images.
* The system does not perform text recognition.
* The system is based on "corner" detection. For instance, a serie of circles won't be detected because they have no corner.


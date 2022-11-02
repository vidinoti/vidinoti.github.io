---
layout: documentation
title: Image Quality Guidelines
category: V-director
order: 3
permalink: /documentation/image-trigger
---

The Augmented Reality technologies provided by Vidinoti allows precise and fast image recognition on mobile phones. Users can upload images (also known as target image or image trigger) on the platform in order to create AR content, which can be later on recognized by mobile phones.

In order to be recognizable, a target image has to have several charateristics. In order to maximize the recognition quality and the imag tracking, this page lists guidlines that should be observed when choosing a target image.

Here are a few points on how to choose a good image trigger. Some of these points are then detailed below.

* The image must be at least 480x480 pixels.
* Maximize textured areas (see below).
* Typically simple pictograms or flat icons are bad candidates for image detection.
* The image must corresponds to a physical flat object (e.g. a picture, painting versus a bottle or sculpture).
* Avoid reflective material like glass or metal.
* The image must be rich in details.
* The image must have a good contrast.
* Avoid repetitive patterns in the image.
* The system does not use colors, it works on grayscale images.
* The system does not perform text recognition. Avoid detecting pages of text.
* The system is based on "corner" detection. For instance, a serie of circles won't be detected because they have no corner.

## Maximize textured areas

Image containing a lot of texture areas is easier to recognize. Textured areas are defined as areas where a lot of different changes in color or gray intensity happen.

{% include image_with_legend.html url="/img/cms/image_texture.jpg" description="Textured VS Non-textured images" %}


## Avoid repeated patterns 

If the image contains the same repeating pattern, it will be more difficult to recognize and to track properly. This is even more important if several target images have the same repeated patterns. Text is the most common repeatable pattern. For the system, all the letters have a smiliar look and therefore cannot be used to perform a good recognition. Avoid having large portion of text in the target images.

{% include image_with_legend.html url="/img/cms/image_pattern.jpg" description="Avoid repeating pattern" %}


## Maximize the spatial repartition of textured areas

Images having textured areas on all the image surface, will have a better recognition quality. If only a corner of the image contains a highly textured area, the system will have trouble to recognize and to track properly this target image.

{% include image_with_legend.html url="/img/cms/image_logo.jpg" description="Bad trigger: non-uniform repartition of texture 
and not enough textured" %}
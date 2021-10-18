---
layout: documentation
title: 3D on floor
category: V-director
order: 13
---

The "3D on floor" feature allows placing 3D objects in Augmented Reality. The 3D model is placed on an horizontal plane. The horizontal plane can be for example a table or the floor.

This feature allows showing 3D objects in augmented reality without the need of an image trigger.

## Supported devices

This feature uses the ARKit and ARCore technologies available on iOS and Android devices. It requires an application running SDK v.7.0.0 or over. Not all devices support the technology. The supported devices are listed below:

### iOS

* iOS 11 or above
* iPhone SE, iPhone 6S, iPhone 6S Plus or over
* iPad 5th Generation or over
* iPad Mini 5th Generation (2019) or over

### Android

* See [ARCore supported devices](https://developers.google.com/ar/discover/supported-devices)

### Fallback for unsupported devices

For unsupported devices, the 3D model won't be displayed in Augmented Reality but the 3D model would be displayed in preview mode.

## Editor Settings Help

![3D on floor - settings panel]({{ site.url }}/img/editor/3d-on-floor_settings.png)

### Correct object center

When the 3D model is placed on the floor, the origin of the 3D model (x, y, z = 0, 0, 0) is placed where the plane is detected. If the checkbox is unchecked, the position of the 3D object will corresponds to the position defined inside the 3D file. For instance, it may appear above the floor if the object Y-value is > 0 or with an offset if the object center is not at X = 0 or Z = 0. This behaviour may be wanted if for instance we want a balloon to be floating up in the air.

However, most of the time we want that the model stands on the ground and such that its center appears where the object has been placed. This is automatically done when the checkbox is enabled. The system will then translate the object on top of the floor and centered. This is often required if the 3D model has not been explicitely created for being displayed in AR.

### Adapt model size

By default, the size of the object in AR will correspond to the size defined in the 3D file. If the 3D file contains a cube of length 1, the cube will appear with a size of 1 meter in AR.

So, if the 3D file does not correspond to the wanted size, you can set the desired size by giving one of the wanted dimension in meter.

### Extra parameters

#### Placement mode

You can customize the placement mode that is used when placing the 3D object. By default, it uses the "automatic" mode if the SDK version is at least 7.2.7. For older SDK versions, the "legacy" mode is being used.

For setting a different mode, add the following in the "Extra parameters" field.

    placementMode = 'manual';

#### Placement mode: automatic (default)

When a horizontal surface is detected, a target visual indicates where the 3D model will appear. When the position remains stable for a while, the position is validated and the object appears.

<video height="360" muted controls="controls">
  <source src="{{ site.url }}/videos/3D_Placement_Automatic.mp4" type="video/mp4">
</video>

#### Placement mode: manual

When a horizontal surface is detected, a target visual indicates where the 3D model will appear. The user must click the button to validate the placement.

<video height="360" muted controls="controls">
  <source src="{{ site.url }}/videos/3D_Placement_Manual.mp4" type="video/mp4">
</video>

#### Placement mode: legacy

As soon as a horizontal surface is detected, the 3D model is placed on the surface.

<video height="360" muted controls="controls">
  <source src="{{ site.url }}/videos/3D_Placement_Legacy.mp4" type="video/mp4">
</video>

### Tutorial

See [V-Director: from Sketchfab to "3D on floor"]({{ '/documentation/tutorial/sketchfab-to-3d-floor' | relative_url }}).
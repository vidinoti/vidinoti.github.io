---
layout: documentation
title: 3D Library - ARKit / ARCore
category: V-director
order: 5
permalink: /documentation/asset3d
---

Vidinoti is introducing a new feature which is the visualization of 3D objects in augmented reality, in real size, without any image trigger.

# V-3Display

For that, we have published a new mobile application **V-3Display** that you can download on the AppStore or Google Play Store.

![V-3Display logo]({{ site.url }}/img/v-3display.png)

[![Download V-3Display on the App Store]({{ site.url }}/img/store/download_app_store.svg)](https://itunes.apple.com/us/app/v-3display/id1435607299?l=fr&ls=1&mt=8)
[![Download V-3Display on the Google Play Store]({{ site.url }}/img/store/google-play-badge.png)](https://play.google.com/store/apps/details?id=com.vidinoti.v3display)

The application uses the latest AR capabilities provided by Apple and Google called ARKit and ARCore. Thus, you need a compatible phone (see section below).


The application showcases a few examples of 3D models that you can try out. The application also allows you to display your own 3D objects! For that, connect to V-Director and create your own 3D assets (see section below about 3D format conversion).
Once you have uploaded your own 3D models, open the Dashboard page and scan your personal QR code with the application.
The application will then show up your own objects that you can place anywhere you want!

Have fun! Don’t hesitate to give us your feedback about this new feature. It will get improved over time!

# Device compatibility

* Apple: [iOS Device Compatibility Reference](https://developer.apple.com/library/archive/documentation/DeviceInformation/Reference/iOSDeviceCompatibility/DeviceCompatibilityMatrix/DeviceCompatibilityMatrix.html)
* Google: [ARCore Supported Devices](https://developers.google.com/ar/discover/supported-devices)

# 3D model conversion

This section describes how to create 3D models for Android and iOS. The steps described here will be automated in the V-Director platform soon.

## How to create a "Apple Scenekit compatible" file

If you want to upload a 3D model compatible with ARKit and Scenekit in the 3D Library, follow the steps described here.

Xcode supports SceneKit (`.scn`) and Collada (`.dae`) 3D models formats. SceneKit files can be uploaded in V-Library without modifications, but Collada files are not directly compatible with SceneKit and need to be modified. To do so, open a Xcode project, create a new Asset Catalogue and change its extension to ".scnassets".
Then drag&drop the Collada file and its textures in the folder. The files will be copied and Xcode will automatically run a script to make the Collada file compatible with SceneKit.

Xcode offers now the possibility to convert it to a `.scn` file in order to be able to modify its attributes, materials and physics properties directly in the SceneKit editor.
To do so, select your dae file in the project navigator, Show the scene graph view and select the root node in the scene graph. Go to the scene inspector and click on the button "Convert Scene to Y up" under the section "Metrics". A prompt asks you to convert the file to SCN format, confirm and it's done.

If the model contains texture files, a ZIP archive must be created, containing the SCN file itself, and a folder named "Resources" that contains the textures. The archive can then be uploaded on V-Director. If there is no external textures or the textures are embedded, the model can be directly uploaded on V-Director. 

## How to create an "Android Sceneform compatible" file

Follow the steps described here: [ARCore - Import and Preview 3D Assets](https://developers.google.com/ar/develop/java/sceneform/import-assets)

By doing so, you will obtain a single `.sfb` file that you can then upload on V-Director.
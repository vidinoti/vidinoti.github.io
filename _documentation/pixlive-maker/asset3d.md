---
layout: documentation
title: 3D Library - ARKit / ARCore
category: V-director
order: 4
permalink: /documentation/asset3d
---

This page describes how to create 3D models for Android and iOS. The steps described here will be automated in the V-Director platform soon.

# How to create a "Apple Scenekit compatible" file

If you want to upload a 3D model compatible with ARKit and Scenekit in the 3D Library, follow the steps described here.

Xcode supports SceneKit (`.scn`) and Collada (`.dae`) 3D models formats. SceneKit files can be uploaded in V-Library without modifications, but Collada files are not directly compatible with SceneKit and need to be modified. To do so, open a Xcode project, create a new Asset Catalogue and change its extension to ".scnassets".
Then drag&drop the Collada file and its textures in the folder. The files will be copied and Xcode will automatically run a script to make the Collada file compatible with SceneKit.

Xcode offers now the possibility to convert it to a `.scn` file in order to be able to modify its attributes, materials and physics properties directly in the SceneKit editor.
To do so, select your dae file in the project navigator, Show the scene graph view and select the root node in the scene graph. Go to the scene inspector and click on the button "Convert Scene to Y up" under the section "Metrics". A prompt asks you to convert the file to SCN format, confirm and it's done.

If the model contains texture files, a ZIP archive must be created, containing the SCN file itself, and a folder named "Resources" that contains the textures. The archive can then be uploaded on V-Director. If there is no external textures or the textures are embedded, the model can be directly uploaded on V-Director. 

# How to create an "Android Sceneform compatible" file

Follow the steps described here: [ARCore - Import and Preview 3D Assets](https://developers.google.com/ar/develop/java/sceneform/import-assets)

By doing so, you will obtain a single `.sfb` file that you can then upload on V-Director.
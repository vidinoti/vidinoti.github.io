---
layout: documentation
title: 'V-Director: from Sketchfab to "3D on floor"'
category: Tutorial
---

## Tutorial: How to create a new AR experience with 3D assets!

![Medieval tower 3D model]({{ site.url }}/img/tutorial/sketchfab-to-3d/tuto_demo.png)

We have introduced a new way to experience 3D models in AR! No more need of image tracking, the 3D model is automatically placed on the floor or on your table. We present here the steps to follow for creating such experience!

The steps are the following:

1. Create or download a 3D model, we present here how Sketchfab models can be used.
2. Create a 3D assets in V-Director
3. Create a V-Director content
4. Play it!

### 1. Get a 3D model

Sketchfab is a platform listing millions of 3D models. It is a good way to find nice 3D models that can be used in V-Director.

* Go to [Sketchfab](https://sketchfab.com)
* Search for a 3D model, for instance search for “tower”. Plenty of results will appear. Not all models are downloadable, you may want to filter the results by showing only the “downloadable” models

![Sketchfab website]({{ site.url }}/img/tutorial/sketchfab-to-3d/tuto_sketchfab.png)

* Select one of the model
* Look at the number of vertices and triangles. It gives you some information about the complexity of the model. If the model is too big and/or too complex, the download and rendering won’t be optimal on a mobile device.

![Sketchfab website]({{ site.url }}/img/tutorial/sketchfab-to-3d/tuto_sketchfab_download.png)

* Download the 3D model in glTF (v2) format. glTF is a recent 3D file format optimized for interoperability and the format currently supported for 3D assets in V-Director.

![Sketchfab website]({{ site.url }}/img/tutorial/sketchfab-to-3d/tuto_sketchfab_download2.png)

* Unzip the files in a folder.

### 2. Create a 3D asset in V-Director

* Connect to V-Director
* Click “3D” in the left menu
* Click “+ Import a new 3D asset”
* Drag’n’drop the folder containing the 3D model (the .gltf file and with its textures)
* A preview of the 3D model is displayed
  * You can zoom in/out using the mouse wheel
  * Click and drag to rotate the camera
  * Ctrl+Click and drag to move the camera
* Click the “Upload” button. The 3D asset is created
* If necessary, you can modify its attributes, in particular its name and its size. If the size is not set, the “intrinsic” size of the 3D model is used. 1 unit in the 3D model will corresponds to 1 meter when displayed in AR. The grid visible for the preview shows a line every meter.

### 3. Create a V-Director content

We need now to integrate the 3D asset inside a standard V-Director content. The 3D asset can be integrated to any type of content (image, GPS or beacon).

For this example, we will create an image content.

* In V-Director, go to “My Contents” and create a new image content
* Upload the image trigger and go to the editor
* For this example, we create a “Text button” that goes to a new scene

![Editor scenario]({{ site.url }}/img/tutorial/sketchfab-to-3d/tuto_editor_scenario.png)

* In the new scene, we add a new “3D asset”
* We search for the asset that we have previously created, select it and click “Load”

![Editor 3D]({{ site.url }}/img/tutorial/sketchfab-to-3d/tuto_editor_3d.png)

* The size of the model is retrieved from the 3D asset but can be overridden in the settings
* The settings provide an option “Correct object center” that translate the model such that it appears correctly in on the floor once it has been placed in AR
* Apply the changes and “Save and quit”

### 4. Play it!

* Download and run the V-Player app
* Scan your QR code
* Scan the image

Attributions for this tutorial

* [3D model by arturhorn on Sketchfab](https://sketchfab.com/3d-models/free-fantasy-guard-tower-92852e66505e438b9494eb3df98dca0e)
* [Pexel image](https://www.pexels.com/photo/black-steel-helmet-near-black-and-gray-handle-sword-161936/)
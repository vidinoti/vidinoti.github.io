---
layout: documentation
title: 3D Preview
category: V-director
order: 6
permalink: /documentation/3dpreview
---

This page describes how to create a web preview for 3D models.

## Step-by-step guide

1. Connect to V-Director and open the 3D asset library.
2. Create a new 3D asset or edit an existing one.
3. Upload a 3D model in glTF format: select glTF in the dropdown menu and select the file to upload. You can either select a single `.gltf` file or upload a zip file containing the glTF file with its textures.

    ![glTF upload]({{ site.url }}/img/3d_preview/gltf-upload.png)

4. Once the file has been uploaded, you can generate the 3D preview by clicking the "Generate preview" button.

    ![glTF generate preview]({{ site.url }}/img/3d_preview/gltf-preview.png)

5. The 3D preview is displayed once it has been generated.

    ![3D Preview]({{ site.url }}/img/3d_preview/3d-preview.png)

6. You can open it in a new browser window by clicking "Open in external tab".

Attribution: the above 3D model has created by [Koha](https://sketchfab.com/Koha.Ha) and distributed on [Sketchfab](https://sketchfab.com/3d-models/ice-cream-truck-57ba94f1def5409d8588a15d497e1368) under CC License.

## Remarks

* If you want to integrate the 3D preview in a content. Right-click "Open in external tab" and copy link address. In your content, paste the link in a new webpage annotation.
* If you generate a new preview, the previous preview will be lost and the previous URL will stop working.
* The [Sketchfab](https://sketchfab.com/3d-models?date=week&features=downloadable&sort_by=-likeCount) website contains many 3D models and allows downloading them in glTF format.
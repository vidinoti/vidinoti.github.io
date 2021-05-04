---
layout: documentation
title: 3D Model for AR - Guidelines
category: V-director
order: 12
---

For having a smooth experience with 3D models in AR, the 3D models must be optimized. Having an optimised 3D model is not easy and many factors affects the performance and model's memory usage. Always test your models on a real device (ideally different devices from low to high-end).

As a global recommendation, try to reduce as much as possible:

* Mesh complexity.
* Texture size and count.
* Animation complexity if any.

For a V-Director 3D asset with a single PBR material, try to stay below:

* 100k polygons
* One single set of 2048x2048px texture set
* Ten seconds of animation

Apple recommendations for optimizing models:

* Freeze transforms and merge adjacent vertices
* If possible, use a single material/texture set for the entire model Don’t include textures you don’t need
* Spend your texture budget on areas that add most value and realism Remember that pixels have a physical size in AR
* Balance texture size and quality against download size

## References

* [Apple WWDC 2018 - Integrating Apps and Content with AR Quick Look](https://developer.apple.com/videos/play/wwdc2018/603)
---
layout: documentation
title: SDK Release notes
category: Sdk
order: 6
---

# Release notes

* [Supported devices](#supported-devices)
* [Android SDK](#android)
* [Third-Party Licenses](#third-party-licenses)
* [iOS SDK](#ios)

# Supported devices

## Android SDK

The latest Android SDK requires **Android 5.1** (API 22) or above.

For ARCore-specific features (e.g. *3D on floor*), only compatible devices are supported. These devices are listed there: [https://developers.google.com/ar/discover/supported-devices]()

## iOS SDK

The latest iOS SDK requires **iOS 10** or above. This correponds to the following devices:

* iPhone 5S and beyond
* iPod 6th generation and beyond
* iPad Air and beyond
* iPad Mini 2 and beyond

For ARKit-specific features (e.g. *3D on floor*), the device must support ARKit. It requires at least iOS 11 and the supported devices include:

* iPhone SE, iPhone 6S, iPhone 6S Plus and beyond
* iPad 5th Generation and beyond
* iPad Mini 5th Generation (2019) and over

# Third-Party Licenses

The Vidinoti SDK includes 3rd-party softwares released under open source license.

For details, see <https://static.vidinoti.com/sdk/SDK-3rdParty.txt>

# Android

## Version 7.6.3 - 2025/10/31

* Bug fixes

## Version 7.6.2 - 2025/07/04

* Update Android Pdf Viewer

## Version 7.6.1 - 2025/06/25

* Add ability to change API endpoints

## Version 7.6.0 - 2024/08/15

* Add Android API 35 support

## Version 7.5.1 - 2023/12/13

* Add better support for standalone contents in ARCore mode

## Version 7.5.0 - 2023/01/18

* Add Android API 33 support

## Version 7.3.5 - 2021/12/22

* Add support for Scene Viewer in SDK web view

## Version 7.3.4 - 2021/10/14

* Allow to define a custom PDF viewer using VDARSDKController#setCustomPdfViewer

## Version 7.3.3 - 2021/09/24

* Fix standalone "3D on floor" content when targeting API 30

## Version 7.3.2 - 2021/09/22

* Fix for Android API 31 - specify explicit value for `android:exported` for all components with an intent filter defined.

## Version 7.3.1 - 2021/08/16

* ARCore unsupported device webview: allow page redirection without user interaction

## Version 7.3.0 - 2021/07/02

* Allow to change fullscreent content background color

## Version 7.2.12 - 2021/06/14

* Small fixes

## Version 7.2.11 - 2021/05/12

* Add close button when navigating within SDK web view.

## Version 7.2.10 - 2021/04/21

* Allow to dispatch custom event to app from SDK webview

## Version 7.2.9 - 2021/03/31

* Add stop method to Context for stopping and closing current context
* Audiosync player: player automatically loops

## Version 7.2.7 - 2021/02/22

* "3D on floor": add ARCore continuous plane detection for new placement method

## Version 7.2.6 - 2021/01/29

* Add `VDARSDKController#setPauseVisionRecognition` for temporarily disabling image and code recognition

## Version 7.2.5 - 2020/11/30

* Fix placement problem with "3D on floor"

## Version 7.2.4 - 2020/11/12

* Advanced AR content: add support for ARCore image detection

## Version 7.2.3 - 2020/09/09

* Remove grey top bar for some content types and replace by standard Android back button

## Version 7.2.2 - 2020/08/31

* Allow to stop AR session and close view from ARCore content

## Version 7.2.1 - 2020/06/12

* Fix audio keep playing on web page close
* Hide next/previous button if not active for web pages

## Version 7.1.0 - 2020/04/02

* Add support for starting GPS tracking with GPS point detection

## Version 7.0.1 - 2020/01/17

* ARCore 3D-player: increase camera far plane

## Version 7.0.0 - 2019/12/18

* Add ARCore support. Allows placing 3D objects on an horizontal plane (floor, table, etc.).

For supporting ARCore, you must include the ARCore dependency to your app. Add the dependency `com.google.ar:core:1.13.0` to your `build.gradle` file.

This feature requires a supported devices. See [Google ARCore supported devices](https://developers.google.com/ar/discover/supported-devices).
If the device is not supported, the 3D model will be displayed in a viewer rather than in AR.

## Version 6.5.17 - 2019/11/04

* Fix 3D transparency problem with some 3D models

## Version 6.5.16 - 2019/10/11

* Fix video not being displayed when opening without using the standard scanner

## Version 6.5.15 - 2019/09/09

* Replace rendering mechanism for HTML annotation (scratches) and improve its rendering quality.

Known issue with Sony Xperia Z running Android 5.1.1: The device may freeze when scanning a scratch.

## Version 6.5.14 - 2019/08/07

* Add method for changing the license key once the SDK has already been initialized
* Add method for forcing the interface language

## Version 6.5.12 - 2019/07/01

* Fix problem with scratch contents when building application with Android target API 28.
* Allow enabling contents by tag without requiring a new synchronization.
* Fix ratio of "screen relative annotations" (e.g. fullscreen contents and close button).

## Version 6.5.11 - 2019/04/23

* Add synchronization mechanism using content creator email.

## Version 6.5.10 - 2019/04/04

* Add video loop support

## Version 6.5.9 - 2019/03/21

* Fix distorted 3D objects

## Version 6.5.8 - 2019/03/19

* Fix 3D animation not starting
* Keep synchronized contents when upgrading the application

## Version 6.5.7

* Remove top bar with title "Content" for fullscreen contents

## Version 6.5.6

* Add support for devices with multiple back-facing cameras
* Improve camera preview
* Add support for file upload from webview

## Version 6.5.5

* Add support for 64-bit architectures (arm64-v8a and x86_64)
* Fix crash for devices not supporting OpenGL antialiasing

## Version 6.5.4

* Fix problem where camera view may have a bad orientation
* Avoid reloading page when changing orientation

## Version 6.5.3

* Fix possible crash due to NullPointerException

## Version 6.5.2

* Fix possible crash for devices running Android 4.4

## Version 6.5.1

* Fix rendering of videos that were starting with a few black frames

## Version 6.5.0

* Improve rendering of 3D objects: add normal mapping support

## Previous releases

### Note for v.6.4.0

Starting from v.6.4.0, the push notifications have been migrated from GCM to FCM. See the migration guide: [https://vidinoti.github.io/201805-android-migration/](https://vidinoti.github.io/201805-android-migration/)

### Warnings:

Since release 6.1.0, the PDF library is not packaged in the AAR file anymore. If you plan to use PDF files, add the external dependency in your gradle file as shown below or in the sample application:

```
compile 'com.github.barteksc:android-pdf-viewer:2.7.0'
```

Remark: If you are using the Cordova plugin, update to version 1.4.0

The old SDK only includes the armeabi-v7a and x86 architectures, ensure that your application does not include other architecture. It may result in crashes. Either split the APK by ABI (see [https://developer.android.com/studio/build/configure-apk-splits.html#configure-abi-split](https://developer.android.com/studio/build/configure-apk-splits.html#configure-abi-split)) or include only the wanted ABI by adding the following to your build.gradle file

```
buildTypes {
    all {
        ndk {
            abiFilters "armeabi-v7a", "x86"
        }
    }
}
```

# iOS

## Version 7.6.1 - 2025/06/24

* Add ability to change API endpoints

## Version 7.5.3 - 2025/05/06

* Fix issue with web links being opened by the system browser (`externalhttps:`)

## Version 7.5.2 - 2023/08/14

* Adapt BTCXRManager to pass the parent view controller

## Version 7.5.1 - 2023/01/24

* Fix camera orientation when starting the application in landscape mode

## Version 7.5.0 - 2022/11/24

* Add support for BTCXR files

## Version 7.4.1 - 2022/09/22

* Fix potential crash when running ARKit on iOS 16

## Version 7.4.0 - 2022/02/23

* Distribute SDK as XCFramework. Allows to run simulator on M1 computers.
* Expose appID and licenseKey for ARKit contents.
* ARKit world map: add SDK custom headers when downloading world map.

## Version 7.3.2 - 2021/12/22

* Add support for USDZ files in SDK web view

## Version 7.3.1 - 2021/12/06

* Fix navigation bar color of default AR view with iOS 15

## Version 7.3.0 - 2021/07/02

* Allow to change fullscreen content background color

## Version 7.2.12 - 2021/06/14

* Small fixes

## Version 7.2.10 - 2021/05/04

* add `openFileURLInInternalBrowser` for opening internal files with SDK web view

## Version 7.2.9 - 2021/03/31

* Add stop method to Context for stopping and closing current context
* Audiosync player: player automatically loops

## Version 7.2.8 - 2021/03/17

* Fix potential issue with iframes in SDK's web view.

## Version 7.2.7 - 2021/02/22

* "3D on floor": add ARKit continuous plane detection for new placement method
* expose `openURLInInternalBrowser` with extra parameters in `VDARSDKController`
* Allow to dispatch custom event to app from SDK webview

## Version 7.2.6 - 2021/02/02

* Fix potential concurrency issue in ARKit image detection

## Version 7.2.5 - 2021/01/19

* Add support for ARKit World Map via advanced contents
* Fix memory leak in ARKit image detection
* Add `pauseVisionRecognition` in `VDARSDKController` for temporarily disabling image and code recognition

## Version 7.2.4 - 2020/10/23

* Expose VDARNearbyGPSController
* Advanced AR content: add support for ARKit image detection

## Version 7.2.3 - 2020/09/08

* Uniformize close button layout: use standard iOS navigation bar with "Done" button
* Fix layout for devices with notch and "home swipe button"
* Close fullscreen video at the end of the file

## Version 7.2.2 - 2020/07/08

* Web page: follow links that should open in a new tab.
* Add "deviceorientation" support to web view.
* Fix memory issue with iOS 13 and ARKit.

## Version 7.2.1 - 2020/05/01

* Improve plane detection for "3D on floor" feature

## Version 7.2.0 - 2020/04/13

* Migrate deprecated iOS SDK UIWebView to WkWebView

## Version 7.1.0 - 2020/04/02

* Add support for starting GPS tracking with GPS point detection

## Version 7.0.3 - 2020/03/13

* Fix memory leak

## Version 7.0.2 - 2020/03/04

* Fix floating-point error for GPS points distance computation
* Allow inline playback of video in ARKit mode

## Version 7.0.1 - 2020/01/17

* iOS: fix flickering when device has "flat" orientation
* ARKit 3D-player: increase camera far plane
* ARKit 3D-player: allow media playback without user interaction
* ARKit 3D-player: avoid screen dim
* ARKit 3D-player: fix issue when switching between cameras

## Version 7.0.0 - 2019/12/18

* Add ARKit support. Allows placing 3D objects on an horizontal plane (floor, table, etc.).

Starting with release 7.0.0, you must also include link the following frameworks with your application:

```
- ARKit
- Metal
- MetalKit
- WebKit
```

The ARKit feature requires a supported devices running iOS 11 or above.
If the device is not supported, the 3D model will be displayed in a viewer rather than in AR.

## Version 6.5.18 - 2019/11/08

* Fix wrong synchronization progress percentage

## Version 6.5.17 - 2019/11/04

* Fix 3D transparency problem with some 3D models

## Version 6.5.15 - 2019/10/30

* Adapt SDK for iOS 13 and Xcode 11: avoid opening fullscreen views in modal mode

## Version 6.5.14 - 2019/08/07

* Add method for changing the license key once the SDK has already been initialized
* Add method for forcing the interface language

## Version 6.5.13 - 2019/07/08

* Fix memory leak

## Version 6.5.12 - 2019/07/01

* Allow enabling contents by tag without requiring a new synchronization.
* Fix ratio of "screen relative annotations" (e.g. fullscreen contents and close button).

## Version 6.5.11 - 2019/04/23

* Fix deprecated push mechanism. It requires adding `UserNotifications.framework` to your linked frameworks.
* Add synchronization mechanism using content creator email.

## Version 6.5.10 - 2019/04/04

* Add video loop support
* Hide "Content" title in top bar of default AR view controller

## Version 6.5.9 - 2019/03/21

* Fix distorted 3D objects

## Version 6.5.8 - 2019/03/19

* Keep synchronized contents when upgrading the application

## Version 6.5.6

* Allow file upload from webview

## Version 6.5.3

* Fix performance issue occurring with some devices on iOS 12

## Version 6.5.2

* Update Dutch translation

## Version 6.5.1

* Disable auto-lock for audio player

## Version 6.5.0

* Improve rendering of 3D objects: add normal mapping support
* Fix popup appearing in loop when camera permission is denied

**NB**: Starting from v.6.5.0, the SDK requires the device capability opengles-3 (iPhone 5S and over)

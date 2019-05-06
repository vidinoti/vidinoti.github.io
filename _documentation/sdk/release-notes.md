---
layout: documentation
title: SDK Release notes
category: Sdk
order: 6
---

# Release notes

* [Android SDK](#android)
* [iOS SDK](#ios)

# Android

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
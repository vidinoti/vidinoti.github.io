---
layout: documentation
title: Create an app - Basics
category: Sdk
order: 1
---

This page describes the fundamentals for using the Vidinoti SDK. For using the SDK, you will need a license key and your application must be registered on V-Director. We describe these steps here.

## 1) Create a V-Director account

If you don't already have a V-Director account, you need to create one [here](https://armanager.vidinoti.com).

## 2) Retrieve your license key

Login to V-Director and open the section "SDK" > "My Licenses". Write down the license key. You will need to integrate this license key in your application source code.

![My licenses]({{ site.url }}/img/cms/sdk-licenses.png)

## 3) Register your application(s) in V-Director

Additionnaly to using a license key, you need to register your application in V-Director. If you don't do it, the SDK won't be able to connect to the server (like if the license key is incorrect). In V-Director, open the section "SDK" > "My Applications".

![My applications]({{ site.url }}/img/cms/sdk-applications.png)

Click the "Add a new application" button.

![New application popup]({{ site.url }}/img/cms/sdk-newapplication.png)

Fill out the form.
The "App name" is the application name, it is only used for describing the application (e.g. "My Awesome App (Android)").
The app identifier must correspond to the **bundle identifier** for **iOS**, or the application **package name** for **Android**.
Select the correct platform (either iOS or Android).

**NB:** if your application is multi-platform (Android and iOS), you need to add both of them.

## 4) Download the SDK

Open the section "SDK" > "Downloads" and download the required SDK.

![SDK downloads]({{ site.url }}/img/cms/sdk-downloads.png)

## 5) Integrate the SDK in your application

**Android native:** Look at the simple demo application present in the SDK zip file and follow the guide here: [Create an Android app]({{ '/documentation/sdk/create-android-app' | relative_url }})

**iOS native:** Look at the simple demo application present in the SDK dmg file. And look at the Swift documentation here: [Create an iOS app in Swift]({{ '/documentation/sdk/create-a-swift-app' | relative_url }})

**Cordova:** Follow the instructions for using the cordova plugin: [https://github.com/vidinoti/cordova-plugin-PixLive](https://github.com/vidinoti/cordova-plugin-PixLive)

**Ionic 1:** Follow the instructions of the plugin: [https://github.com/vidinoti/angular-pixlive](https://github.com/vidinoti/angular-pixlive)

**Ionic 2+:** Follow the instructions of the plugin: [https://github.com/vidinoti/ionic-module-pixlive](https://github.com/vidinoti/ionic-module-pixlive)

**Xamarin:** Follow the instructions of the plugin: [https://github.com/vidinoti/pixlive-xamarin-demo](https://github.com/vidinoti/pixlive-xamarin-demo)

Additional documentation is available here: [https://armanager.vidinoti.com/?page=arsdk_doc](https://armanager.vidinoti.com/?page=arsdk_doc)


---
layout: documentation
title: Configure push notifications for Android
category: Sdk
order: 2
---

# Introduction

This page describes how to register your application with the Google push notification service.

# Instructions

You need to create a new Firebase project in order to obtain the API key for Google Cloud Messaging.

1) Create a new Firebase project. Go to [https://console.firebase.google.com/](https://console.firebase.google.com/) and add a new project.

![Firebase: add project]({{ site.url }}/img/android_push_configuration/gcm_new_firebase_project.png)

Give your project a name

![Firebase: create new project]({{ site.url }}/img/android_push_configuration/gcm_new_project.png)

2) Once in your project page, go to the settings (top left of the page).

![Firebase: settings]({{ site.url }}/img/android_push_configuration/gcm_firebase_settings.png)

3) Open the "CLOUD MESSAGING" tab. All the necessary keys are visible in this page.

![Firebase: cloud messaging settings]({{ site.url }}/img/android_push_configuration/gcm_key.png)

4) The **Sender ID** is the ID that needs to be configured within your app. The code would look like the following:

```
String senderID = "1234"; // The Sender ID retrieved from the Firebase console
VDARSDKController.getInstance().setNotificationsSupport(true, senderID);
```

5) Copy the **Legacy server key** and paste it in PixLive Maker (PixLive Maker > PixLive SDK > My Applications).

![Configuration in PixLive Maker]({{ site.url }}/img/android_push_configuration/gcm_cms.png)
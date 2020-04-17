---
layout: documentation
title: Nearby GPS tracking and notifications
category: Sdk
order: 7
---

# Introduction

This page describes how to setup the SDK to send a notification when a user enters a new GPS point even when the application is in the background. Notifications are sent only the first time the user enters the GPS point.

# Nearby GPS Tracking

The nearby GPS Tracking is a foreground service showing notifications when the user enters a new GPS point. Since it is a foreground service it will continue to run when the application is in the brackground. To start the GPS tracking call:

```
VDARSDKController.getInstance().startGPSNotifications();
VDARSDKController.getInstance().startNearbyGPSDetection();
```

When the application is not in the background you may want to disable the notifications. In order to disable the notifications call:

```
VDARSDKController.getInstance().stopGPSNotifications();
```

When the notifications are disabled the service will no longer send notifications. You can at anytime re-enable the notifications by calling:

```
VDARSDKController.getInstance().startGPSNotifications();
```

Checking the user position in the background may have an impact on the battery. You can stop the GPS tracking at any time by calling:

```
VDARSDKController.getInstance().stopNearbyGPSDetection();
```

## Custom parameters

The SDK provides a way to start the nearby GPS tracking with custom parameters:

```
startNearbyGPSDetection(long minGPSIntervalMS, float minGPSDistance, int detectionInterval, float maxDetectionRadius)
```

* where minGPSIntervalMS is the minimal time interval before a new user position is fetched
* where minGPSDistance is the minimal distance the user has to move before it is considered as a new position
* where detectionInterval is after how long a gps point is reconsidered as new
* where maxDetectionRadius is the maximal detection radius

## Reset the visited points list

It is possible to reset the visited points list. After that every point already visited will be considered new again and will send a notification if they are enabled.

```
import com.vidinoti.android.vdarsdk.geopoint.GeoPointManager;

...

GeoPointManager.resetNewNearbyGPSPoints();
```


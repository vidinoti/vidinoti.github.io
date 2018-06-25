---
layout: post
title: Upgrade from Android 6.3 or earlier
date:   2018-05-01 12:00:00 +0200
categories: tech
---

# Android push notifications: Migration from GCM to FCM.

Google has deprecated GCM (Google Cloud Messaging) and will remove its support as soon as April 11, 2019. For supporting Android push notifications from V-Director after this date, you need upgrade your app with the latest Vidinoti SDK.

Follow the steps described here for migrating your app to the new Firebase Cloud Messaging.

## Remove code related to GCM

### Gradle build file

In your app App-level `build.gradle` (`yourProject/yourAppModule/build.gradle`), remove any GCM dependency.

Delete the line `compile 'com.google.android.gms:play-services-gcm:..'`.

### AndroidManifest file

Delete the permission related to GCM.
```
    <!--  Permissions for notifications -->
    <uses-permission android:name="com.google.android.c2dm.permission.RECEIVE" />
    <uses-permission android:name="android.permission.GET_ACCOUNTS" />

    <permission android:name="com.mycompany.myarapplication.permission.C2D_MESSAGE" android:protectionLevel="signature" />
    <uses-permission android:name="com.mycompany.myarapplication.permission.C2D_MESSAGE" />
```

Delete the service and receiver.
```
    <!-- For notifications -->
    <service android:name=".GcmService" android:exported="false">
        <intent-filter>
            <action android:name="com.google.android.c2dm.intent.RECEIVE" />
        </intent-filter>
    </service>
    <receiver
        android:name="com.google.android.gms.gcm.GcmReceiver"
        android:exported="true"
        android:permission="com.google.android.c2dm.permission.SEND" >
        <intent-filter>
            <action android:name="com.google.android.c2dm.intent.RECEIVE" />
            <category android:name="com.mycompany.myarapplication" />
        </intent-filter>
    </receiver>
```

### Delete unused class

Delete the `GcmService` class that was referenced in your `AndroidManifest.xml` file.

## Add support for FCM

Follow the guide available in the documentation: [Configure push notifications for Android]({{ '/documentation/sdk/android-push' | relative_url }})


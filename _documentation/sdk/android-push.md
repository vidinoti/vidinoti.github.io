---
layout: documentation
title: Configure push notifications for Android
category: Sdk
order: 4
---

# Introduction

This page describes how to register and configure your application with the Google push notification service.

# Firebase project and V-Director

You need to create a new Firebase project in order to obtain the API keys for using FCM.

## Create a Firebase project

Create a new Firebase project. Go to [https://console.firebase.google.com/](https://console.firebase.google.com/) and add a new project.

![Firebase: add project]({{ site.url }}/img/android_push_configuration/gcm_new_firebase_project.png)

Give your project a name

![Firebase: create new project]({{ site.url }}/img/android_push_configuration/gcm_new_project.png)

## Register your Android app

Register your Android application. Click "Add Firebase to your Android app". Enter your application package name and retrieve the file `google-services.json`. We will need this file later.

![Firebase: create new project]({{ site.url }}/img/android_push_configuration/fcm_add_android.png)

## Configure V-Director

In your Firebase project page, go to the settings (top left of the page).

![Firebase: settings]({{ site.url }}/img/android_push_configuration/gcm_firebase_settings.png)

Open the "CLOUD MESSAGING" tab. And copy the **Legacy server key**.

![Firebase: cloud messaging settings]({{ site.url }}/img/android_push_configuration/gcm_key.png)

Go to V-Director under the "My applications" section (V-Director > SDK > My Applications). Edit your application and add the **legacy server key** in the "Push notification API key" field.

![Configuration in V-Director]({{ site.url }}/img/android_push_configuration/gcm_cms.png)

# Adapt your application

This section describes the different steps that you must perform on your application code. For a complete example, see the demo application provided with the Vidinoti SDK.

## Google service json file

Take the file `google-services.json` that you have created earlier and move it to your Android app module.

## Gradle files

Edit your build gradle files.

**Project-level build.gradle (yourProject/build.gradle):**

```
buildscript {
  dependencies {
    // Add this line
    classpath 'com.google.gms:google-services:3.2.0'
  }
}
```

**App-level build.gradle (yourProject/yourAppModule/build.gradle):**

```
dependencies {
  // Add this line
  compile 'com.google.firebase:firebase-messaging:15.0.0'
}
...
// Add to the bottom of the file
apply plugin: 'com.google.gms.google-services'
```

## App source code

### MyInstanceIDListenerService

Create a new service that will receive the FCM token renewals. The token must then be forwarded to the Vidinoti SDK.

```
import com.google.firebase.iid.FirebaseInstanceId;
import com.google.firebase.iid.FirebaseInstanceIdService;
import com.vidinoti.android.vdarsdk.VDARSDKController;

/**
 * Service required for the push notifications.
 * It receives the update of the Firebase token that needs to be forwarded to the Vidinoti SDK.
 */
public class MyInstanceIDListenerService extends FirebaseInstanceIdService {

    @Override
    public void onTokenRefresh() {
        // Forward the token to the Vidinoti SDK
        VDARSDKController controller = VDARSDKController.getInstance();
        if (controller != null) {
            String refreshedToken = FirebaseInstanceId.getInstance().getToken();
            controller.updatePushNotificationToken(refreshedToken);
        }
    }

}
```

### MyFcmListenerService

Creates a service that receives the push notifications. By default, we create a notification in the status bar.

```
import android.app.NotificationChannel;
import android.app.NotificationManager;
import android.app.PendingIntent;
import android.content.Context;
import android.content.Intent;
import android.media.RingtoneManager;
import android.os.Build;
import android.support.v4.app.NotificationCompat;
import android.util.Log;

import com.google.firebase.messaging.FirebaseMessagingService;
import com.google.firebase.messaging.RemoteMessage;

import java.util.Map;

/**
 * Service that receives the push notifications.
 * When a new notification is received, it creates a new notification in the status panel.
 * When the notification is opened, it opens the start activity and some information needs to
 * be forwarded to the Vidinoti SDK. See the documentation at https://vidinoti.github.io/ for
 * more information.
 */
public class MyFcmListenerService extends FirebaseMessagingService {

    private static final String TAG = MyFcmListenerService.class.getName();

    private static final String CHANNEL_ID = "vidinoti_push_channel";

    @Override
    public void onMessageReceived(RemoteMessage remoteMessage) {
        Map<String, String> data = remoteMessage.getData();

        NotificationManager notificationManager = (NotificationManager) getSystemService(Context.NOTIFICATION_SERVICE);
        if (notificationManager == null) {
            Log.w(TAG, "NotificationManager is null");
            return;
        }

        String nid = data.get("nid");
        String message = data.get("message");
        if (nid == null || nid.length() == 0 || message == null || message.length() == 0) {
            Log.w(TAG, "Invalid push data");
            return;
        }

        // Get the default intent of the app
        Intent appIntent = getPackageManager().getLaunchIntentForPackage(getPackageName());
        if (appIntent == null) {
            Log.w(TAG, "Launch intent not found");
            return;
        }
        appIntent.putExtra("nid", nid);
        appIntent.putExtra("remote", true);

        PendingIntent contentIntent = PendingIntent.getActivity(this, 0, appIntent, PendingIntent.FLAG_UPDATE_CURRENT);

        createNotificationChannel(notificationManager);
        NotificationCompat.Builder mBuilder = new NotificationCompat.Builder(this, CHANNEL_ID)
                .setSmallIcon(R.drawable.notification_icon)
                .setContentTitle(getString(R.string.app_name))
                .setContentText(message)
                .setContentIntent(contentIntent)
                .setAutoCancel(true)
                .setPriority(NotificationCompat.PRIORITY_DEFAULT)
                .setSound(RingtoneManager.getDefaultUri(RingtoneManager.TYPE_NOTIFICATION));

        //To make sure notification ID is unique over time
        int when = (int) ((System.currentTimeMillis() - 1419120000000L) / 1000L);

        notificationManager.notify(when, mBuilder.build());
    }

    /**
     * Creates a channel if necessary (required from Android API 26)
     */
    private void createNotificationChannel(NotificationManager notificationManager) {
        if (Build.VERSION.SDK_INT >= Build.VERSION_CODES.O) {
            CharSequence name = "Vidinoti";
            String description = "Notification about latest news";
            int importance = NotificationManager.IMPORTANCE_DEFAULT;
            NotificationChannel channel = new NotificationChannel(CHANNEL_ID, name, importance);
            channel.setDescription(description);
            notificationManager.createNotificationChannel(channel);
        }
    }
}
```

### AndroidManifest

Add the two above services to your `AndroidManifest.xml` file.

```
    <service android:name=".MyInstanceIDListenerService">
        <intent-filter>
            <action android:name="com.google.firebase.INSTANCE_ID_EVENT" />
        </intent-filter>
    </service>
    <service android:name=".MyFcmListenerService">
        <intent-filter>
            <action android:name="com.google.firebase.MESSAGING_EVENT" />
        </intent-filter>
    </service>
```

### Launch activity

Add the following code in the `onCreate` method of your launch Activity. It gives the information about the push notification to the Vidinoti SDK. The SDK will then handle the notification appropriately.

```
        final Intent intent = getIntent();
        if (intent != null && intent.getExtras() != null
                && intent.getExtras().getString("nid") != null) {

            final String nid = intent.getExtras().getString("nid");

            VDARSDKController.getInstance().addNewAfterLoadingTask(
                    new Runnable() {
                        @Override
                        public void run() {
                            boolean remote = intent.getExtras().getBoolean("remote");
                            VDARSDKController.getInstance().processNotification(nid, remote);
                        }
                    });
        }
```

### Enable notification after the SDK initialization

Call `VDARSDKController.getInstance().setNotificationsSupport(true);` once the SDK has been initialized.

# Send push notification

Once you have done all the above steps, you should be able to send push notifications to your application via the V-Director platform.



*Updated on: April 3rd, 2018*


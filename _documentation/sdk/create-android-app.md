---
layout: documentation
title: Create an Android app
category: Sdk
order: 3
---

# Introduction

This page gives you a few hints for integrating the Vidinoti SDK in an Android application.

You can find some additional information and the API reference there: [Android SDK Reference](http://doc.vidinoti.com/vdarsdk/web/android/latest/reference/packages.html)

# Requirement / getting started

Follow the steps described in [Create an app - Basics]({{ '/documentation/sdk/create-an-app' | relative_url }}). In summary, do the following:

1. Connect to V-Director
2. Download the latest iOS SDK version under "SDK" > "Downloads"
3. Retrieve your license key under "SDK" > "Licenses". Copy it somewhere, you will need it later.
4. Open the section "SDK" > "My Applications".
5. Create a new application with your application bundle ID. It is important that the registered bundle ID corresponds to your application otherwise the SDK won't be able to connect to the backend. If you use several bundle ID (e.g. for staging), add each of them as a new application.

# Add the SDK to your application

To embed the Vidinoti SDK in your Android application using Android Studio, follow the below steps:

* Create, if not existing, a `libs` directory in the `app` directory of your project.
* Copy the file `vdarsdk-release.aar` from the Vidinoti SDK into this folder.
* In the build.gradle file of your application, add the following lines:

```
repositories {
    mavenCentral()
    flatDir {
        dirs 'libs'
    }
}

dependencies {
    implementation name:'vdarsdk-release', ext:'aar'
    implementation 'com.android.support:appcompat-v7:28.0.0'
    implementation ('com.github.barteksc:android-pdf-viewer:2.7.0') {
        exclude group: 'com.android.support'
    }
    // your own dependencies are here
}
```

Before using the SDK, you need to initialize it by calling `VDARSDKController#startSDK(Context, String, String)`. This can be done in the `onCreate` from a custom `Application` or from your main activity.

This method will start the whole Vidinoti Augmented reality system by loading the locally saved AR & Beacon content and setting up everything for the rendering. This loading process is done asynchronously to the call. That's why you should make sure to check the result of `VDARSDKController#isLoaded()` before calling any functions of the SDK Controller.

You can also schedule a task to be run when the loading process is over by calling the `VDARSDKController#addNewAfterLoadingTask(Runnable)` method. All the tasks scheduled will be run on the main UI thread.

Note that starting the VDARSDKController if it has already been started has no effect. Moreover, the `VDARSDKController` is a singleton instance and, therefore, will be the same instance for the whole application life.

Some devices may not be supported by the SDK. You can check it by calling `VDARSDKController#isDeviceSupported()`. If you try to use the SDK with an unsupported device, it may result in a crash.

You need to assign an `Activity` as the main AR activity using the SDK controller (only one activity can use the SDK Controller at a time). You can do this by calling the following:

```
VDARSDKController.getInstance().setActivity(this);
```

Start the download of some contents from your V-Director account. You can start a synchronization so that all contents you have published on the platform will be available on the users devices. When you delete / add new contents in your account, the corresponding contents will also be added/deleted on users devices. The best practice is to launch a synchronization every time the application is launched, even if the AR activity is not opened. This allows a seamless user interaction as the user won't need to wait for the content to be loaded when the AR activity is opened.

The following sample code shows how to make a synchronization:

```
VDARSDKController controller = VDARSDKController.getInstance();
if (controller == null) {
    return;
}
controller.addNewAfterLoadingTask(new Runnable() {
    public void run() {
        VDARRemoteController.getInstance().syncRemoteContextsAsynchronouslyWithPriors(priors, new Observer() {
            public void update(Observable observable, Object data) {
                VDARRemoteController.ObserverUpdateInfo info = (VDARRemoteController.ObserverUpdateInfo) data;
                if (info.isCompleted()) {
                    Log.v(TAG, "Synchronization over. Synced " + info.getFetchedContexts().size() + " contents:");
                }
            }
        });
    }
});
```

The Vidinoti SDK comes with a view class `VDARAnnotationView` rendering the camera view and the annotations. Add this view to your `Activity` or `Fragment` to play AR contents.

A camera object has to be created to allow the SDK to get access to the camera. The camera is automatically registered within the SDK upon creation:

	DeviceCameraImageSender imageSender = new DeviceCameraImageSender();

You should now add the `VDARAnnotationView#onResume()` and `VDARAnnotationView#onPause()` call on the `VDARAnnotationView` that you have embedded in the corresponding lifecycle methods of your Activity or Fragment. Not doing so will make your application crash.

Your application is now ready to run the SDK. Explore the API and discover other features.

Don't hesitate to ask your questions to the support: support(at)vidinoti.com

# Other features

## Enable QR Code recognition:

```
VDARSDKController.getInstance().setEnableCodesRecognition(true);
```

Note that this not only provide to your activity the ability to recognize standard QR code but the SDK understand special QR codes that can be used to trigger the download of a specific content, to trigger a tag-based synchronization of contents. See the `setEnableCodesRecognition(boolean)` method documentation for more information.
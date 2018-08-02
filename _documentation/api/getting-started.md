---
layout: documentation
title: Getting started
category: API
order: 1
---

This page describes the fundamentals for using the API exposed by V-Director.

# Register your application

For accessing the API from your application, you need to register your application in V-Director. If you have already integrated the SDK in your application, you probably have already done the following.

## 1) Create a V-Director account

If you don't already have a V-Director account, you need to create one [here](https://armanager.vidinoti.com).

## 2) Retrieve your license key

Login to V-Director and open the section "SDK" > "My Licenses". Write down the license key. You will use it for authenticating with the API.

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

# API Authentication

In order to authenticate the HTTP requests, custom headers are used. For all API HTTP requests, add the following headers:

| Header field name | Header value | Example |
|-------|--------|---------|
| `PixLiveSDK-AppId` | Your app ID (that you configured just above) | `com.vidinoti.testapp` |
| `PixLiveSDK-Platform` | `iOS` or `android` | `android` |
| `PixLiveSDK-LicenseKey` | Your SDK license key | `0123456789abcdefghij` |

## Example

You can test that everything is working with a simple `curl` command:

    curl -H "PixLiveSDK-AppId: com.vidinoti.testapp" -H "PixLiveSDK-Platform: android" -H "PixLiveSDK-LicenseKey: 0123456789abcdefghij" https://sdk.vidinoti.com/v1/tour

# API Endpoint

The API endpoint is `https://sdk.vidinoti.com`
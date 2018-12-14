---
layout: post
title: Workaround for iOS SDK crash when building a Swift app with Xcode 10.1
date:   2018-12-13 12:00:00 +0200
categories: tech
---

# Description of the problem

We discovered a bug when building iOS Swift applications integrating our Vidinoti SDK with Xcode 10.1. The application will crash at startup if running on device running iOS 11. This is very unfortunate and we propose here a workaround.

We filled a bug report to Apple and we hope that it will be resolved for the next release of Xcode.

In the meantime, please do the following for avoiding the bug:

* Create two Objective-C files on your project called `VDARLocalizationManager.m` and `VDARLocalizationManager.h`.
* Edit the files and add the content below.

### VDARLocalizationManager.h

    #import <Foundation/Foundation.h>

    @interface VDARLocalizationManager : NSObject {
        
    }

    + (VDARLocalizationManager*)sharedInstance;

    @end



### VDARLocalizationManager.m


    #import "VDARLocalizationManager.h"


    @implementation VDARLocalizationManager

    + (VDARLocalizationManager*)sharedInstance
    {
        return nil;
    }

    @end

---
layout: documentation
title: Synchronization mechanism
category: Sdk
order: 3
---

# Introduction

This page describes the synchronization mechanism used by the SDK. The synchronization allows retrieving the published contents that have been created on V-Director and makes them available on the mobile device. This step is mandatory otherwise the SDK will never retrieve data from the server and remain "empty".

There are different ways of executing the synchronization. Either we synchronize all the contents or only a subset of them using a filter. These filters are often called "priors". We described some synchronization scenarios below.

# Default synchronization - sync with all contents

By default, the synchronization retrieves all contents that are published on V-Director. However, we recommend using a synchronization filter. It allows having a more flexible system, see the next section.

For retrieving all published contents, there are two things to do.

In V-Director, configure your application such that the "Tag management system" is NOT checked (In V-Director > SDK > My Applications). If you check the checkbox, the server expects some synchronization filters and will not return all the contents.

![Synchronization without filter]({{ site.url }}/img/cms/sdk-applications-notagfilter.png))

In your source code, call the synchronization function without any parameters.

### Android

```
VDARSDKController controller = VDARSDKController.getInstance();
if (controller == null) {
    return;
}
controller.addNewAfterLoadingTask(new Runnable() {
    public void run() {
        VDARRemoteController.getInstance().syncRemoteContextsAsynchronouslyWithPriors(null, new Observer() {
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

### iOS

```
func synchronize() {
    if syncing {
        return
    }
    syncing = true
    VDARSDKController.sharedInstance()?.afterLoadingQueue.addOperation {
        DispatchQueue.main.async {
            VDARRemoteController.sharedInstance()?.syncRemoteModelsAsynchronously(withPriors: [], withCompletionBlock: {result, error in
                syncing = false
                if let error = error {
                    print("The system got an error during synchronization: \(error)")
                }
            })
        }
    }
}
```

# Selective synchronization

For having a more flexible system, we recommend using filters for the synchronization. Even if you don't need it from the beginning, you may want to use tags later on if your number of contents increase or if you want to provide multilingual content.

First we need to enable the filter mechanism on V-Director. Go to V-Director > SDK > My Applications and check the tag management system for your application.

![Synchronization without filter]({{ site.url }}/img/cms/sdk-applications-tagfilter.png))

## Synchronization per tag

You can use a tag filter for retrieving only the contents belonging to a given tag.
In particular, you must use this mechanism for multilingual content. A custom "language" tag is assigned to the contents when the multilingual content is enabled (for enabling the multilingual mode, go to V-Director > SDK > SDK Settings and configure the available languages; then assign your content to one or several language).

In your application code, you must ask for synchronizing with a given tag. For example, if we want to retrieve all the French contents; we asks to synchronize with the tag "lang_fr". See example below.

### Android

```
[...]
List<VDARPrior> priors = new ArrayList<>();
priors.add(new VDARTagPrior("lang_fr"));
VDARRemoteController.getInstance().syncRemoteContextsAsynchronouslyWithPriors(priors, new Observer() {
[...]
```

### iOS

```
[...]
let priors: [Any] = [VDARTagPrior(tagName: "lang_fr")!]
VDARRemoteController.sharedInstance()?.syncRemoteModelsAsynchronously(withPriors: priors, withCompletionBlock: {result, error in
[...]
```

## Other filters

There exist other filters than the tag filter. For instance, you can synchronize per Tour (see `VDARTourPrior`) or you can combine several filters. For instance, you can synchronize with `(tag Category1 AND tag lang_en) OR (Category2 and lang_en)` (give a list of priors and see `VDARIntersectionPrior`).

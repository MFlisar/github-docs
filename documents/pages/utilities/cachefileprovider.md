---
icon: material/github
library: CacheFileProvider
module: core
---

{% include 'badges_header.md' %}

<i>{{ projects[page.meta.library]['info'] }}</i>

## :material-check-all: Features

* offers functions to copy a file to the underlying `FileProvider` folder
* allows to simply share a file without any setup from user side
* minimal size - contains only **8 functions** inside **2 classes**

## :link: Dependencies

This library does not have any dependencies!

## :simple-gradle: Setup Gradle

{% include 'jitpack_setup.md' %}

## :keyboard: Usage

It works as simple as following:

```kotlin
// create a file that can be shared with external apps
val cacheFile = CachedFileProvider.copyFileToCache(context, file)
val cacheFile = CachedFileProvider.copyFileToCache(context, uri)

// get the shareable uri for this file
val uri = CachedFileProvider.getCacheFileUri(context, cacheFile.name)

// now you can share the uri with external apps
// ATTENTION: if you share the file via an intent,
// also use Intent.FLAG_GRANT_READ_URI_PERMISSION
// ...

```

:bulb: Tipp

If you want to share the cached file with an email app, then check out [FeedbackManager](feedbackmanager.md) - its an utility based on `CacheFileProvider` that does exactly that. It also takes care of the above mentioned `Intent.FLAG_GRANT_READ_URI_PERMISSION`.
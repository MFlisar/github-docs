---
icon: material/github
library: CacheFileProvider
module: core
---

{% include 'badges_header.md' %}

<i>This is a minimal library with a **few lines of code** and without dependencies that offers a simple file provider (simple read only access for sharing files with other apps).</i>

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
val cacheFile = CachedFileProvider.copyFileToCache(context, uri)
val uri = CachedFileProvider.getCacheFileUri(context, cacheFile.name)
// now you can share the uri with external apps
// ATTENTION: if you share the file via an intent, also use Intent.FLAG_GRANT_READ_URI_PERMISSION

// alternatively call the copy function with a File
val cacheFile = CachedFileProvider.copyFileToCache(context, file)
```
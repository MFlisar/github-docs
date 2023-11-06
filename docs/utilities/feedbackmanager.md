---
icon: material/github
library: FeedbackManager
module: core
---

{% include 'badges_header.md' %}

<i>This is a very small library that allows you to **send feedback** from an app **without internet permission** via email, either directly or via an unintrusive notification.</i>

## :material-check-all: Features

* send feedback mail via a single function
* show a feedback notification via a single function
* no internet permission needed - everything is done via a shared `Intent` which then can by handled by an installed email app
* minimal size - only a **few functions** inside **2 classes**

## :link: Dependencies

| Dependency | Version |
|:-|-:|
| [CacheFileProvider](https://github.com/MFlisar/CacheFileProvider) | 0.3.0 |

## :simple-gradle: Setup Gradle

{% include 'jitpack_setup.md' %}

## :keyboard: Usage

It works as simple as following:

```kotlin
val feedback = Feedback(
    receivers = listOf("some.email@gmail.com"),
    subject = "Subject of mail",
    text = "Some text",
    textIsHtml = false, // indicates if text is holding html text or plain texz
    attachments = listOf(
        FeedbackFile(uri),
        FeedbackFile(file)
    )
)
feedback.startEmailChooser(context, titleForChooser)
```

## :material-professional-hexagon: Advanced Usage

???+ code "Create an `Intent` for later"

    ```kotlin
    val feedback = Feedback(...)
    val intent = feedback.buildIntent(
        context = context,
        chooserTitle = "Title of the Email Chooser"
    )
    ```

???+ code "Show a notification"

    This allows you to show a notification which will start the email chooser if the user clicks on the notification only.

    ```kotlin
    val feedback = Feedback(...)
    feedback.startNotification(
        context = context,
        chooserTitle = "Title of the Email Chooser"
        notificationTitle = "Notification",
        notificationText = "Message",
        notificationIcon = R.mipmap.icon,
        notificationChannel = "ChannelName",
        notificationId = 1234 /* channel id */
    )
    ```
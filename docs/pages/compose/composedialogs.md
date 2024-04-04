---
icon: simple/jetpackcompose
library: ComposeDialogs
demo_link: https://github.com/MFlisar/ComposeDialogs/blob/master/demo/src/main/java/com/michaelflisar/composedialogs/demo
screenshots: https://raw.githubusercontent.com/MFlisar/ComposeDialogs/master/screenshots/dark
modules:
  - core: 
    - core
  - dialog:
    - dialog-info
    - dialog-input
    - dialog-number
    - dialog-list
    - dialog-progress
    - dialog-time
    - dialog-date
    - dialog-color
    - dialog-billing
---

{% include 'badges_header.md' %}

<i>{{ projects[page.meta.library]['info'] }}</i>

## :camera: Screenshots

|||||
| :-: | :-: | :-: | :-: |
| **Info Dialog** {: colspan=4 style="background-color:var(--md-primary-fg-color--light);"} | &#8288 {: style="padding:0"} | &#8288 {: style="padding:0"} |  &#8288 {: style="padding:0"} |
| ![Demo]({{ page.meta.screenshots }}/demo_info1.jpg) | ![Demo]({{ page.meta.screenshots }}/demo_info2.jpg) | ![Demo]({{ page.meta.screenshots }}/demo_info3.jpg) | ![Demo]({{ page.meta.screenshots }}/demo_info4.jpg) |
| **Input Dialog** {: colspan=4 style="background-color:var(--md-primary-fg-color--light);"} | &#8288 {: style="padding:0"} | &#8288 {: style="padding:0"} |  &#8288 {: style="padding:0"} |
| ![Demo]({{ page.meta.screenshots }}/demo_input1.jpg) | ![Demo]({{ page.meta.screenshots }}/demo_input2.jpg) | |  |
| **Number Dialog** {: colspan=4 style="background-color:var(--md-primary-fg-color--light);"} | &#8288 {: style="padding:0"} | &#8288 {: style="padding:0"} |  &#8288 {: style="padding:0"} |
| ![Demo]({{ page.meta.screenshots }}/demo_number1.jpg "Demo") | ![Demo]({{ page.meta.screenshots }}/demo_number2.jpg "Demo") | ![Demo]({{ page.meta.screenshots }}/demo_number3.jpg "Demo") | |
| **Date Dialog** {: colspan=4 style="background-color:var(--md-primary-fg-color--light);"} | &#8288 {: style="padding:0"} | &#8288 {: style="padding:0"} |  &#8288 {: style="padding:0"} |
| ![Demo]({{ page.meta.screenshots }}/demo_calendar1.jpg "Demo") | ![Demo]({{ page.meta.screenshots }}/demo_calendar2.jpg "Demo") | ![Demo]({{ page.meta.screenshots }}/demo_calendar3.jpg "Demo") | |
| **Time Dialog** {: colspan=4 style="background-color:var(--md-primary-fg-color--light);"} | &#8288 {: style="padding:0"} | &#8288 {: style="padding:0"} |  &#8288 {: style="padding:0"} |
| ![Demo]({{ page.meta.screenshots }}/demo_time1.jpg "Demo") | ![Demo]({{ page.meta.screenshots }}/demo_time2.jpg "Demo") |||
| **Color Dialog** {: colspan=4 style="background-color:var(--md-primary-fg-color--light);"} | &#8288 {: style="padding:0"} | &#8288 {: style="padding:0"} |  &#8288 {: style="padding:0"} |
| ![Demo]({{ page.meta.screenshots }}/demo_color1.jpg "Demo") | ![Demo]({{ page.meta.screenshots }}/demo_color2.jpg "Demo") | ![Demo]({{ page.meta.screenshots }}/demo_color3.jpg "Demo") | ![Demo]({{ page.meta.screenshots }}/demo_color4.jpg "Demo") |
| **List Dialog** {: colspan=4 style="background-color:var(--md-primary-fg-color--light);"} | &#8288 {: style="padding:0"} | &#8288 {: style="padding:0"} |  &#8288 {: style="padding:0"} |
| ![Demo]({{ page.meta.screenshots }}/demo_list1.jpg "Demo") | ![Demo]({{ page.meta.screenshots }}/demo_list2.jpg "Demo") | ![Demo]({{ page.meta.screenshots }}/demo_list3.jpg "Demo") | ![Demo]({{ page.meta.screenshots }}/demo_list4.jpg "Demo") |
| ![Demo]({{ page.meta.screenshots }}/demo_list5.jpg "Demo") | ![Demo]({{ page.meta.screenshots }}/demo_list6.jpg "Demo") | ![Demo]({{ page.meta.screenshots }}/demo_list7.jpg "Demo") | |
| **Progress Dialog** {: colspan=4 style="background-color:var(--md-primary-fg-color--light);"} | &#8288 {: style="padding:0"} | &#8288 {: style="padding:0"} |  &#8288 {: style="padding:0"} |
| ![Demo]({{ page.meta.screenshots }}/demo_progress1.jpg "Demo") | ![Demo]({{ page.meta.screenshots }}/demo_progress2.jpg "Demo") |||

## :material-check-all: Features

* with this ibrary you get a very simple way to show dialogs
* supports showing dialogs as *dialogs*  or *bottom sheets*
* easily extendible - creating a new dialog is just a few lines of code

**All features are splitted into separate modules, just include the modules you want to use!**

## :link: Dependencies

**Compose**

| Dependency | Version | Infos |
|:-|-:|:-:|
| [Compose BOM](https://developer.android.com/jetpack/compose/bom/bom){target=_blank} | `2024.02.01` | [Mapping](https://developer.android.com/jetpack/compose/bom/bom-mapping){target=_blank} |
| Material3 | `1.2.0` | |

**Library**

| Module | Dependency | Version |
|:-|:-|-:|
| `core` | - |  |
| `dialog-info` | - |  |
| `dialog-input` | - |  |
| `dialog-number` | - |  |
| `dialog-list` | - |  |
| `dialog-progress` | - |  |
| `dialog-time` | - |  |
| `dialog-date` | - |  |
| `dialog-color` | - |  |
| `dialog-billing` | [KotBilling](https://github.com/MFlisar/KotBilling) | 0.6 |

## :simple-gradle: Setup Gradle

{% include 'jitpack_setup.md' %}

## :keyboard: Usage

```kotlin

// create and remember a state
val state = rememberDialogState()

// show a dialog if necessary
if (state.showing)
{
    DialogInfo(
        state = state,
        // Custom - Required
        info: String,
        // Custom - Optional
        infoLabel: String = "",
        // Base Dialog -  Optional - all options can be set up with custom attributes, following are just the default examples
        title: (@Composable () -> Unit)? = null,
        icon: (@Composable () -> Unit)? = null,
        style: DialogStyle = DialogDefaults.styleDialog(), // DialogDefaults.styleBottomSheet() => both have a few settings...
        buttons: DialogButtons = DialogDefaults.buttons(),
        options: Options = Options(),
        onEvent: (event: DialogEvent) -> Unit = {
            // optional event handler for all dialog events
        }
    )
}

// show the dialog inside a button press event or similar
Button(onClick = { state.show() }) {
    Text("Show Dialog")
}
```

Alternatively, if you want to use one dialog with many items (e.g. for list items) you can do following:

```kotlin
// create and remember a state with data (e.g. an Integer)
val state = rememberDialogState<Int>(data = null)

// show a dialog if necessary
if (state.showing)
{
    val data = state.requireData()
    DialogInfo(
        state = state,
        // Custom - Required
        info = "Data = $data"
    )
}

// a list that uses the dialog
val items = 1..100
LazyColumn {
    items.forEach {
        item(key = it) {
            Button(onClick = { state.show(it) }) {
                Text("Item $it")
            }
        }
    }
}
```

## :dna: Demo

{% include 'github_demo.md' %}

## :material-view-module: Modules and Extensions

??? info-primary "Info Dialog"

    | Preview | | Module |
    | :- | :- | :- |
    | ![Preview]({{ page.meta.screenshots }}/demo_info1.jpg "Preview") | ![Preview]({{ page.meta.screenshots }}/demo_info2.jpg "Preview") | `info` |

    This shows a simple dialog with some informational text.

    ```kotlin title="DialogInfo.kt"
    --8<--
    https://raw.githubusercontent.com/MFlisar/ComposeDialogs/49002d560e59f7cf71167762533d71148e418bba/library/modules/info/src/main/java/com/michaelflisar/composedialogs/dialogs/info/DialogInfo.kt:19:32
    --8<--
    ```

??? info-primary "Input Dialog"

    | Preview | | Module |
    | :- | :- | :- |
    | ![Preview]({{ page.meta.screenshots }}/demo_input1.jpg "Preview") | ![Preview]({{ page.meta.screenshots }}/demo_input2.jpg "Preview") | `input` |

    This shows a dialog with a `InputField`. All its parameters are exposed via the compose function as you can see below, which allows you to simply adjust the `InputField`s behaviour. Additinally you can attach a validator which ensures, that the dialog will only return a valid input and can't be closed otherwise.

    ```kotlin title="DialogInput.kt"
    --8<--
    https://raw.githubusercontent.com/MFlisar/ComposeDialogs/49002d560e59f7cf71167762533d71148e418bba/library/modules/input/src/main/java/com/michaelflisar/composedialogs/dialogs/input/DialogInput.kt:65:93
    --8<--
    ```

??? info-primary "Number Dialog"

    | Preview | | Module |
    | :- | :- | :- |
    | ![Preview]({{ page.meta.screenshots }}/demo_number1.jpg "Preview") | ![Preview]({{ page.meta.screenshots }}/demo_number3.jpg "Preview") | `number` |

    This shows a number **picker** dialog. You can always use the *Input Dialog*  for numbers as well and change its options to accept numbers only and even attach an validator. But this one is meant for picking numbers with the help of one or two increase and decrease buttons.

    ```kotlin title="DialogNumberPicker.kt"
    --8<--
    https://raw.githubusercontent.com/MFlisar/ComposeDialogs/49002d560e59f7cf71167762533d71148e418bba/library/modules/number/src/main/java/com/michaelflisar/composedialogs/dialogs/input/DialogNumberPicker.kt:47:76
    --8<--
    ```
??? info-primary "Date Dialog"

    | Preview | | Module |
    | :- | :- | :- |
    | ![Preview]({{ page.meta.screenshots }}/demo_calendar1.jpg "Preview") | ![Preview]({{ page.meta.screenshots }}/demo_calendar2.jpg "Preview") | `date` |

    This shows a date selector dialog. First day of week, labels, and style can be adjusted to your needs.

    ```kotlin
    --8<--
    https://raw.githubusercontent.com/MFlisar/ComposeDialogs/49002d560e59f7cf71167762533d71148e418bba/library/modules/date/src/main/java/com/michaelflisar/composedialogs/dialogs/datetime/DialogDate.kt:73:87
    --8<--
    ```

??? info-primary "Time Dialog"

    | Preview | Module |
    | :- | :- |
    | ![Preview]({{ page.meta.screenshots }}/demo_time1.jpg "Preview") | `time` |

    This shows a time selector dialog. 24h mode is optional.

    ```kotlin title="DialogTime.kt"
    --8<--
    https://raw.githubusercontent.com/MFlisar/ComposeDialogs/49002d560e59f7cf71167762533d71148e418bba/library/modules/time/src/main/java/com/michaelflisar/composedialogs/dialogs/datetime/DialogTime.kt:33:46
    --8<--
    ```

??? info-primary "Color Dialog"

    | Preview | | Module |
    | :- | :- | :- |
    | ![Preview]({{ page.meta.screenshots }}/demo_color1.jpg "Preview") | ![Preview]({{ page.meta.screenshots }}/demo_color2.jpg "Preview") | `color` |

    This shows a color selector dialog. A table with predefined material colors as well as a customisation page will be shown. Alpha support can be enabled optionally.

    ```kotlin
    --8<--
    https://raw.githubusercontent.com/MFlisar/ComposeDialogs/49002d560e59f7cf71167762533d71148e418bba/library/modules/color/src/main/java/com/michaelflisar/composedialogs/dialogs/color/DialogColor.kt:57:75
    --8<--
    ```

??? info-primary "List Dialog"

    | Preview | | Module |
    | :- | :- | :- |
    | ![Preview]({{ page.meta.screenshots }}/demo_list1.jpg "Preview") | ![Preview]({{ page.meta.screenshots }}/demo_list2.jpg "Preview") | `list` |
    | ![Preview]({{ page.meta.screenshots }}/demo_list3.jpg "Preview") | ![Preview]({{ page.meta.screenshots }}/demo_list4.jpg "Preview") | `list` |

    This shows a dialog with a list of items. Rendering, selection mode and more is adjustable.

    Here you can create a dialog based on static list data like following:

    ```kotlin title="DialogList.kt"
    --8<--
    https://raw.githubusercontent.com/MFlisar/ComposeDialogs/49002d560e59f7cf71167762533d71148e418bba/library/modules/list/src/main/java/com/michaelflisar/composedialogs/dialogs/list/DialogList.kt:61:79
    --8<--
    ```

    But you can also create list with an asynchronous loader function like following:

    ```kotlin title="DialogList.kt"
    --8<--
    https://raw.githubusercontent.com/MFlisar/ComposeDialogs/49002d560e59f7cf71167762533d71148e418bba/library/modules/list/src/main/java/com/michaelflisar/composedialogs/dialogs/list/DialogList.kt:118:142
    --8<--
    ```
??? info-primary "Progress Dialog"

    | Preview | | Module |
    | :- | :- | :- |
    | ![Preview]({{ page.meta.screenshots }}/demo_progress1.jpg "Preview") | ![Preview]({{ page.meta.screenshots }}/demo_progress2.jpg "Preview") | `progress` |

    This shows a simple loading dialog with a progress indicator.

    ```kotlin title="DialogProgress.kt"
    --8<--
    https://raw.githubusercontent.com/MFlisar/ComposeDialogs/49002d560e59f7cf71167762533d71148e418bba/library/modules/progress/src/main/java/com/michaelflisar/composedialogs/dialogs/progress/DialogProgress.kt:29:43
    --8<--
    ```

??? info-primary "Billing Dialog"

    This shows a dialog with the prices and names of your products. It also shows if a product is already owned and allows to buy unowned prodcuts by clicking them.

    ```kotlin title="DialogBilling.kt"
    --8<--
    https://raw.githubusercontent.com/MFlisar/ComposeDialogs/main/library/modules/billing/src/main/java/com/michaelflisar/composedialogs/dialogs/billing/DialogBilling.kt:74:86
    --8<--
    ```

??? info-primary "Custom Dialog"

    ```kotlin title="Dialog.kt"
    --8<--
    https://raw.githubusercontent.com/MFlisar/ComposeDialogs/49002d560e59f7cf71167762533d71148e418bba/library/core/src/main/java/com/michaelflisar/composedialogs/core/Dialog.kt:43:53
    --8<--
    ```

    ```kotlin
    Dialog(state, title, icon, style, buttons, options, onEvent = onEvent) {
        Text("Text in custom dialog")
        // ...
    }
    ```

## :material-professional-hexagon: Advanced Usage

Check out the dialog state and the dialogs to find out what settings you can use and especially the demo app for a working example.

**Dialog State (simple with a boolean flag or complex with a data object)**

In case of the simple state `true` means that the dialog is visible and `false` that it's not. In case of the complex state holding an object means the dialog is visible and `null` means it's not visible.

```kotlin
--8<--
https://raw.githubusercontent.com/MFlisar/ComposeDialogs/49002d560e59f7cf71167762533d71148e418bba/library/core/src/main/java/com/michaelflisar/composedialogs/core/DialogState.kt:104:110
--8<--
```

In case of the complex state simply use `state.show(data)` to show the dialog and then inside your dialog call `val data = state.requireData()` to get the data from the state.

**CAUTION:** the state must be saveable by `Bundle`, if it is not, provide a custom `saver`!

```kotlin
--8<--
https://raw.githubusercontent.com/MFlisar/ComposeDialogs/49002d560e59f7cf71167762533d71148e418bba/library/core/src/main/java/com/michaelflisar/composedialogs/core/DialogState.kt:56:63
--8<--
```
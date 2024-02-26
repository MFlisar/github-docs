---
icon: simple/jetpackcompose
library: ComposePreferences
demo_link: https://github.com/MFlisar/ComposePreferences/blob/master/demo/src/main/java/com/michaelflisar/composepreferences/demo
screenshots: https://raw.githubusercontent.com/MFlisar/ComposePreferences/master/screenshots/light
previews: https://raw.githubusercontent.com/MFlisar/ComposePreferences/master/screenshots/previews
modules:
  - core: 
    - core
  - screen:
    - screen-bool
    - screen-button
    - screen-input
    - screen-color
    - screen-date
    - screen-time
    - screen-list
    - screen-number
  - extension:
    - extension-kotpreferences
---

{% include 'badges_header.md' %}

<i>{{ projects[page.meta.library]['info'] }}</i>

## :camera: Screenshots

| Screenshots | | |
|-|-|-|
| ![Demo]({{ page.meta.screenshots }}/root.jpg "Demo") | ![Demo]({{ page.meta.screenshots }}/infos.jpg "Demo") | ![Demo]({{ page.meta.screenshots }}/bool.jpg "Demo") |
| ![Demo]({{ page.meta.screenshots }}/button.jpg "Demo") | ![Demo]({{ page.meta.screenshots }}/color.jpg "Demo") | ![Demo]({{ page.meta.screenshots }}/date.jpg "Demo") |
| ![Demo]({{ page.meta.screenshots }}/input.jpg "Demo") | ![Demo]({{ page.meta.screenshots }}/list.jpg "Demo") | ![Demo]({{ page.meta.screenshots }}/number.jpg "Demo") |
| ![Demo]({{ page.meta.screenshots }}/time.jpg "Demo") | | |

## :material-check-all: Features

* offers a simple `PreferenceScreen` composable
* does offer all common used preferences
* manages nesting, visibilities and dependencies for you
* can be easily extended

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
| **Screens** {: colspan=3 style="background-color:var(--md-primary-fg-color--light);"} | &#8288 {: style="padding:0"} | &#8288 {: style="padding:0"} |
| `screen-bool` | - |  |
| `screen-button` | - |  |
| `screen-input` | [ComposeDialogs](https://github.com/MFlisar/ComposeDialogs) | 1.0.5 |
| `screen-color` | [ComposeDialogs](https://github.com/MFlisar/ComposeDialogs) | 1.0.5 |
| `screen-date` | [ComposeDialogs](https://github.com/MFlisar/ComposeDialogs) | 1.0.5 |
| `screen-time` | [ComposeDialogs](https://github.com/MFlisar/ComposeDialogs) | 1.0.5 |
| `screen-list` | [ComposeDialogs](https://github.com/MFlisar/ComposeDialogs) | 1.0.5 |
| `screen-number` | [ComposeDialogs](https://github.com/MFlisar/ComposeDialogs) | 1.0.5 |
| **Extensions** {: colspan=3 style="background-color:var(--md-primary-fg-color--light);"} | &#8288 {: style="padding:0"} | &#8288 {: style="padding:0"} |
| `extension-kotpreferences` | [KotPreferences](https://github.com/MFlisar/KotPreferences) | 0.3 |

## :simple-gradle: Setup Gradle

{% include 'jitpack_setup.md' %}

## :keyboard: Usage

It works as simple as following:

```kotlin
// Preferences must be wrapped in a screen
// => this allows to manage internal hierarchy and screen nesting and everything is managed automatically
// => this also enables internal scrolling
PreferenceScreen(
    // optional parameters to customise this screen
    settings =  PreferenceSettingsDefaults.settings(),
    scrollable = true
) {
    // Preferences at root level
    PreferenceInfo(
        title = {  Text("Info 1") }
    )
    PreferenceBool(
        style = PreferenceBool.Style.Switch,
        value = <value>,
        onValueChange = {
            // update value here
        },
        title = { Text("Bool") }
        )
        
    // Sub Preference - all nested preferences will show if you click the sub preference (and all preferences from other levels will be hidden automatically)
    // + back press + state saving will be handled automatically
    PreferenceSubScreen(
        title = { Text("Menu") }
    ) {
        // sub preferences must be placed here
        // you can even nest another PreferenceSubScreen here - any nesting depth is supported!
    }
    
    // IMPORTANT:
    // don't place any non preference composables here, they won't be correctly shown/hidden and managed by the preference screen because they don't hold any hierarchical data!
    // also gray out and enabled states won't work
    // if you want to place some custom content wrap it inside a `BasePreference` (if you want the default title/subtitle/icon/content layout) 
    // or inside a `BasePreferenceContainer` if you want to place plain content
    
    // Custom 1 - default button inside the content area wrapped as preference => this will work correctly even if used in sub preferences and it will automatically support enabled/disabling
    BasePreference(
        title = { Text("A custom preference") },
        subtitle = { Text("Showing a button") },
        icon = { Icon(Icons.Default.Android, null) }
    ) {
        Button(onClick = {
            // ...
        }) {
            Icon(Icons.Default.Android, null)
        }
    }
    
    // Custom 2 - completely free content => this will also work correctly even if used in sub preferences and it will automatically support enabled/disabling
    // but it allows you to wrap ANY composable inside it
    BasePreferenceContainer(
        modifier = Modifier.padding(16.dp),
        preferenceStyle = PreferenceStyleDefaults.item()
    ) { modifier ->
        Button(
            onClick = {
                // ...
        }) {
            Text("Button")
        }
    }
}
```

## :dna: Demo

{% include 'github_demo.md' %}

## :material-view-module: Modules and Extensions

??? info-primary "Info Preference"

    | Preview | Module |
    | :- | :- |
    | ![Preview]({{ page.meta.previews }}/info1.jpg "Preview") | `core` |

    ```kotlin title="PreferenceInfo.kt"
    --8<--
    https://raw.githubusercontent.com/MFlisar/ComposePreferences/880e28fdb71bb0c56840758ca79802e96e2a7e5b/library/core/src/main/java/com/michaelflisar/composepreferences/core/PreferenceInfo.kt:33:45
    --8<--
    ```

??? info-primary "Divider Preference"

    | Preview | Module |
    | :- | :- |
    | ![Preview]({{ page.meta.previews }}/divider1.jpg "Preview") | `core` |

    ```kotlin title="PreferenceDivider.kt"
    --8<--
    https://raw.githubusercontent.com/MFlisar/ComposePreferences/880e28fdb71bb0c56840758ca79802e96e2a7e5b/library/core/src/main/java/com/michaelflisar/composepreferences/core/PreferenceDivider.kt:27:32
    --8<--
    ```

??? info-primary "Section Header Preference"

    | Preview | Module |
    | :- | :- |
    | ![Preview]({{ page.meta.previews }}/header1.jpg "Preview") | `core` |

    ```kotlin title="PreferenceSectionHeader.kt"
    --8<--
    https://raw.githubusercontent.com/MFlisar/ComposePreferences/880e28fdb71bb0c56840758ca79802e96e2a7e5b/library/core/src/main/java/com/michaelflisar/composepreferences/core/PreferenceSectionHeader.kt:30:39
    --8<--
    ```

??? info-primary "Bool Preference"

    | Preview | | Module |
    | :- | :- | :- |
    | ![Preview]({{ page.meta.previews }}/bool1.jpg "Preview") | ![Preview]({{ page.meta.previews }}/bool2.jpg "Preview") | `bool` |

    ```kotlin title="PreferenceBool.kt"
    --8<--
    https://raw.githubusercontent.com/MFlisar/ComposePreferences/880e28fdb71bb0c56840758ca79802e96e2a7e5b/library/modules/screen/bool/src/main/java/com/michaelflisar/composepreferences/screen/bool/PreferenceBool.kt:76:88
    --8<--
    ```

??? info-primary "Button Preference"

    | Preview | Module |
    | :- | :- |
    | ![Preview]({{ page.meta.previews }}/button1.jpg "Preview") | `button` |

    ```kotlin title="PreferenceButton.kt"
    --8<--
    https://raw.githubusercontent.com/MFlisar/ComposePreferences/880e28fdb71bb0c56840758ca79802e96e2a7e5b/library/modules/screen/button/src/main/java/com/michaelflisar/composepreferences/screen/button/PreferenceButton.kt:28:38
    --8<--
    ``` 

??? info-primary "Color Preference"

    | Preview | | Module |
    | :- | :- | :- |
    | ![Preview]({{ page.meta.previews }}/color1.jpg "Preview") | ![Preview]({{ page.meta.previews }}/color2.jpg "Preview") | `color` |

    ```kotlin title="PreferenceColor.kt"
    --8<--
    https://raw.githubusercontent.com/MFlisar/ComposePreferences/880e28fdb71bb0c56840758ca79802e96e2a7e5b/library/modules/screen/color/src/main/java/com/michaelflisar/composepreferences/screen/color/PreferenceColor.kt:88:100
    --8<--
    ```   

??? info-primary "Date Preference"

    | Preview | Module |
    | :- | :- |
    | ![Preview]({{ page.meta.previews }}/date1.jpg "Preview") | `date` |

    ```kotlin title="PreferenceDate.kt"
    --8<--
    https://raw.githubusercontent.com/MFlisar/ComposePreferences/880e28fdb71bb0c56840758ca79802e96e2a7e5b/library/modules/screen/date/src/main/java/com/michaelflisar/composepreferences/screen/date/PreferenceDate.kt:85:100
    --8<--
    ``` 
 
??? info-primary "Input Preference"

    | Preview | | Module |
    | :- | :- | :- |
    | ![Preview]({{ page.meta.previews }}/input-text1.jpg "Preview") | | `input` |
    | ![Preview]({{ page.meta.previews }}/input-number1.jpg "Preview") | ![Preview]({{ page.meta.previews }}/input-number2.jpg "Preview") | `input` |

    ```kotlin title="PreferenceInputText.kt"
    --8<--
    https://raw.githubusercontent.com/MFlisar/ComposePreferences/880e28fdb71bb0c56840758ca79802e96e2a7e5b/library/modules/screen/input/src/main/java/com/michaelflisar/composepreferences/screen/input/PreferenceInputText.kt:67:78
    --8<--
    ``` 

    ```kotlin title="PreferenceInputNumber.kt"
    --8<--
    https://raw.githubusercontent.com/MFlisar/ComposePreferences/880e28fdb71bb0c56840758ca79802e96e2a7e5b/library/modules/screen/input/src/main/java/com/michaelflisar/composepreferences/screen/input/PreferenceInputNumber.kt:70:81
    --8<--
    ``` 

??? info-primary "Input List"

    | Preview | | Module |
    | :- | :- | :- |
    | ![Preview]({{ page.meta.previews }}/list1.jpg "Preview") | ![Preview]({{ page.meta.previews }}/list2.jpg "Preview") | `list` |
    | ![Preview]({{ page.meta.previews }}/list-multi1.jpg "Preview") | | `list` |

    This preference does offer 2 different options, one that allows you to only select a single item and one that allows to select mutliple items.

    ```kotlin title="PreferenceList.kt"
    --8<--
    https://raw.githubusercontent.com/MFlisar/ComposePreferences/880e28fdb71bb0c56840758ca79802e96e2a7e5b/library/modules/screen/list/src/main/java/com/michaelflisar/composepreferences/screen/list/PreferenceList.kt:99:114
    --8<--
    ``` 

    ```kotlin title="PreferenceListMulti.kt"
    --8<--
    https://raw.githubusercontent.com/MFlisar/ComposePreferences/880e28fdb71bb0c56840758ca79802e96e2a7e5b/library/modules/screen/list/src/main/java/com/michaelflisar/composepreferences/screen/list/PreferenceListMulti.kt:85:104
    --8<--
    ``` 

??? info-primary "Number Preference"

    | Preview | Module |
    | :- | :- |
    | ![Preview]({{ page.meta.previews }}/number1.jpg "Preview") | `number` |

    ```kotlin title="PreferenceNumber.kt"
    --8<--
    https://raw.githubusercontent.com/MFlisar/ComposePreferences/880e28fdb71bb0c56840758ca79802e96e2a7e5b/library/modules/screen/number/src/main/java/com/michaelflisar/composepreferences/screen/number/PreferenceNumber.kt:95:111
    --8<--
    ``` 

??? info-primary "Time Preference"

    | Preview | Module |
    | :- | :- | 
    | ![Preview]({{ page.meta.previews }}/time1.jpg "Preview") | `time` |

    ```kotlin title="PreferenceTime.kt"
    --8<--
    https://raw.githubusercontent.com/MFlisar/ComposePreferences/880e28fdb71bb0c56840758ca79802e96e2a7e5b/library/modules/screen/time/src/main/java/com/michaelflisar/composepreferences/screen/time/PreferenceTime.kt:83:96
    --8<--
    ``` 
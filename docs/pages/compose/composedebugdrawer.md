---
icon: simple/jetpackcompose
library: ComposeDebugDrawer
demo_link: https://github.com/MFlisar/ComposeDebugDrawer/blob/master/demo/src/main/java/com/michaelflisar/composedebugdrawer/demo
screenshots: https://raw.githubusercontent.com/MFlisar/ComposeDebugDrawer/master/screenshots
modules:
  - core: 
    - core
  - info: 
    - infos-build
    - infos-device
  - plugin: 
    - plugin-lumberjack
    - plugin-kotpreferences
---

{% include 'badges_header.md' %}

<i>{{ projects[page.meta.library]['info'] }}</i>

## :camera: Screenshots

| Demos | | | |
|-|-|-|-|
| ![Demo]({{ page.meta.screenshots }}/demo1.jpg "Demo") | ![Demo]({{ page.meta.screenshots }}/demo2.jpg "Demo") | ![Demo]({{ page.meta.screenshots }}/demo3.jpg "Demo") | ![Demo]({{ page.meta.screenshots }}/demo4.jpg "Demo") |
| ![Demo]({{ page.meta.screenshots }}/demo5.jpg "Demo") | ![Demo]({{ page.meta.screenshots }}/demo6.jpg "Demo") | ![Demo]({{ page.meta.screenshots }}/demo7.jpg "Demo") |  |
| ![Demo]({{ page.meta.screenshots }}/demo-theme-1.jpg "Demo") | ![Demo]({{ page.meta.screenshots }}/demo-theme-2.jpg "Demo") | ![Demo]({{ page.meta.screenshots }}/demo-theme-3.jpg "Demo") | |

## :material-check-all: Features

* easily extendible
* one line integration
* can be easily enabled/diabled in debug/release builds or based on a user setting
* predefined optional modules

**All features are splitted into separate modules, just include the modules you want to use!**

## :link: Dependencies

**Compose**

| Dependency | Version | Infos |
|:-|-:|:-:|
| [Compose BOM](https://developer.android.com/jetpack/compose/bom/bom){target=_blank} | `2023.10.01` | [Mapping](https://developer.android.com/jetpack/compose/bom/bom-mapping){target=_blank} |
| Material3 | `1.1.2` | |

**Library**

| Module | Dependency | Version |
|:-|:-|-:|
| `core` | - |  |
| **Info Modules** {: colspan=3 style="background-color:var(--md-primary-fg-color--light);"} | &#8288 {: style="padding:0"} | &#8288 {: style="padding:0"} |
| `infos-build` | - |  |
| `infos-device` | - |  |
| **Plugins** {: colspan=3 style="background-color:var(--md-primary-fg-color--light);"} | &#8288 {: style="padding:0"} | &#8288 {: style="padding:0"} |
| `plugin-lumberjack` | [Lumberjack](https://github.com/MFlisar/Lumberjack) | 6.0.1 |
| `plugin-kotpreferences` | [KotPreferences](https://github.com/MFlisar/KotPreferences) | 0.3 |

## :simple-gradle: Setup Gradle

{% include 'jitpack_setup.md' %}

## :keyboard: Usage

It works as simple as following:

???+ code "DebugDrawer"

    ```kotlin
    // wrap your app content inside the drawer like following
    val drawerState = rememberDebugDrawerState()
    ComposeAppTheme  {
        DebugDrawer(
            enabled = BuildConfig.DEBUG, // if disabled the drawer will not be created at all, in this case inside a release build...
            drawerState = drawerState,
            drawerContent = {
                // drawer content
            },
            content = {
                // your wrapped app content
            }
        )
    }
    ```

???+ code "Example Drawer Content"

    ```kotlin
    @Composable
    private fun Drawer(drawerState: DebugDrawerState) {
        DebugDrawerBuildInfos(drawerState)
        DebugDrawerActions(drawerState)
        DebugDrawerDeviceInfos(drawerState)
        
        // lumberjack module for logs
        DebugDrawerLumberjack(
            drawerState = drawerState,
            setup = DemoLogging.fileLoggingSetup,
            mailReceiver = "feedback@gmail.com"
        )
        
        // kotpreferences module for delegate based preferences (another library of mine)
        DebugDrawerRegion(
            icon = Icons.Default.ColorLens,
            label = "Demo Preferences",
            drawerState = drawerState
        ) {
            DebugDrawerDivider(info = "Boolean")
            DebugDrawerSettingCheckbox(setting = DemoPrefs.devBoolean1)
            DebugDrawerSettingCheckbox(setting = DemoPrefs.devBoolean2)
            DebugDrawerDivider(info = "Enum")
            DebugDrawerSettingDropdown(setting = DemoPrefs.devStyle,items = DemoPrefs.UIStyle.values())
        }
        
        // manual checkboxes, dropdowns, infos
        DebugDrawerRegion(
            icon = Icons.Default.Info,
            label = "Manual",
            drawerState = drawerState
        ) {
            // Checkbox
            var test1 by remember { mutableStateOf(false) }
            DebugDrawerCheckbox(
                label = "Checkbox",
                description = "Some debug flag",
                checked = test1
            ) {
                test1 = it
            }
            
            // Button
            DebugDrawerButton(
                icon = Icons.Default.BugReport, 
                label = "Button (Filled)"
            ) {
                // on click
            }
            
            // Dropdown
            val items = listOf("Entry 1", "Entry 2", "Entry 3")
            var selected by remember { mutableStateOf(items[0]) }
            DebugDrawerDropdown(
                modifier = modifier,
                label = "Items",
                selected = selected,
                items = items
            ) {
                selected = it
            }
            
            // Sectioned Button
            val items2 = listOf("L1", "L2", "L3")
            val level = remember { mutableStateOf(items2[0]) }
            DebugDrawerSegmentedButtons(
                selected = level, 
                items = items2
            )

            // Info
            DebugDrawerInfo(title = "Custom Info", info = "Value of custom info...")
        }
    }
    ```

## :dna: Demo

{% include 'github_demo.md' %}

## :material-view-module: Modules and Extensions

??? info-primary "Module Build Infos"

    This simple module allows you to add a *build info* to the debug drawer.

    ```kotlin
    DebugDrawerBuildInfos(drawerState)
    ```

??? info-primary "Module Device Infos"

    This simple module allows you to add a *device info* to the debug drawer.

    ```kotlin
    DebugDrawerDeviceInfos(drawerState)
    ```

??? info-primary "Extension Lumberjack"

    This simple module allows you to add a region for my *lumberjack* logging library.

??? info-primary "Extension KotPreferences"

    This simple module allows you to use my elegate based preference library *KotPreferences* inside the debug drawer.
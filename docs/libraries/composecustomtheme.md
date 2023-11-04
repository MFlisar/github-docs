---
icon: simple/jetpackcompose
library: ComposeCustomTheme
demo_link: https://github.com/MFlisar/ComposeCustomTheme/blob/master/demo/src/main/java/com/michaelflisar/composecustomtheme/demo
screenshots: https://raw.githubusercontent.com/MFlisar/ComposeCustomTheme/master/screenshots
modules:
  - core: 
    - core
  - extension:
    - defaultthemes
---

{% include 'badges_header.md' %}

<i>This is a **full compose theme engine** that handles applying a theme as well as updating the system ui elements. Extendible and allows to simply apply user selected themes inside your app.</i>

## :camera: Screenshots

| Demo |
|-|
| ![Log]({{ page.meta.screenshots }}/demo.gif) |

## :material-check-all: Features

* allows to define custom user themes and applies them automatically
* ability to retrieve all registered themes
* supports system ui theming (status bar + navigation bar)
* build on top of `MaterialTheme`
* comes with optional *build-in themes*

**All features are splitted into separate modules, just include the modules you want to use!**

## :link: Dependencies

| Dependency | Version | Infos |
|:-|-:|:-:|
| [Compose BOM](https://developer.android.com/jetpack/compose/bom/bom){target=_blank} | `2023.10.01` | [Mapping](https://developer.android.com/jetpack/compose/bom/bom-mapping){target=_blank} |
| Material3 | `1.1.2` | |

## :simple-gradle: Setup Gradle

{% include 'jitpack_setup.md' %}

## :material-code-tags: Setup Library

```kotlin
class App : Application() {

    override fun onCreate() {

        // register all available themes or register your custom themes
        ComposeTheme.register(
            *ComposeThemeDefaults
                .getDefaultThemes()
                .toTypedArray()
        )
    }

}
```

## :keyboard: Usage

```kotlin
// simply wrap your composable content inside ComposeTheme as if you would use MaterialTheme directly
val baseTheme = remember { mutableStateOf(ComposeTheme.BaseTheme.System) }
val dynamic = remember { mutableStateOf(false) }
val theme = remember { mutableStateOf("green") } // the key of an registered theme
val state = ComposeTheme.State(baseTheme, dynamic, theme)
ComposeTheme(state = state) {
    // content
}
```

## :dna: Demo

{% include 'github_demo.md' %}

## :material-view-module: Modules and Extensions

There only exists on very small extension for this library.

### Extension DefaultThemes

This extension adds a collection of default themes that you can use if needed.

```kotlin
// returns a list of all existing default themes
val themes = ComposeThemeDefaults.getDefaultThemes()
```
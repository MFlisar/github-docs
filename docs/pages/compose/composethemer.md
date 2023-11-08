---
icon: simple/jetpackcompose
library: ComposeThemer
demo_link: https://github.com/MFlisar/ComposeThemer/blob/master/demo/src/main/java/com/michaelflisar/Composethemer/demo
screenshots: https://raw.githubusercontent.com/MFlisar/ComposeThemer/master/screenshots
modules:
  - core: 
    - core
  - extension:
    - themes
---

{% include 'badges_header.md' %}

<i>{{ projects[page.meta.library]['info'] }}</i>

## :camera: Screenshots

| Demo |
|-|
| ![Log]({{ page.meta.screenshots }}/demo.gif) |

## :material-check-all: Features

* allows to define custom user themes and applies them automatically
* ability to retrieve all registered themes
* supports system ui theming (status bar + navigation bar)
* build on top of `MaterialTheme`
* comes with optional *55 build-in themes*

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
            *ComposeThemes
                .getAll()
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

??? info-primary "Extension Themes"

    This extension adds a collection of default themes that you can use if needed.

    ```kotlin
    // returns a list of all existing default themes
    val themes = ComposeTheme.getRegisteredThemes()

    // or get the default themes one by one (all named like Theme*)
    val theme = ThemeAmberBlue.get()
    // ... there are 56 predefined themes availabe ...
    ```

## :material-professional-hexagon: Advanced Usage

??? info-primary "Custom Statusbar / Navigationbar Colors"

    The default themes do use functions that allow you to define some custom statusbar / navigation settings if desired. Supported colors are `default`, `primary` and `surface` (those colors derive their color from the theme itself) or `custom` for fully user defined colors.

    ```kotlin
    // get all themes with custom statusbar / navigation bar
    ComposeTheme.getRegisteredThemes(
        statusBarColor = ComposeTheme.SystemUIColor.Surface,
        navigationBarColor = ComposeTheme.SystemUIColor.Surface
    )

    // or get a single predefined theme with custom statusbar / navigation bar
    val theme = ThemeAmberBlue.get(
        statusBarColor = ComposeTheme.SystemUIColor.Surface,
        navigationBarColor = ComposeTheme.SystemUIColor.Surface
    )
    ```

## :material-handshake: Credits

This library contains 54 predefined color schemes inside the `themes` module. Those are all directly copied from [FlexColorScheme](https://rydmike.com/flexcolorscheme/themesplayground-latest/){target=_blank} - a very useful homepage that allows you to **create your own themes** and also contains 54 predefined themes already. With the permission of [Rydmike](https://github.com/rydmike){target=_blank} I just copied every single predefined theme from his homepage and added it to this library.
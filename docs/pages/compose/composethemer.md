---
icon: simple/jetpackcompose
library: ComposeThemer
demo_link: https://github.com/MFlisar/ComposeThemer/blob/master/demo/src/main/java/com/michaelflisar/Composethemer/demo
screenshots: https://raw.githubusercontent.com/MFlisar/ComposeThemer/master/screenshots
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
* offers some edgeToEdge helper functions

**All features are splitted into separate modules, just include the modules you want to use!**

## :link: Dependencies

| Dependency | Version | Infos |
|:-|-:|:-:|
| [Compose BOM](https://developer.android.com/jetpack/compose/bom/bom){target=_blank} | `{{ projects[page.meta.library]['dependencies']['bom'] }}` | [Mapping](https://developer.android.com/jetpack/compose/bom/bom-mapping){target=_blank} |
| Material3 | `{{ projects[page.meta.library]['dependencies']['material3'] }}` | |

## :simple-gradle: Setup Gradle

{% include 'jitpack_setup.md' %}

## :material-code-tags: Setup Library

```kotlin
class App : Application() {

    override fun onCreate() {

        // register all available themes or register your custom themes
        ComposeTheme.register(*ComposeThemes.ALL.toTypedArray())

        // OR register some of them (or even your own ones)
        ComposeTheme.register(
            ThemeAmberBlue.get(),
            ThemeAquaBlue.get(),
            ThemeBahamaAndTrinidad.get(),
            // ...
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

    // update edgeToEdge to the correct styles with the provided helper functions
    // e.g. like following if the layout has a primary toolbar at top and nothing at bottom
    // TIPP:
    // this functions has an overload that works with SystemBarStyle instead if you want to use that directly
    ComposeTheme.enableEdgeToEdge(
        activity = this,
        statusBarColor = MaterialTheme.colorScheme.primary,
        navigationBarColor = if (landscape) {
            SystemBarStyle.defaultScrim(resources)
        } else MaterialTheme.colorScheme.background,
        isNavigationBarContrastEnforced = landscape
    )

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

??? info-primary "SystemBarStyle extensions"

    I added some extensions to `SystemBarStyle.Companion`.

    ```kotlin
   // following gives you a fully transparent SystemBarStyle or the default SystemBarStyle for the statusbar or navigationbar
   SystemBarStyle.transparent()
   SystemBarStyle.statusBar()
   SystemBarStyle.navigationBar()
   // this gives you the default scrim color that is normally defined privately aand can't be easily accessed
   SystemBarStyle.defaultScrim(resource)
    ```

??? info-primary "Disable the edgeToEdge mode"

    If desired, you can still use this library without using the edgeToEdge feature.

    ```kotlin
    ComposeTheme(state = state, edgeToEdge = false) {
        // content
    }
    ```

## :material-handshake: Credits

This library contains 54 predefined color schemes inside the `themes` module. Those are all directly copied from [FlexColorScheme](https://rydmike.com/flexcolorscheme/themesplayground-latest/){target=_blank} - a very useful homepage that allows you to **create your own themes** and also contains 54 predefined themes already. With the permission of [Rydmike](https://github.com/rydmike){target=_blank} I just copied every single predefined theme from his homepage and added it to this library.
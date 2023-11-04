---
icon: simple/jetpackcompose
library: ComposeChangelog
demo_link: https://github.com/MFlisar/ComposeChangelog/blob/master/demo/src/main/java/com/michaelflisar/composechangelog/demo
screenshots: https://raw.githubusercontent.com/MFlisar/ComposeChangelog/master/screenshots
modules:
  - core: 
    - core
  - statesaver:
    - statesaver-preferences
    - statesaver-kotpreferences
---

{% include 'badges_header.md' %}

<i>This library offers you a a **changelog dialog** for compose including the ability to show new logs on app start only as well as filtering and customisation.</i>

## :camera: Screenshots

| Dialogs |
|-|
| ![Log]({{ page.meta.screenshots }}/overview.jpg) |

## :material-check-all: Features

* filtering
    * useful to filter out uninteresting old changelog entries on app start
    * useful for filtering changelog based on build flavour
* also supports automatic handling of showing changelogs on app start (uses preference to save last seen changelog version and handles everything for you automatically to only show **new changelogs** and only show those once)
* customise look
    * you can provide custom composables for every item type if desired
    * you can provide custom version name formatter
    * you can provide a custom sorter
* supports raw and xml resources, default resource name is `changelog.xml` in raw folder
* supports summaries with a "show more" button

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
| **Extensions** {: colspan=3 style="background-color:var(--md-primary-fg-color--light);"} | &#8288 {: style="padding:0"} | &#8288 {: style="padding:0"} |
| `statesaver-preferences` | - |  |
| `statesaver-kotpreferences` | [KotPreferences](https://github.com/MFlisar/KotPreferences) | 0.3 |

## :simple-gradle: Setup Gradle

{% include 'jitpack_setup.md' %}

## :keyboard: Usage

It works as simple as following:

```kotlin
// 1) we need a state saver to persist the version for which the changelog was last shown
// use either of the following 2 or implement the corresponding interface yourself
val changelogStateSaver = ChangelogStateSaverPreferences(LocalContext.current)
val changelogStateSaverKotPrefs = ChangelogStateSaverKotPreferences(AppPrefs.lastShownVersionForChangelog)

// 2) optional - here you can apply some customisations like changelog resource id, localized texts, styles, filter, sorter, renderer...
val setup = ChangelogDefaults.setup()

// 3) show the changelog for the app start - this will only show the changelogs that the user did not see yet
Changelog.CheckedShowChangelog(changelogStateSaver, setup)
```

Alternatively simple show the changelog based on an event like a button click whenever you want:

```kotlin

// 1) we need a state to decide if we need to show the changelog or not
var showChangelog by remember { mutableStateOf(false) }

// 2) we need some event source
Button(onClick = { showChangelog = true }) {
    Text("Show Changelog")
}

// 3) we show the changelog if necessary
if (showChangelog) {
    // optional setup...
    val setup = ChangelogDefaults.setup()
    Changelog.ShowChangelogDialog(setup) {
        // this is the dismiss callback, here we must reset the showChangelog flag
        showChangelog = false
    }
}

```

## :dna: Demo

{% include 'github_demo.md' %}
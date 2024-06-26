---
icon: simple/jetpackcompose
library: ComposeChangelog
demo_link: https://github.com/MFlisar/ComposeChangelog/blob/master/demo/src/main/java/com/michaelflisar/composechangelog/demo
screenshots: https://raw.githubusercontent.com/MFlisar/ComposeChangelog/master/screenshots
---

{% include 'badges_header.md' %}

<i>{{ projects[page.meta.library]['info'] }}</i>

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
* optional provides a `gradle plugin` that allows you to convert version names automatically to version numbers

**All features are splitted into separate modules, just include the modules you want to use!**

## :link: Dependencies

**Compose**

BOM: 

| Dependency | Version | Infos |
|:-|-:|:-:|
| [Compose BOM](https://developer.android.com/jetpack/compose/bom/bom){target=_blank} | `{{ projects[page.meta.library]['dependencies']['bom'] }}` | [Mapping](https://developer.android.com/jetpack/compose/bom/bom-mapping){target=_blank} |
| Material3 | `{{ projects[page.meta.library]['dependencies']['material3'] }}` | |

**Library**

| Module | Dependency | Version |
|:-|:-|-:|
| `core` | - |  |
| **Extensions** {: colspan=3 style="background-color:var(--md-primary-fg-color--light);"} | &#8288 {: style="padding:0"} | &#8288 {: style="padding:0"} |
| `statesaver-preferences` | - |  |
| `statesaver-kotpreferences` | [KotPreferences](https://github.com/MFlisar/KotPreferences) | `{{ projects[page.meta.library]['dependencies']['kotpreferences'] }}` |
| **Plugins** {: colspan=3 style="background-color:var(--md-primary-fg-color--light);"} | &#8288 {: style="padding:0"} | &#8288 {: style="padding:0"} |
| `gradle-plugin` | - |  |

## :simple-gradle: Setup Gradle

{% include 'jitpack_setup.md' %}

## :keyboard: Usage

It works as simple as following:

???+ code "Define your changelog as raw xml file"

    ```xml title="raw/changelog.xml"
    <changelog>
    
        <!-- with version names -->
        <release versionName="1.2.1" date="2024-04-20">
            <new type="summary">-new gradle plugin added - you don't need to convert version names to version codes anymore!</new>
        </release>
        <release versionName="1.2.0" date="2023-03-04">
            <info>Some info 1 - apostrophe test: it's weird, but apostrophes do not work in precompiled xml files placed in xml resources!</info>
            <new type="summary">Some improvement 1</new>
            <bugfix>Some bugfix 1</bugfix>
            <info>Some info 2</info>
            <new type="summary">Some improvement 2</new>
            <bugfix>Some bugfix 2</bugfix>
            <info>Some info 3</info>
            <new>Some improvement 3</new>
            <bugfix>Some bugfix 3</bugfix>
            <customTag>My custom tag text...</customTag>
        </release>

        <!-- with version codes --> 
        <release versionCode="118" date="2023-03-04">
            <new type="summary">This version has a summary item only - no show more button will be shown even if show more buttons are enabled</new>
        </release>
        <release versionCode="115" date="2023-03-04">
            <info>Some info</info>
            <new type="summary">Some improvement</new>
            <bugfix>Some bugfix</bugfix>
        </release>
        <release versionCode="110" versionName="Version 1.10" date="2023-03-03" filter="dogs">
            <info>Some dogs info - filter only set in release tag</info>
            <new type="summary">Some dogs improvement - filter only set in release tag</new>
            <bugfix>Some dogs bugfix - filter only set in release tag</bugfix>
        </release>
        <release versionCode="105" versionName="Version 1.05" date="2023-03-02" filter="cats">
            <info type="summary">single summary of version 1.05</info>
            <info>Some cats info - filter only set in release tag</info>
            <new>Some cats improvement - filter only set in release tag</new>
            <bugfix>Some cats bugfix - filter only set in release tag</bugfix>
        </release>
        <release versionCode="100" versionName="First release" date="2023-03-01">
            <info filter="cats" type="summary">single cats summary of version 1.00</info>
            <info filter="dogs" type="summary">single dogs summary of version 1.00</info>
            <info filter="cats">New cats added - this info has filter text 'cats'</info>
            <info filter="dogs">New dogs added - this info has filter text 'dogs'</info>
            <new filter="cats">Some cats improvement - this info has filter text 'cats'</new>
            <new filter="dogs">Some dogs improvement - this info has filter text 'dogs'</new>
            <bugfix filter="cats">Some cats bugfix - this info has filter text 'cats'</bugfix>
            <bugfix filter="dogs">Some dogs bugfix - this info has filter text 'dogs'</bugfix>
        </release>
        <release versionCode="90" versionName="First beta" date="2023-02-01">
            <info>this release does not have any summary item and will be shown expanded even if summary is enabled - this behaviour can be adjusted by the second parameter in the builder with which you enable summaries</info>
        </release>
    </changelog>
    ```

???+ code "Show the interesting parts of the changelog on app start"

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

???+ code "Show the full changelog"

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

## :material-professional-hexagon: Advanced Usage

If you want to you can simply use the new `gradle-plugin` module. Following shows it's usage and advantages:

???+ code "Using the gradle plugin"

    - Project `build.gradle.kts` file:

    ```kotlin
    buildscript {
        repositories {
            // repositories
            // ...
        }
        dependencies {
            // your classpaths...
            // ...

            // classpath for the gradle plugin of comose changelog
            classpath("com.github.MFlisar.ComposeChangelog:gradle-plugin:<VERSION>")
        }
    }
    ```

    After adding above you can simple apply the plugin inside your apps `build.gradle.kts` file like following and use it like following:

    ```kotlin
    import com.michaelflisar.composechangelog.gradle.plugin.Changelog
    import com.michaelflisar.composechangelog.DefaultVersionFormatter

    plugins {
        // other plugins
        id("com.android.application")
        id("kotlin-android")
        id("kotlin-kapt")

        // plugin of compose changelog
        id("compose-changelog")
    }

    // define your app version code based on your format, here we use the Major.Minor.Patch format
    val version = "0.3.0"
    val code = Changelog.buildVersionCode(version, DefaultVersionFormatter(DefaultVersionFormatter.Format.MajorMinorPatch))

    // make sure to use the SAME formatter inside your code whenever you want to show a changelog - Major.Minor.Patch format is the default one though

    android {

        // ...

        defaultConfig {
            // use the version and code variables from above
            versionCode = code
            versionName = version
        }

         // ...
    }
    ```

    You now only must change `val version = "0.3.0"` to whatever new version you want and the code will be calculated by itself.

    Additionally you can easily use the `versionName` tag inside your `changelog.xml` file, the formatter will correctly parse it to it's number for you.

!!! info-primary "Information"

    Always make sure to use the same formatter in your `build.gradle.kts` as well as inside your code.
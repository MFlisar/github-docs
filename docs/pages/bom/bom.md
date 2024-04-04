---
icon: material/github
library: BOM
demo_link:
screenshots:
module:
---

{% include 'badges_header.md' %}

<i>{{ projects[page.meta.library]['info'] }}</i>

## :material-check-all: Features

* simple usage of my libraries and compatible versions without any work on your side
* naming is based on the compose bom naming, this means, the name will match the used compose bom file inside all libraries

## :link: Dependencies

None, this is just a BOM file.

## :simple-gradle: Setup Gradle

This library is distributed via [JitPack.io](https://jitpack.io/){target=_blank}.

??? code "1/3: Add jitpack to your project's `build.gradle`"

    ```kotlin
    repositories {
        maven { url "https://jitpack.io" }
    }
    ```

???+ code "2/3: Add dependencies to your module's `build.gradle`"

    ```kotlin

    // use the latest version of the library
    val {{ page.meta.library | lower }} = "<LATEST-VERSION>" 

    // add the bom dependency
    implementation(platform("com.github.MFlisar:{{ page.meta.library }}:${{ page.meta.library | lower }}"))
    ```

???+ code "3/3: Add dependencies to your module's `build.gradle`"

    ```kotlin

    // ------------------------------------------
    // add desired libraries WITHOUT versions now
    // ------------------------------------------
    {{ "" }}
    {%- for p in projects -%}
    {%- if p == page.meta.library -%}
    {% elif projects[p]['modules'] == null %}
    // {{ p }}
    implementation("com.github.MFlisar:{{ p }}")
    {% elif projects[p]['modules'] != null %}
    // {{ p }}
    {%- for group in projects[p]['modules'] %}
    {%- for module in group[group | first ] %}
    implementation("com.github.MFlisar.{{ p }}:{{ module }}")
    {%- endfor %}
    {%- endfor %}
    {% endif %}
    {%- endfor -%}

    ```
This library is distributed via [JitPack.io](https://jitpack.io/){target=_blank}.

??? code "1/2: Add jitpack to your project's `build.gradle`"

    ```kotlin
    repositories {
        maven { url "https://jitpack.io" }
    }
    ```

???+ code "2/2: Add dependencies to your module's `build.gradle`"

    ```kotlin

    // use the latest version of the library
    val {{ page.meta.library | lower }} = "<LATEST-VERSION>" 

    {% if projects[page.meta.library]['modules'] == null -%}
    // add library dependency
    implementation("com.github.MFlisar:{{ page.meta.library }}:${{ page.meta.library | lower }}")
    {% else -%}
    // include necessary modules
    {% for group in projects[page.meta.library]['modules'] %}
    // {{ group | first }} module{% if group[sub] | length > 1 %}s{%endif%}
    {%- for module in group[group | first ] %}
    implementation("com.github.MFlisar.{{ page.meta.library }}:{{ module }}:${{ page.meta.library | lower }}")
    {%- endfor %}
    {% endfor %}
    {%- endif %}
    
    ```

!!! tip "BOM"

    Consider using my [BOM Library](../bom/bom.md) to manage my libraries versions, especially if you use more than one of my libraries.
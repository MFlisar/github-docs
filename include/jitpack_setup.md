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

    {% if page.meta.modules == null -%}
    // add library dependency
    implementation("com.github.MFlisar:{{ page.meta.library }}:${{ page.meta.library | lower }}")
    {% else -%}
    // include necessary modules
    {% for module in page.meta.modules %}
    {%- for sub in module %}
    // {{ module | first }} module{% if module[sub] | length > 1 %}s{%endif%}
    {%- for e in module[sub] %}
    implementation("com.github.MFlisar.{{ page.meta.library }}:{{ e }}:${{ page.meta.library | lower }}")
    {%- endfor %}
    {% endfor %}
    {%- endfor %}
    {%- endif %}

    ```
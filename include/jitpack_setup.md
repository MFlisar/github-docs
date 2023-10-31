Jitpack Setup:
{{ page.title }}
{{ page.meta.libray }}

### TEST
```kotlin

// base path
{{ page.meta.module_base_path }}

{% for group in page.meta.modules %}
// Group: {{ group[0] }}
{% for module in group[1] %}
Module: {{ module[0] }}
{% endfor %}

{% endfor %}

```

### TEST ENDE

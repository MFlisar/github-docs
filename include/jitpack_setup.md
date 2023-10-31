Jitpack Setup:
{{ page.title }}
{{ page.meta.libray }}

### TEST
```kotlin

// base path
{{ page.meta.module_base_path }}

{% for group in page.meta.modules %}

// Group: {{ group }}
{% for module in group %}
Module: {{ module }}
{% endfor %}

{% for key, value in group.items() %}
    {{ key|e }}
    {{ value|e }}
{% endfor %}

{% endfor %}

```

### TEST ENDE

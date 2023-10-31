Jitpack Setup:
{{ page.title }}
{{ page.meta.libray }}

### TEST
```kotlin

// base path
{{ page.meta.module_base_path }}

{% for key, value in page.meta.modules %}
// Group1: {{ key }} - {{ value }}
{% endfor %}

{% for group in page.meta %}
// Group2: {{ group }}
{% endfor %}

```

### TEST ENDE

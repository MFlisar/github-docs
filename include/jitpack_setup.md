Jitpack Setup:
{{ page.title }}
{{ page.meta.libray }}

### TEST
```kotlin

// base path
{{ page.meta.module_base_path }}

{% for key, value in page.meta %}
// Group: {{ key }} - {{ value }}
{% endfor %}

{% for group in page.meta %}
// Group: {{ group }}
{% endfor %}

```

### TEST ENDE

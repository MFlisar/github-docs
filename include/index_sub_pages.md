<ul>
{% for n in navigation.pages %}
{% if page.url in n['url'] %}
{% if n['url'] != page.url %}
<li><a href="{{ n['url'] | replace(page.url, '') }}"> {{ n['title'] }}</a></li>
{% endif %}
{% endif %}
{% endfor %}
</ul>
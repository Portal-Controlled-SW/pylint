{% set title = "What's new in Pylint " + versiondata.version + "?" %}
{{ title }}
{{ underlines[0] * (title|length) }}
Release date: {{ versiondata.date }}

{% for section, _ in sections.items() %}
{% set underline = underlines[0] %}{% if section %}{{section}}
{{ underline * section|length }}{% set underline = underlines[1] %}

{% endif %}

{% if sections[section] %}
{% for category, val in definitions.items() if category in sections[section]%}
{{ definitions[category]['name'] }}
{{ underline * definitions[category]['name']|length }}

{% if definitions[category]['showcontent'] %}
{% for text, values in sections[section][category].items() %}
- {{ text }} ({{ values|join(', ') }})
{% endfor %}

{% else %}
- {{ sections[section][category]['']|join(', ') }}

{% endif %}
{% if sections[section][category]|length == 0 %}
No significant changes.

{% else %}
{% endif %}

{% endfor %}
{% else %}
No significant changes.


{% endif %}
{% endfor %}

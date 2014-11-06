{{ STATIC_URL }}

{% url 'schema' release_name 'release-schema' %}

<script src="{{ STATIC_URL }}docson/widget.js" data-schema={% url 'schema' release_name 'release-schema' %}></script>
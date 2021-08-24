{% assign location-type-include = include.location-type %}

{% for location in location-type-include %}

{% assign location-name = location[0] %}
{% assign location-value = location[1] %}

### {{ location-name | capitalize }}

{% for location-place in location-value %}

{% include city-location-place.md 
  place=location-place
%}

{% endfor %}
{% endfor %}

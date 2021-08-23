{% assign place = include.restaurant %}

{% assign rate-split = place.rate | at_least: 0 | at_most: 5 | round: 2 | split: "." %}
{% assign rate-integral = rate-split[0] %}
{% assign rate-fractional = rate-split[1] | append: "00" | truncate: 2, "" %}

#### {{ place.name }}

[{{ place.address }}](geo:?q={{ place.address | replace: " ", "+" | replace: ",", "" }})  
{{ rate-integral }}.{{ rate-fractional }} / 5.00

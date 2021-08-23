{% assign place = include.restaurant %}

{% assign rate-sum = 0 %}
{% for comment in place.comments %}
    {% assign fixed-rate = comment.rate | at_least: 0 | at_most: 5 %}
    {% assign rate-sum = rate-sum | plus: fixed-rate %}
{% endfor %}

{% assign rate-split = rate-sum | divided_by: place.comments.size | round: 2 | split: "." %}
{% assign rate-integral = rate-split[0] %}
{% assign rate-fractional = rate-split[1] | append: "00" | truncate: 2, "" %}

#### {{ place.name }}

[{{ place.address }}](geo:?q={{ place.address | replace: " ", "+" | replace: ",", "" }})  
Cumulative Rate: {{ rate-integral }}.{{ rate-fractional }} / 5.00

<p>
{% for comment in place.comments %}
({{ comment.rate }} / 5.00) {{comment.comment}} - {{comment.author}}<br>
{% endfor %}
</p>

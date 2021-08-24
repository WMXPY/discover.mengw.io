{% assign place = include.place %}

{% if place.comments.size > 0 %}
{% assign rate-sum = 0 %}
{% for comment in place.comments %}
    {% assign fixed-rate = comment.rate | at_least: 0 | at_most: 5 %}
    {% assign rate-sum = rate-sum | plus: fixed-rate %}
{% endfor %}

{% assign rate-split = rate-sum | divided_by: place.comments.size | round: 2 | split: "." %}
{% assign rate-integral = rate-split[0] %}
{% assign rate-fractional = rate-split[1] | append: "00" | truncate: 2, "" %}
{% else %}
{% assign rate-integral = "0" %}
{% assign rate-fractional = "00" %}
{% endif %}

#### {{ place.name }}

<div>
<i class="fa fa-map-marker fa-fw"></i> 
{% include address.html 
  address=place.address
%}
</div>
<i class="fa fa-star fa-fw"></i> {{ rate-integral }}.{{ rate-fractional }} / 5.00

{% if place.comments.size > 0 %}
<p>
<i class="fa fa-comments fa-fw"></i>
<br>
{% for comment in place.comments %}
{% assign comment-rate-split = comment.rate | at_least: 0 | at_most: 5 | round: 2 | split: "." %}
{% assign comment-rate-integral = comment-rate-split[0] %}
{% assign comment-rate-fractional = comment-rate-split[1] | append: "00" | truncate: 2, "" %}
<span>({{ comment-rate-integral }}.{{ comment-rate-fractional }} / 5.00)</span>
<span>{{ comment.comment }}</span>
<span>-</span>
<span>{{ comment.author }}</span>
<br>
{% endfor %}
</p>
{% endif %}

{% assign data = site.data[page.country][page.state][page.city] %}

{% if data.food %}
## Food

{% if data.food.chinese %}
### Chinese

{% for place in data.food.chinese %}
{% include city-food-restaurant.md 
 restaurant=place
%}
{% endfor %}

{% endif %}
{% endif %}
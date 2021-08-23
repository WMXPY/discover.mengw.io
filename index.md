---
title: Discover
layout: home
---

# Discover

This site discover nice place around the earth.

{% assign countries = site.data | sort %}
{% for country in countries %}
{% assign countryName = country[0] %}
{% unless countryName == "dictionary" %}

## {{ site.data.dictionary[countryName] }}

{% assign states = site.data[countryName] | sort %}
{% for state in states %}
{% assign stateName = state[0] %}

### {{ stateName | capitalize }}

<ul>
{% assign cities = site.data[countryName][stateName] | sort %}
{% for city in cities %}
{% assign cityName = city[0] %}
{% assign cityData = city[1] %}

<li>   
<a href="./{{countryName}}/{{stateName}}/{{cityName}}">{{cityData.city}}</a>
</li>

{% endfor %}
</ul>

{% endfor %}

{% endunless %}
{% endfor %}

## Links

-   [Barktler](https://github.com/Barktler) API Solution > [Barktler.com](//barktler.com)
-   [Brontosaurus](https://github.com/SudoDotDog/Brontosaurus) authorization solution > [Brontosaurus Land](https://brontosaurus.land)
-   SudoDotDog Package Index > [sudo.dog](https://sudo.dog)
-   BWNL Package Index > [BWNL.io](https://bwnl.io)
-   Amazing Links > [link.mengw.io](https://link.mengw.io)
-   My Work and Me > [mengw.io](https://mengw.io)

> Built with Love by [WMXPY](//github.com/WMXPY) & [PCXPY](//github.com/PCXPY)

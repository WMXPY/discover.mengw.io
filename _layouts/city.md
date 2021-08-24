{% assign data = site.data[page.country][page.state][page.city] %}

{% capture core-content %}

# {{data.city}} - {{data.state}}

{% for location-type in data.locations %}

{% assign location-type-name = location-type[0] %}
{% assign location-type-value = location-type[1] %}

## {{ location-type-name | capitalize }}

{% include city-location-type.md 
  location-type=location-type-value
%}

{% endfor %}

{% endcapture %}

<!DOCTYPE html>
<html lang="{{ page.lang | default: site.lang | default: "en" }}">
{%- include city-head.html -%}

<body>
  {%- include header.html -%}
  <main class="page-content" aria-label="Content">
    <div class="wrapper">
      {{ core-content | markdownify }}
      {{ content }}
    </div>
  </main>
  <script src="/assets/js/code-blockquote.js"></script>
  <script src="/assets/js/code-highlight.js"></script>
  <script src="https://cdnjs.cloudflare.com/ajax/libs/anchor-js/4.1.0/anchor.min.js"
    integrity="sha256-lZaRhKri35AyJSypXXs4o6OPFTbTmUoltBbDCbdzegg=" crossorigin="anonymous"></script>
  <script>
    anchors.add();
  </script>
  {%- include city-footer.html -%}
</body>

</html>
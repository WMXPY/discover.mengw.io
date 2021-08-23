{% assign data = site.data.united-states.iowa.ames %}

{% capture core-content %}
# {{data.city}} - {{data.state}}
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
  <script src="https://cdnjs.cloudflare.com/ajax/libs/anchor-js/4.1.0/anchor.min.js"
    integrity="sha256-lZaRhKri35AyJSypXXs4o6OPFTbTmUoltBbDCbdzegg=" crossorigin="anonymous"></script>
  <script>
    anchors.add();
  </script>
  {%- include city-footer.html -%}
</body>

</html>
---
layout: page
permalink: /publications/
title: publications
description: Selected. For a full list, see my <a href="https://scholar.google.com/citations?user=IiA-t5YAAAAJ&hl=en">Google Scholar</a>.
sections:
  - bibquery: "@article"
    text: "Journal Articles"
  - bibquery: "@preprint"
    text: "Preprints"
#   - bibquery: "@inproceedings"
#     text: "Conference and workshop papers"
#   - bibquery: "@misc|@phdthesis|@mastersthesis"
#     text: "Thesis"
years: [2024, 2023, 2022, 2021, 2020, 2019, 2018, 2017, 2016, 2015]
social: true
nav: true
nav_order: 2
---

<div class="publications">

{%- for section in page.sections %}
  <a id="{{section.text}}"></a>
  <h1 class="bibtitle">{{section.text}}</h1>
  {%- for y in page.years %}

    {%- comment -%}  Count bibliography in actual section and year {%- endcomment -%}
    {%- capture citecount -%}
    {%- bibliography_count -f {{site.scholar.bibliography}} -q {{section.bibquery}}[year={{y}}] -%}
    {%- endcapture -%}

    {%- comment -%} If exist bibliography in actual section and year, print {%- endcomment -%}
    {%- if citecount !="0" %}

      <!-- <h2 class="year">{{y}}</h2> -->
      {% bibliography -f {{site.scholar.bibliography}} -q {{section.bibquery}}[year={{y}}] %}

    {%- endif -%}

  {%- endfor %}

{%- endfor %}

</div>

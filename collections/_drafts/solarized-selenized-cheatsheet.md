---
title: Solarized & Selenized Colorscheme Cheatsheet
tags: colorscheme cheatsheet solarized selenized
classes: wide
bases:
  - base00
  - base01
  - base02
  - base03
  - base04
  - base05
  - base06
  - base07
  - base08
  - base09
  - base0a
  - base0b
  - base0c
  - base0d
  - base0e
  - base0f
colorscheme_pairs:
  - title: "Solarized (dark & light)"
    palettes:
      - solarized_dark
      - solarized_light
  - title: "Selenized (dark & light)"
    palettes:
      - selenized_dark
      - selenized_light
  - title: "Solarized and Selenized (dark)"
    palettes:
      - solarized_dark
      - selenized_dark
  - title: "Solarized and Selenized (light)"
    palettes:
      - solarized_light
      - selenized_light
---

<style type="text/css">
  table {
    margin: auto;
    border-collapse: collapse;
  }

  thead th.name {
    width: 12%
  }

  thead th.value {
    width: 15%;
  }

  th {
    font-weight: bold;
    background-color: #d5cdb6;
  }

  th,
  td {
    text-align: center;
    vertical-align: middle;
    border: 1px solid;
  }
  
  td > code {
    background: none;
  }
</style>

Note: Color values here are canonical in CIE L\*a\*b\* form. The included sRGB
values were computed with [`palettte`](https://docs.rs/palette/latest/palette/).

{%- for colorscheme_pair in page.colorscheme_pairs %}
## {{ colorscheme_pair.title }}

<table>
  <thead>
    <tr>
      <th rowspan="2"></th>
      <th rowspan="2">Base16</th>
    {%- for colorscheme in colorscheme_pair.palettes %}
    {%- assign palette = site.data.colorschemes[colorscheme] %}
      <th colspan="3">{{ palette.palette }}</th>
    {%- endfor %}
    </tr>
    <tr>
    {%- for colorscheme in colorscheme_pair.palettes %}
      <th class="name">name</th>
      <th class="value"><strong>L*a*b*</strong></th>
      <th class="value">sRGB</th>
    {%- endfor %}
    </tr>
  </thead>

  <tbody>
  <!-- Shades bases -->
  {%- for i in (0..7) %}
    <tr>
    {%- if forloop.first %}
      <th rowspan="8">shades</th>
    {%- endif %}
      <th>{{ page.bases[i]] }}</th>
    {%- for colorscheme in colorscheme_pair.palettes %}
    {%- assign palette = site.data.colorschemes[colorscheme] %}
    {%- assign color = palette.colors[i] %}
      <td><code>{{ color.name }}</code></td>
      <td><code>{{ color.lab.l }} {{ color.lab.a }} {{ color.lab.b }}</code></td>
      <td><code>{{ color.rgb.hex }}</code></td>
    {%- endfor %}
    </tr>
  {%- endfor %}

  <!-- Accents bases -->
  {%- for i in (8..15) %}
    <tr>
    {%- if forloop.first %}
      <th rowspan="8">accents</th>
    {%- endif %}
      <th>{{ page.bases[i]] }}</th>
    {%- for colorscheme in colorscheme_pair.palettes %}
    {%- assign palette = site.data.colorschemes[colorscheme] %}
    {%- assign color = palette.colors[i] %}
      <td><code>{{ color.name }}</code></td>
      <td><code>{{ color.lab.l }} {{ color.lab.a }} {{ color.lab.b }}</code></td>
      <td><code>{{ color.rgb.hex }}</code></td>
    {%- endfor %}
    </tr>
  {%- endfor %}
  </tbody>
</table>

{%- endfor %}
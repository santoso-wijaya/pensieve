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
---

<style type="text/css">
  <!-- TODO -->
</style>

Note: Color values here are canonical in CIE L\*a\*b\* form. The included sRGB
values were computed with [`palettte`](https://docs.rs/palette/latest/palette/).

## Solarized (dark & light)

{% assign colorschemes = "solarized_dark,solarized_light" | split:"," %}

<table>
  <tr>
    <th rowspan="2"></th>
    <th rowspan="2">Base16</th>
  {%- for colorscheme in colorschemes %}
  {%- assign palette = site.data.colorschemes[colorscheme] %}
    <th colspan="3">{{ palette.palette }}</th>
  {%- endfor %}
  </tr>
  <tr>
  {%- for colorscheme in colorschemes %}
    <th>name</th>
    <th><strong>L*a*b*</strong></th>
    <th>sRGB</th>
  {%- endfor %}
  </tr>

<!-- Shades bases -->
{%- for i in (0..7) %}
  <tr>
  {%- if forloop.first %}
    <th rowspan="8">shades</th>
  {%- endif %}
    <th>{{ page.bases[i]] }}</th>
  {%- for colorscheme in colorschemes %}
  {%- assign palette = site.data.colorschemes[colorscheme] %}
  {%- assign color = palette.colors[i] %}
    <td>{{ color.name }}</td>
    <td>{{ color.lab.l }} {{ color.lab.a }} {{ color.lab.b }}</td>
    <td>{{ color.rgb.hex }}</td>
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
  {%- for colorscheme in colorschemes %}
  {%- assign palette = site.data.colorschemes[colorscheme] %}
  {%- assign color = palette.colors[i] %}
    <td>{{ color.name }}</td>
    <td>{{ color.lab.l }} {{ color.lab.a }} {{ color.lab.b }}</td>
    <td>{{ color.rgb.hex }}</td>
  {%- endfor %}
  </tr>
{%- endfor %}
</table>

## Selenized (dark & light)

{% assign colorschemes = "selenized_dark,selenized_light" | split:"," %}

<table>
  <tr>
    <th rowspan="2"></th>
    <th rowspan="2">Base16</th>
  {%- for colorscheme in colorschemes %}
  {%- assign palette = site.data.colorschemes[colorscheme] %}
    <th colspan="3">{{ palette.palette }}</th>
  {%- endfor %}
  </tr>
  <tr>
  {%- for colorscheme in colorschemes %}
    <th>name</th>
    <th><strong>L*a*b*</strong></th>
    <th>sRGB</th>
  {%- endfor %}
  </tr>

<!-- Shades bases -->
{%- for i in (0..7) %}
  <tr>
  {%- if forloop.first %}
    <th rowspan="8">shades</th>
  {%- endif %}
    <th>{{ page.bases[i]] }}</th>
  {%- for colorscheme in colorschemes %}
  {%- assign palette = site.data.colorschemes[colorscheme] %}
  {%- assign color = palette.colors[i] %}
    <td>{{ color.name }}</td>
    <td>{{ color.lab.l }} {{ color.lab.a }} {{ color.lab.b }}</td>
    <td>{{ color.rgb.hex }}</td>
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
  {%- for colorscheme in colorschemes %}
  {%- assign palette = site.data.colorschemes[colorscheme] %}
  {%- assign color = palette.colors[i] %}
    <td>{{ color.name }}</td>
    <td>{{ color.lab.l }} {{ color.lab.a }} {{ color.lab.b }}</td>
    <td>{{ color.rgb.hex }}</td>
  {%- endfor %}
  </tr>
{%- endfor %}
</table>

## Solarized and Selenized (dark)

{% assign colorschemes = "solarized_dark,selenized_dark" | split:"," %}

<table>
  <tr>
    <th rowspan="2"></th>
    <th rowspan="2">Base16</th>
  {%- for colorscheme in colorschemes %}
  {%- assign palette = site.data.colorschemes[colorscheme] %}
    <th colspan="3">{{ palette.palette }}</th>
  {%- endfor %}
  </tr>
  <tr>
  {%- for colorscheme in colorschemes %}
    <th>name</th>
    <th><strong>L*a*b*</strong></th>
    <th>sRGB</th>
  {%- endfor %}
  </tr>

<!-- Shades bases -->
{%- for i in (0..7) %}
  <tr>
  {%- if forloop.first %}
    <th rowspan="8">shades</th>
  {%- endif %}
    <th>{{ page.bases[i]] }}</th>
  {%- for colorscheme in colorschemes %}
  {%- assign palette = site.data.colorschemes[colorscheme] %}
  {%- assign color = palette.colors[i] %}
    <td>{{ color.name }}</td>
    <td>{{ color.lab.l }} {{ color.lab.a }} {{ color.lab.b }}</td>
    <td>{{ color.rgb.hex }}</td>
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
  {%- for colorscheme in colorschemes %}
  {%- assign palette = site.data.colorschemes[colorscheme] %}
  {%- assign color = palette.colors[i] %}
    <td>{{ color.name }}</td>
    <td>{{ color.lab.l }} {{ color.lab.a }} {{ color.lab.b }}</td>
    <td>{{ color.rgb.hex }}</td>
  {%- endfor %}
  </tr>
{%- endfor %}
</table>

## Solarized and Selenized (light)

{% assign colorschemes = "solarized_light,selenized_light" | split:"," %}

<table>
  <tr>
    <th rowspan="2"></th>
    <th rowspan="2">Base16</th>
  {%- for colorscheme in colorschemes %}
  {%- assign palette = site.data.colorschemes[colorscheme] %}
    <th colspan="3">{{ palette.palette }}</th>
  {%- endfor %}
  </tr>
  <tr>
  {%- for colorscheme in colorschemes %}
    <th>name</th>
    <th><strong>L*a*b*</strong></th>
    <th>sRGB</th>
  {%- endfor %}
  </tr>

<!-- Shades bases -->
{%- for i in (0..7) %}
  <tr>
  {%- if forloop.first %}
    <th rowspan="8">shades</th>
  {%- endif %}
    <th>{{ page.bases[i]] }}</th>
  {%- for colorscheme in colorschemes %}
  {%- assign palette = site.data.colorschemes[colorscheme] %}
  {%- assign color = palette.colors[i] %}
    <td>{{ color.name }}</td>
    <td>{{ color.lab.l }} {{ color.lab.a }} {{ color.lab.b }}</td>
    <td>{{ color.rgb.hex }}</td>
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
  {%- for colorscheme in colorschemes %}
  {%- assign palette = site.data.colorschemes[colorscheme] %}
  {%- assign color = palette.colors[i] %}
    <td>{{ color.name }}</td>
    <td>{{ color.lab.l }} {{ color.lab.a }} {{ color.lab.b }}</td>
    <td>{{ color.rgb.hex }}</td>
  {%- endfor %}
  </tr>
{%- endfor %}
</table>

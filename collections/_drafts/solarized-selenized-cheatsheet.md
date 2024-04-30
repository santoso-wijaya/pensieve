---
title: Solarized & Selenized Colorscheme Cheatsheet
tags: colorscheme cheatsheet solarized selenized
classes: wide
---

Note: Color values here are canonical in CIE L*a*b* form. The included sRGB
values were computed with [`palettte`](https://docs.rs/palette/latest/palette/).

## Solarized (dark & light)

{% assign colorschemes = "solarized_dark,solarized_light" | split:"," %}

<table>
  <tr>
    <th rowspan="2"></th>
    <th rowspan="2">Base16</th>
  {% for colorscheme in colorschemes %}
  {% assign palette = site.data.colorschemes[colorscheme] %}
    <th colspan="3">{{ palette.palette }}</th>
  {% endfor %}
  </tr>
  <tr>
  {% for colorscheme in colorschemes %}
    <th>name</th>
    <th><strong>L*a*b*</strong></th>
    <th>sRGB</th>
  {% endfor %}
  </tr>

  <tr>
    <th rowspan="8">shades</th>
{% for i in (0..7) %}
  <th>base0{{ i }}</th>
  {% for colorscheme in colorschemes %}
  {% assign palette = site.data.colorschemes[colorscheme] %}
  {% assign color = palette.colors[i] %}
    <td>{{ color.name }}</td>
    <td>{{ color.lab.l }} {{ color.lab.a }} {{ color.lab.b }}</td>
    <td>{{ color.rgb.hex }}</td>
  {% endfor %}
  </tr>

  {% unless forloop.last %}
    <tr>
  {% endunless %}
{% endfor %}

<!-- TODO: render the 8 accent rows -->
</table>

## Selenized (dark & light)

{% assign colorschemes = "selenized_dark,selenized_light" | split:"," %}

<table>
  <tr>
    <th rowspan="2"></th>
    <th rowspan="2">Base16</th>
  {% for colorscheme in colorschemes %}
  {% assign palette = site.data.colorschemes[colorscheme] %}
    <th colspan="3">{{ palette.palette }}</th>
  {% endfor %}
  </tr>
  <tr>
  {% for colorscheme in colorschemes %}
    <th>name</th>
    <th><strong>L*a*b*</strong></th>
    <th>sRGB</th>
  {% endfor %}
  </tr>

  <tr>
    <th rowspan="8">shades</th>
{% for i in (0..7) %}
  <th>base0{{ i }}</th>
  {% for colorscheme in colorschemes %}
  {% assign palette = site.data.colorschemes[colorscheme] %}
  {% assign color = palette.colors[i] %}
    <td>{{ color.name }}</td>
    <td>{{ color.lab.l }} {{ color.lab.a }} {{ color.lab.b }}</td>
    <td>{{ color.rgb.hex }}</td>
  {% endfor %}
  </tr>

  {% unless forloop.last %}
    <tr>
  {% endunless %}
{% endfor %}
</table>

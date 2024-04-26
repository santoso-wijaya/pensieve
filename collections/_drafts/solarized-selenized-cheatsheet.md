---
title: Solarized & Selenized Colorscheme Cheatsheet
tags: colorscheme cheatsheet solarized selenized
classes: wide
colorschemes:
  - selenized_light
  - solarized_light
  - solarized_dark
  - selenized_dark
---

<table>
  <tr>
    <th rowspan="2"></th>
    <th rowspan="2">Base16</th>
    <th rowspan="2">Suggested usage</th>
  {% for colorscheme in page.colorschemes %}
  {% assign palette = site.data.colorschemes[colorscheme] %}
    <th colspan="3">{{ palette.palette }}</th>
  {% endfor %}
  </tr>
  <tr>
  {% for colorscheme in page.colorschemes %}
    <th>name</th>
    <th><strong>L*a*b*</strong></th>
    <th>sRGB</th>
  {% endfor %}
  </tr>
</table>

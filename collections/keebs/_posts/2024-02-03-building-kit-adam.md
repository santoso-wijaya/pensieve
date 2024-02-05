---
title:  "Building Kit Adam"
tag: mechanical keyboard
toc: true
toc_icon: "keyboard"
#header:
  #image: /assets/keebs/kit-adams/done_header.jpeg # TODO
---

I spent the day building Kit Adam today. 楽しかったよ。

{% assign assets_base = "assets/keebs/kit-adams/" %}

#### Unboxing...

{% responsive_image_block %}
  path: {{ assets_base | append: "unboxing.jpeg" }}
  alt: "Unboxing Kit Adam"
{% endresponsive_image_block %}

{% comment %}
  The above tag is provided by jekyll-responsive-image plugin.
  It would generate an `<img srcset>` tag like this:
  <img src="/assets/resized/unboxing-1400x1050.jpeg"
       alt="Unboxing Kit Adam"
       srcset="/assets/resized/unboxing-320x240.jpeg 320w,/assets/resized/unboxing-480x360.jpeg 480w,/assets/resized/unboxing-800x600.jpeg 800w,/assets/resized/unboxing-1400x1050.jpeg 1400w, /assets/keebs/kit-adams/unboxing.jpeg 5712w"
  />
{% endcomment %}

#### The PCB

{% assign alt = "An ADAM/アダム PCB" %}
{% for i in (1..3) %}
  {% responsive_image_block %}
    path: {{ assets_base | append: "pcb" | append: i | append: ".jpeg" }}
    alt: {{ alt }}
  {% endresponsive_image_block %}
{% endfor %}

#### *Stabby stabby*

{% assign alt = "Mounting stabilizers into plate" %}
{% for i in (1..3) %}
  {% responsive_image_block %}
    path: {{ assets_base | append: "stabs" | append: i | append: ".jpeg" }}
    alt: {{ alt }}
  {% endresponsive_image_block %}
{% endfor %}

#### Switches

The mounted switches clips the PCB-foam-plate sandwich together. I'm using
Gateron Jupiter tactile brown switches here.

{% assign alt = "Gateron Jupiter brown switches" %}
{% for i in (1..4) %}
  {% responsive_image_block %}
    path: {{ assets_base | append: "switches" | append: i | append: ".jpeg" }}
    alt: {{ alt }}
  {% endresponsive_image_block %}
{% endfor %}

Switches は完成だ！

{% responsive_image_block %}
  path: {{ assets_base | append: "switches5.jpeg" }}
  alt: {{ alt }}
{% endresponsive_image_block %}

#### Casing

{% assign alt = "Casing" %}
{% for i in (1..2) %}
  {% responsive_image_block %}
    path: {{ assets_base | append: "case" | append: i | append: ".jpeg" }}
    alt: {{ alt }}
  {% endresponsive_image_block %}
{% endfor %}

#### Paddings

{% assign alt = "Foam paddings" %}
{% for i in (1..2) %}
  {% responsive_image_block %}
    path: {{ assets_base | append: "padding" | append: i | append: ".jpeg" }}
    alt: {{ alt }}
  {% endresponsive_image_block %}
{% endfor %}

#### Keycaps

Next: keycaps. I chose a Matcha themed set with *kana* sub legends.

あとは keycaps の問題なんだ。「Matcha」のデサインを選んだ。

{% assign alt = "Matcha keycaps" %}
{% for i in (1..2) %}
  {% responsive_image_block %}
    path: {{ assets_base | append: "keycaps" | append: i | append: ".jpeg" }}
    alt: {{ alt }}
  {% endresponsive_image_block %}
{% endfor %}

WERK!

{% responsive_image_block %}
  path: {{ assets_base | append: "keycaps_werk.jpeg" }}
  alt: "Partially installed keycaps spelling WERK"
{% endresponsive_image_block %}

あいすキミを

{% responsive_image_block %}
  path: {{ assets_base | append: "keycaps_aisu.jpeg" }}
  alt: "Partially installed keycaps spelling あいすきみを"
{% endresponsive_image_block %}

#### All done!

{% assign alt = "Finished keyboard" %}
{% for suffix in [1, 2, "_pegboard"] %}
  {% responsive_image_block %}
    path: {{ assets_base | append: "done" | append: suffix | append: ".jpeg" }}
    alt: {{ alt }}
  {% endresponsive_image_block %}
{% endfor %}

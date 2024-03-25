---
title     : "Building Kit Adam"
tag       : mechanical keyboard
toc       : true
toc_icon  : "keyboard"

gallery-pcb:
- url           : /assets/keebs/kit-adams/pcb1.jpeg
  image_path    : /assets/keebs/kit-adams/pcb1.jpeg
  alt           : &pcb "An ADAM/アダム PCB"
  title         : *pcb
- url           : /assets/keebs/kit-adams/pcb2.jpeg
  image_path    : /assets/keebs/kit-adams/pcb2.jpeg
  alt           : &pcb
  title         : *pcb
- url           : /assets/keebs/kit-adams/pcb3.jpeg
  image_path    : /assets/keebs/kit-adams/pcb3.jpeg
  alt           : &pcb
  title         : *pcb

gallery-stabs:
- url           : /assets/keebs/kit-adams/stabs1.jpeg
  image_path    : /assets/keebs/kit-adams/stabs1.jpeg
  alt           : &stabs "Stabilizers mounted into the plate"
  title         : *stabs
- url           : /assets/keebs/kit-adams/stabs2.jpeg
  image_path    : /assets/keebs/kit-adams/stabs2.jpeg
  alt           : *stabs
  title         : *stabs
- url           : /assets/keebs/kit-adams/stabs3.jpeg
  image_path    : /assets/keebs/kit-adams/stabs3.jpeg
  alt           : *stabs
  title         : *stabs

gallery-switches:
- url           : /assets/keebs/kit-adams/switches1.jpeg
  image_path    : /assets/keebs/kit-adams/switches1.jpeg
  alt           : &switches "Gateron Jupiter brown tactile switches"
  title         : *switches
- url           : /assets/keebs/kit-adams/switches2.jpeg
  image_path    : /assets/keebs/kit-adams/switches2.jpeg
  alt           : *switches
  title         : *switches
- url           : /assets/keebs/kit-adams/switches3.jpeg
  image_path    : /assets/keebs/kit-adams/switches3.jpeg
  alt           : *switches
  title         : *switches
- url           : /assets/keebs/kit-adams/switches4.jpeg
  image_path    : /assets/keebs/kit-adams/switches4.jpeg
  alt           : *switches
  title         : *switches
- url           : /assets/keebs/kit-adams/switches5.jpeg
  image_path    : /assets/keebs/kit-adams/switches5.jpeg
  alt           : *switches
  title         : *switches

gallery-case:
- url           : /assets/keebs/kit-adams/case1.jpeg
  image_path    : /assets/keebs/kit-adams/case1.jpeg
  alt           : &case "Building the lego-like casing"
  title         : *case
- url           : /assets/keebs/kit-adams/case2.jpeg
  image_path    : /assets/keebs/kit-adams/case2.jpeg
  alt           : *case
  title         : *case

gallery-padding:
- url           : /assets/keebs/kit-adams/padding1.jpeg
  image_path    : /assets/keebs/kit-adams/padding1.jpeg
  alt           : &padding "Foam paddings"
  title         : *padding
- url           : /assets/keebs/kit-adams/padding2.jpeg
  image_path    : /assets/keebs/kit-adams/padding2.jpeg
  alt           : *padding
  title         : *padding

gallery-keycaps:
- url           : /assets/keebs/kit-adams/keycaps1.jpeg
  image_path    : /assets/keebs/kit-adams/keycaps1.jpeg
  alt           : &keycaps "Matcha keycaps"
  title         : *keycaps
- url           : /assets/keebs/kit-adams/keycaps2.jpeg
  image_path    : /assets/keebs/kit-adams/keycaps2.jpeg
  alt           : &keycaps "Matcha keycaps"
  title         : *keycaps
- url           : /assets/keebs/kit-adams/keycaps_werk.jpeg
  image_path    : /assets/keebs/kit-adams/keycaps_werk.jpeg
  alt           : "Partially installed keycaps spelling WERK"
  title         : "WERK!"
- url           : /assets/keebs/kit-adams/keycaps_aisu.jpeg
  image_path    : /assets/keebs/kit-adams/keycaps_aisu.jpeg
  alt           : "Partially installed keycaps spelling あいすきみを"
  title         : "あいすキミを"

gallery-done:
- url           : /assets/keebs/kit-adams/done1.jpeg
  image_path    : /assets/keebs/kit-adams/done1.jpeg
  alt           : &done "Finished keyboard"
  title         : *done
- url           : /assets/keebs/kit-adams/done_pegboard.jpeg
  image_path    : /assets/keebs/kit-adams/done_pegboard.jpeg
  alt           : &pegboard "Finished keyboard mounted on pegboard"
  title         : *pegboard
- url           : /assets/keebs/kit-adams/done2.jpeg
  image_path    : /assets/keebs/kit-adams/done2.jpeg
  alt           : *done
  title         : *done
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

  See: /_includes/responsive-image.html and the .README.md file there.
{% endcomment %}

#### The PCB

{% include gallery id="gallery-pcb" class="full" caption="The アダム PCB." %}

{% comment %}
  See: https://mmistakes.github.io/minimal-mistakes/post%20formats/post-gallery/
{% endcomment %}

#### *Stabby stabby*

{% include gallery id="gallery-stabs" class="full"
                   caption="These stabilizers came pre-lubed. Nice!" %}

#### Switches

The mounted switches clips the PCB-foam-plate sandwich together. I'm using
Gateron Jupiter tactile brown switches here.

{% include gallery id="gallery-switches" class="full"
                   caption="Switches は完成だ！" %}

#### Casing

{% include gallery id="gallery-case" class="full" %}

#### Paddings

{% include gallery id="gallery-padding" class="full" %}

#### Keycaps

Next: keycaps. I chose a Matcha themed set with *kana* sub legends.

{% include gallery id="gallery-keycaps" class="full" %}

あとは keycaps の問題なんだ。「Matcha」のデサインを選んだ。

#### All done!

{% include gallery id="gallery-done" class="full" %}

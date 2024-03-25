---
title: "Rainbow Indent Lines"
tags: vim neovim lazyvim plugin rainbow
classes: wide
---

LazyVim also comes with the "ibl"
([`indent-blankline.nvim`](http://www.lazyvim.org/plugins/ui#indent-blanklinenvim))
plugin that renders vertical lines (by default, with the `|` character)
as indent guidelines. I don't like how strong they look, though, in the
Solarized colorscheme that I just applied.

But then I found this
[example config](https://github.com/lukas-reineke/indent-blankline.nvim?tab=readme-ov-file#multiple-indent-colors)
to make them rainbow colored. I thought that was pretty neat. I landed on the
following Lua script to achieve this.

In
[`~/.config/nvim/lua/plugins/indent-blankline.lua`](https://github.com/santoso-wijaya/lazyvim-config/blob/3d9393adacaa03bdb5a44e6a3c920096cefb3cfe/lua/plugins/indent-blankline.lua):

{% responsive_image_block %}
  path: "assets/nvim/lazyvim/neovide-ibl-rainbow.png"
  alt: "LazyVim in NeoVide with Indent Blanklines with rainbow lines"
{% endresponsive_image_block %}

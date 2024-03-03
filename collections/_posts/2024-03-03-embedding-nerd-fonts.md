---
title: Embedding a Nerd Font
tags: web fonts typography
---

I want to embed a Nerd Font patched font on this site. If it works, it should be
able to render the following glyphs.

```toml
[os.symbols]
Macos     = ""
Ubuntu    = "󰕈"
Windows   = "󰍲"
Alpine    = ""
Amazon    = ""
Android   = ""
Arch      = "󰣇"
Artix     = "󰣇"
CentOS    = ""
Debian    = "󰣚"
Fedora    = "󰣛"
Gentoo    = "󰣨"
Linux     = "󰌽"
Raspbian  = "󰐿"
Redhat    = "󱄛"
SUSE      = ""
Mint      = "󰣭"
Manjaro   = ""
```

NF-patched fonts aren't usually freely available on CDN or other like
distribution packages on the web. For this project, I need to download the
patched `.ttf`, compress it into `.woff2`, include it in this site, and define a
CSS font family out of it.

# Install FiraCode Nerd Font

First, we need to install the patched font to obtain its TTF.

```sh
$ brew install --cask font-fira-code-nerd-font
```

# Define a new font family

In our SCSS file:

```scss
/* define a font family for Nerd Fonts patched variant of FiraCode */
@font-face {
  font-family: 'FiraCode Nerd Font';
  src: url('/assets/fonts/FiraCodeNerdFont-Regular.woff2') format('woff2'),
       url('/assets/fonts/FiraCodeNerdFont-Regular.woff') format('woff'),
       url('/assets/fonts/FiraCodeNerdFont-Regular.ttf') format('truetype');
}

/* system typefaces */
$monospace: 'FiraCode Nerd Font', monospace;

code {
  font-family: $monospace;
}
```

# Using NF with CSS classes

We can also render NF glyphs using CSS class names. See:
[Nerd Fonts Cheat Sheet](https://www.nerdfonts.com/cheat-sheet)

```html
@import "https://www.nerdfonts.com/assets/css/webfont.css"

I really <i class="nf nf-fa-heart"></i> <i class="nf nf-custom-vim"></i>
<i class="nf nf-custom-neovim"></i>
```

<center>
I really <i class="nf nf-fa-heart"></i> <i class="nf nf-custom-vim"></i>
<i class="nf nf-custom-neovim"></i>
</center>

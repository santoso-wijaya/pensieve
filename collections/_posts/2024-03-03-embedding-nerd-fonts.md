---
title: Embedding a Nerd Font
tags: web fonts typography
classes: wide
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

# Install Monaspace Nerd Fonts

TIP: [Monaspace](https://monaspace.githubnext.com) (by GitHub) looks gorgeous!
The whole set is pleasant to behold and I appreciate the coding-specific and
contextual ligatures that they've done. I'm using it in my IDEs and terminals,
too, wherever I can.

First, we install the NF-patched fonts set (along with the original).

```sh
$ brew install --cask font-monaspace-nerd-font font-monaspace
```

We can then convert the downloaded OTF (OpenType Fonts) files into WOFF
(Web Fonts) files.

# Define a new web font family

In our SCSS file:

```scss
/* Define a font family for Nerd Fonts patched variant of Monaspace Neon. */
@font-face {
  font-family: 'MonaspiceNe Nerd Font';
  src: url('/assets/fonts/MonaspiceNeNerdFont-Regular.woff2') format('woff2'),
       url('/assets/fonts/MonaspiceNeNerdFont-Regular.woff') format('woff'),
       url('/assets/fonts/MonaspiceNeNerdFont-Regular.otf') format('opentype');
  font-weight: normal;
  font-style: normal;
}

/* system typefaces */
$monospace: 'MonaspiceNe Nerd Font', monospace;

tt,
code,
kbd,
samp,
pre {
  font-family: $monospace;
  // Render all ligature and contextual healing features in Monaspace.
  // See: https://github.com/githubnext/monaspace?tab=readme-ov-file#coding-ligatures
  font-feature-settings: 'calt', 'liga', 'dlig', 'ss01', 'ss02', 'ss03', 'ss04', 'ss05', 'ss06', 'ss07', 'ss08';
}
```

# Using NF with CSS classes

We can also render NF glyphs using CSS class names. See:
[Nerd Fonts Cheat Sheet](https://www.nerdfonts.com/cheat-sheet)

```html
@import "https://www.nerdfonts.com/assets/css/webfont.css"

I really <i class="nf nf-fa-heart"></i>
         <i class="nf nf-custom-vim">im</i>
         <i class="nf nf-custom-neovim">vim</i>
```

<center>
I really <i class="nf nf-fa-heart"></i> <i class="nf nf-custom-vim">im</i>
         <i class="nf nf-custom-neovim">vim</i>
</center>

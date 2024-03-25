---
title: Alacritty
tags: terminal
classes: wide
---

[Alacritty](https://github.com/alacritty/alacritty) is a cross-platform terminal
emulator that's GPU-accelerated with OpenGL and is written in Rust. I find that
developer tools written in Rust, a language beloved by the developer community,
have been impressing me a lot lately. The prompt app
[Starship](https://starship.rs) and NeoVim GUI NeoVide come to mind.

I discovered Alacritty on my search for an alternative---preferably
cross-platform---terminal emulator, as I kept bumping against Mac OS' default
Terminal.app's limitations and rough edges.

What drew me the most to Alacritty is its configurability and customization
options, especially as they can be expressed in developer-friendly `.toml` file
format.

Here's what my Alacritty terminal currently looks like (Solarized, of course).

{% responsive_image_block %}
  path: assets/alacritty/alacritty.png
  alt: "Alacritty terminal with Solarized theme"
{% endresponsive_image_block %}

With my `alacritty.toml` settings:

```toml
[shell]
program = "/bin/zsh"
args = ["-l"]

[window]
dimensions = { columns = 240, lines = 80 }
padding = { x = 5, y = 5 }
dynamic_padding = true
opacity = 0.8
blur = true # Only works on MacOS

[font]
normal.family = "MonaspiceNe Nerd Font"
size = 12

# Colors: Solarized Light
[colors.primary]
foreground  = '0x586e75'
background  = '0xfdf6e3'
[colors.normal]
black       = '0x073642'
red         = '0xdc322f'
green       = '0x859900'
yellow      = '0xb58900'
blue        = '0x268bd2'
magenta     = '0xd33682'
cyan        = '0x2aa198'
white       = '0xeee8d5'
[colors.bright]
black       = '0x002b36'
red         = '0xcb4b16'
green       = '0x586e75'
yellow      = '0x657b83'
blue        = '0x839496'
magenta     = '0x6c71c4'
cyan        = '0x93a1a1'
white       = '0xfdf6e3'
```

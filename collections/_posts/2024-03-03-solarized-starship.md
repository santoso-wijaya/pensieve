---
title: Solarized Starship
tags: terminal shell solarized
---

{% responsive_image_block %}
  path: assets/solarized/starship.png
  alt: "Starship prompt with Solarized colorscheme"
{% endresponsive_image_block %}

I just discovered [Starship](https://starship.rs), a Rusty terminal cross-shell
prompt with tons of customization options.

## Installation

Installation is easy with Homebrew.

```sh
brew install starship
```

## Installing Nerd Fonts

The prompt heavily utilizes extended unicode glyphs that are available in the
[Nerd Fonts](https://www.nerdfonts.com/font-downloads) patched fonts set.
Installing an NF-patched Meslo font, for instance, can be done easily on a Mac
OS with Homebrew.

```sh
brew tap homebrew/cask-fonts
brew install --cask font-meslo-lg-nerd-font
```

Then, we need to use that font in our Terminal or VSCode apps. For Terminal.app,
I find that
["MesloLGS Nerd Font"](https://github.com/ryanoasis/nerd-fonts/tree/master/patched-fonts/Meslo/S)
works best. For VSCode, I am trying out
["MonaspiceNe Nerd Font"](https://github.com/ryanoasis/nerd-fonts/tree/master/patched-fonts/Monaspace)
(based on GitHub's latest
[Monaspace](https://monaspace.githubnext.com/#learn-more) font family) at the
moment.

TODO: I need to also use this font for this site. Using the system font default, 
      these glyphs will not be able to render properly.

## Configuring Starship

I really like the
[Gruvbox Rainbow](https://starship.rs/presets/gruvbox-rainbow.html#gruvbox-rainbow-preset)
preset as a base.

```sh
starship preset gruvbox-rainbow -o ~/.config/starship.toml
```

But I want to *Solarize* it. So I tweaked its palette, and ended up with this
`starship.toml` file.

```toml
"$schema" = 'https://starship.rs/config-schema.json'

format = """
[](sol_orange)\
$os\
$username\
[](bg:sol_yellow fg:sol_orange)\
$directory\
[](fg:sol_yellow bg:sol_cyan)\
$git_branch\
$git_status\
[](fg:sol_cyan bg:sol_blue)\
$c\
$rust\
$golang\
$nodejs\
$php\
$java\
$kotlin\
$haskell\
$python\
[](fg:sol_blue bg:base2)\
$docker_context\
[](fg:base2 bg:base2)\
$time\
[ ](fg:base2)\
$line_break$character"""

palette = 'solarized_light'

[palettes.solarized_light]
# background and content tones:
#                           # DARK MODE             | LIGHT MODE
base03        = '#002b36'   # background            | -
base02        = '#073642'   # background highlights | -
base01        = '#586e75'   # comments              | opt. emph. content
base00        = '#657b83'   # -                     | primary content
base0         = '#839496'   # primary content       | -
base1         = '#93a1a1'   # opt. emph. content    | comments
base2         = '#eee8d5'   # -                     | background highlights
base3         = '#fdf6e3'   # -                     | background
# accent colors:
sol_yellow    = '#b58900'
sol_orange    = '#cb4b16'
sol_red       = '#dc322f'
sol_magenta   = '#d33682'
sol_violet    = '#6c71c4'
sol_blue      = '#268bd2'
sol_cyan      = '#2aa198'
sol_green     = '#859900'
# Note that for tones, the normal relationship for background and body text
# is `base03:base0` for dark mode and `base3:base00` for light mode.
# Notice the "flipping" of leading 0?

[os]
disabled = false
style = "bg:sol_orange fg:base3"

[os.symbols]
Macos = ""
Ubuntu = "󰕈"
Windows = "󰍲"
SUSE = ""
Raspbian = "󰐿"
Mint = "󰣭"
Manjaro = ""
Linux = "󰌽"
Gentoo = "󰣨"
Fedora = "󰣛"
Alpine = ""
Amazon = ""
Android = ""
Arch = "󰣇"
Artix = "󰣇"
CentOS = ""
Debian = "󰣚"
Redhat = "󱄛"
RedHatEnterprise = "󱄛"

[username]
show_always = true
style_user = "bg:sol_orange fg:base3"
style_root = "bg:sol_orange fg:base3"
format = '[ $user ]($style)'

[directory]
style = "bg:sol_yellow fg:base3"
format = "[ $path ]($style)"
truncation_length = 3
truncation_symbol = "…/"

[directory.substitutions]
"Documents" = "󰈙 "
"Downloads" = " "
"Music" = "󰝚 "
"Pictures" = " "
"Code" = "󰲋 "
"workspace" = "󰲋 "

[git_branch]
symbol = ""
style = "bg:sol_cyan"
format = '[[ $symbol $branch ](fg:base3 bg:sol_cyan)]($style)'

[git_status]
style = "bg:sol_cyan"
format = '[[($all_status$ahead_behind )](fg:base3 bg:sol_cyan)]($style)'

[nodejs]
symbol = ""
style = "bg:sol_blue"
format = '[[ $symbol( $version) ](fg:base3 bg:sol_blue)]($style)'

[c]
symbol = " "
style = "bg:sol_blue"
format = '[[ $symbol( $version) ](fg:base3 bg:sol_blue)]($style)'

[rust]
symbol = ""
style = "bg:sol_blue"
format = '[[ $symbol( $version) ](fg:base3 bg:sol_blue)]($style)'

[golang]
symbol = ""
style = "bg:sol_blue"
format = '[[ $symbol( $version) ](fg:base3 bg:sol_blue)]($style)'

[php]
symbol = ""
style = "bg:sol_blue"
format = '[[ $symbol( $version) ](fg:base3 bg:sol_blue)]($style)'

[java]
symbol = " "
style = "bg:sol_blue"
format = '[[ $symbol( $version) ](fg:base3 bg:sol_blue)]($style)'

[kotlin]
symbol = ""
style = "bg:sol_blue"
format = '[[ $symbol( $version) ](fg:base3 bg:sol_blue)]($style)'

[haskell]
symbol = ""
style = "bg:sol_blue"
format = '[[ $symbol( $version) ](fg:base3 bg:sol_blue)]($style)'

[python]
symbol = ""
style = "bg:sol_blue"
format = '[[ $symbol( $version) ](fg:base3 bg:sol_blue)]($style)'

[docker_context]
symbol = ""
style = "bg:base2"
format = '[[ $symbol( $context) ](fg:#83a598 bg:base2)]($style)'

[time]
disabled = false
time_format = "%R"
style = "bg:base3"
format = '[[  $time ](fg:base00 bg:base2)]($style)'

[line_break]
disabled = false

[character]
disabled = false
success_symbol = '[>](bold fg:sol_green)'
error_symbol = '[>](bold fg:sol_red)'
vimcmd_symbol = '[<](bold fg:sol_green)'
vimcmd_replace_one_symbol = '[<](bold fg:sol_violet)'
vimcmd_replace_symbol = '[<](bold fg:sol_violet)'
vimcmd_visual_symbol = '[<](bold fg:sol_yellow)'
```

Neat!

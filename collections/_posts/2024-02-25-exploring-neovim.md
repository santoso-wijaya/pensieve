---
title : "Exploring NeoVim"
tags  : vim nvim terminal editor
---

{% responsive_image_block %}
  path: assets/vim/nvim.png
  alt: "NeoVim in Terminal"
{% endresponsive_image_block %}

I have been using vim and various IDEs with vim-like bindings for a good long
while now, ever since college.

Lately, I have been curious to try NeoVim and its more powerful features. I am
hoping to power up my homekey usage.

# Installing NeoVim

On Mac OS, with Homebrew, that's trivial.

```sh
$ brew install neovim
```

My muscle memory compels me to type `vim` and `view` when opening text files.
To give NeoVim a fair shake at making it into my core personal toolkit, I
created aliases.

In my `~/.zshrc` file:

```sh
if which nvim >/dev/null; then
  function use-nvim  {
    alias vim="nvim"
    alias vi="nvim"
    alias view="nvim -R"
  }
  use-nvim
fi
```

## User Config

Vim reads from `~/.vimrc` and its plugin, etc lives in `~/.vim/`, while
NeoVim canonically reads its vimrc file from `~/.config/nvim/init.vim` (or
`.lua`) and `~/.config/nvim/`, respectively.

I want to keep things as compatible between the two, for now. In case I decide
later to return to Vim--or if I find myself in a system without the facilities
for NeoVim--I want most of what I use to customize NeoVim to also apply to Vim.

More to the point: I want my Vim and NeoVim installations to share the same
config file.

```sh
$ mkdir ~/.vim/
$ ln -s ../.vim ~/.config/nvim  # this redirects nvim's config dir to vim's
$ ln -s $HOME/.vimrc ~/.vim/init.vim    # redirects init.vim to ~/.vimrc
```

The vimrc file `~/.vimrc` now becomes our master vimrc file. It should work
for both NeoVim and Vim.

Its content, at the moment (I'm currently in the middle of trying out three
new plugins: `vim-commentary`, `vim-easymotion`, and `vim-sneak`):

{% highlight viml %}
" Installing vim-plug:
" curl -fLo ~/.vim/autoload/plug.vim --create-dirs \
"    https://raw.githubusercontent.com/junegunn/vim-plug/master/plug.vim
"
call plug#begin()
" The default plugin directory will be as follows:
"   - Neovim (Linux/macOS/Windows): stdpath('data') . '/plugged'

" Make sure you use single quotes
" Shorthand notation; fetches https://github.com/tpope/vim-sensible
Plug 'tpope/vim-sensible'
" Binds 'gc' to toggle comments in visual mode
Plug 'tpope/vim-commentary'
" Syntax highlighting for Liquid tempaltes
Plug 'tpope/vim-liquid'
" Binds some nifty, flighty navigation modes across a f ile
Plug 'easymotion/vim-easymotion'
" Any valid git URL is allowed
" Binds 's{char}{char}' as a quicker 'f' search
Plug 'https://github.com/justinmk/vim-sneak.git'
" Official Rust plugin
Plug 'rust-lang/rust.vim'

" Initialize plugin system
" - Automatically executes `filetype plugin indent on` and `syntax enable`.
call plug#end()

" I was also already using pathogen for Vim to set up Solarized colorscheme.

" First, install pathogen in your system with:
" mkdir -p ~/.vim/autoload ~/.vim/bundle && \
"     curl -LSso ~/.vim/autoload/pathogen.vim https://tpo.pe/pathogen.vim
execute pathogen#infect()


set nocompatible
syntax on
filetype plugin indent on

set background=dark
colorscheme solarized

set hlsearch
set ruler
set colorcolumn=80,120

set number
" toggle line numbers and fold column for easy copying:
nnoremap <F2> :set nonumber!<CR>:set foldcolumn=0<CR>

set backup                      " Be safe.
set history=1000                " Remember a lot.
set showcmd                     " Show the last command.
set showmatch                   " When a bracket is typed show its match.
set smarttab                    " Only respect shiftwidth for code indents.
set expandtab
set tabstop=2
set shiftwidth=2
set autoindent
set smartindent

" Do not clutter the current directory with swap, backup, undo files.
set swapfile
set directory=.swp/,~/.swp/,/tmp//
set backupdir=.backup/,~/.backup/,/tmp//
set undodir=.undo/,~/.undo/,/tmp//
{% endhighlight %}

# (Neo)?Vim Tricks

These posts illustrate the power of Vim that inspires me:

*   [*3 Vim commands for blazingly fast navigation between brackets ⚡*](https://dev.to/m4xshen/3-vim-commands-for-blazingly-fast-navigation-between-brackets-55kc)

# Next: Mastering LSPs

For quick edits and one-offs, Vim is great. It lets me live and stay in the
Terminal without too much context switching. For more extensive coding, though,
I still rely on language features and the bells and whistles delivered by an
IDE like VSCode.

Next up, I want to explore LSP servers and understand how NeoVim, as a client,
interacts with them. My goal is to set one up that lets me work comfortably
in some programming languages of choice, wholly in NeoVim.

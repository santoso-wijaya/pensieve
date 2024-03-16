---
title: "NeoVim as an IDE"
tags: vim neovim plugin lsp editor
---

{% responsive_image_block %}
  path: assets/vim/nvim_nerdtree_coc.png
  alt: "NeoVim with NERDTree and CoC"
{% endresponsive_image_block %}

## Adding a file explorer to Vim with NERDTree plugin

In our vimrc file:

{% highlight viml %}
call plug#begin()
" ...

" A file system explorer in Vim
Plug 'preservim/nerdtree'

" ...
call plug#end()

" NERDTree keybindings
nnoremap <leader>n :NERDTreeFocus<CR>
nnoremap <C-t> :NERDTreeToggle<CR>
" ... (other keybindings and useful autocmds)
{% endhighlight %}

This setup lets me toggle the NERDTree explorer with
<kbd>Ctrl</kbd>+<kbd>T</kbd>, among other automatic quality of life behaviors.
The interface is intuitive enough to use.

{% responsive_image_block %}
  path: assets/vim/nvim_nerdtree.png
  alt: "NeoVim with NERDTree shown"
{% endresponsive_image_block %}

## Adding language support with CoC

This one is a bit more involved, as a client-server architecture is involved.
There are many language servers out there that we can use, and many plugins for
(Neo)Vim that act as LSP clients.

I'm trying out [`coc.nvim`](https://github.com/neoclide/coc.nvim) right now. 
It's got its own extension ecosystem for us to add language support as we need
them.

The Vim plugin part of CoC itself is supposed to be a thin client to a
language server where most of the language logic resides. The plugin handles
rendering of popup menu and taking user input for action. We would also need
to assign key bindings to those user actions for the plugin to be useful.

### Setting up CoC

CoC requires nodejs.

```sh
$ curl -sL install-node.vercel.app/lts | bash
```

First, let's install the plugin itself, and configure some bindings and
custom settings for ourselves. In our vimrc file:

{% highlight viml %}
call plug#begin()
" ...

" Using CoC for LSP
Plug 'neoclide/coc.nvim', {'branch': 'release'}

" ...
call plug#end()

" CoC-recommended settings below

set nobackup
set nowritebackup

set updatetime=300

set signcolumn=yes

" Use tab for trigger completion with characters ahead and navigate
" NOTE: There's always complete item selected by default, you may want to enable
" no select by `"suggest.noselect": true` in your configuration file
" NOTE: Use command ':verbose imap <tab>' to make sure tab is not mapped by
" other plugin before putting this into your config
inoremap <silent><expr> <TAB>
      \ coc#pum#visible() ? coc#pum#next(1) :
      \ CheckBackspace() ? "\<Tab>" :
      \ coc#refresh()
inoremap <expr><S-TAB> coc#pum#visible() ? coc#pum#prev(1) : "\<C-h>"

function! CheckBackspace() abort
  let col = col('.') - 1
  return !col || getline('.')[col - 1]  =~# '\s'
endfunction

" GoTo code navigation
nmap <silent> gd <Plug>(coc-definition)
nmap <silent> gt <Plug>(coc-type-definition)
nmap <silent> gi <Plug>(coc-implementation)
nmap <silent> gr <Plug>(coc-references)

" Use `[g` and `]g` to navigate diagnostics
" Use `:CocDiagnostics` command to get all diagnostics of current buffer in
" location list
nmap <silent> [g <Plug>(coc-diagnostic-prev)
nmap <silent> ]g <Plug>(coc-diagnostic-next)

" Use D to show documentation in preview window
nnoremap <silent> D :call ShowDocumentation()<CR>

function! ShowDocumentation()
  if CocAction('hasProvider', 'hover')
    call CocActionAsync('doHover')
  else
    call feedkeys('K', 'in')
  endif
endfunction

" Highlight the symbol and its references when holding the cursor
autocmd CursorHold * silent call CocActionAsync('highlight')

" Symbol renaming
nmap <leader>rn <Plug>(coc-rename)

" The default PMenu (floating selection menu box) that appears has a color
" scheme that clashes with solarized-dark, making it hard to see.
" I copied these color settings from current PMenu values from :hi
highlight CocFloating cterm=reverse ctermfg=12 ctermbg=0 guibg=Magenta

" end CoC-recommended settings above
{% endhighlight %}

Then, from Vim, execute `:CocConfig` command to create a `coc-settings.json`
config file. I have the following settings defined:

```json
{
  "colors.enable": true,
  "suggest.noselect": true
}
```

Then, either execute `:CocInstall` in a restarted Vim session, or from the
shell, we install some extensions for languages that I will need.

```sh
$ vim +'CocInstall coc-python coc-tsserver coc-rust-analyzer' +qa
$ vim +'CocInstall coc-markdownlint coc-yaml coc-toml' +qa
$ vim +'CocInstall coc-html coc-css coc-json coc-git' +qa
$ vim +'CocInstall coo-sql coc-xml coc-sh' +qa
```

These extensions are published to NPM, and more can be discovered
[there](https://github.com/neoclide/coc.nvim).

### CoC usage

In the vimrc file snippet above, some example notable usage patterns:

*   Press <kbd>TAB</kbd> to accept a selected auto-complete suggestion
*   Press <kbd>gt</kbd> to navigate to type definition under cursor
*   Press <kbd>K</kbd> to show documentation of code under cursor in a preview
    window
*   Customize CoC's floating window colors to harmonize with solarized-dark


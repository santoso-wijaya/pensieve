---
title:  "Solarized"
tags: colorscheme jekyll
---

I love the [Solarized](https://ethanschoonover.com/solarized/) color scheme. I
use it everywhere I code.

Today, I wanted to customize the blog engine powering this Pensieve to also
apply a Solarized color scheme when syntax highlighting a code block.

Code sample:

```ruby
require 'active_record'

class Person < ActiveRecord::Base
  establish_connection :adapter => 'sqlite3', :database => 'foobar.db'
  connection.create_table table_name, :force => true do |t|
    t.string :name
  end
end

bob = Person.create!(:name => 'bob')
puts Person.all.inspect
bob.destroy
puts Person.all.inspect
```

Here's what I did to make this happen.

1.  Locate the current Jekyll theme's css folder, and copy over
    `assets/css/main.scss` file from there.

    ```sh
    % mkdir -p assets/css
    % bundle show minimal-mistakes-jekyll | xargs -I {} \
        cp {}/assets/css/main.scss ./assets/css/main.scss
    ```

1.  Edit the copy and add the color overrides before any of the import
    statements there.

    ```scss
    ---
    ---

    @charset "utf-8";

    /*--- theme customizations ---*/
    /* solarized light syntax highlighting (base16) */
                                // solarized; TERMCOL
    $base00: #fdf6e3 !default;  // base3; brwhite
    $base01: #073642 !default;  // base02; black
    $base02: #586e75 !default;  // base01; brgreen
    $base03: #657b83 !default;  // base00; bryellow
    $base04: #839496 !default;  // base0; brblue
    $base05: #586e75 !default;  // base01; brgreen
    $base06: #eee8d5 !default;  // base2; white
    $base07: #fdf6e3 !default;  // base3; brwhite
    $base08: #dc322f !default;  // red
    $base09: #cb4b16 !default;  // orange
    $base0a: #b58900 !default;  // yellow
    $base0b: #859900 !default;  // green
    $base0c: #2aa198 !default;  // cyan
    $base0d: #268bd2 !default;  // blue
    $base0e: #6c71c4 !default;  // violet
    $base0f: #d33682 !default;  // red
    /*--- end theme customizations ---*/

    @import "minimal-mistakes/skins/{{ site.minimal_mistakes_skin | default: 'default' }}"; // skin
    @import "minimal-mistakes"; // main partials
    ```

    The full file:
    [`pensieve/assets/css/main.scss`](https://github.com/santoso-wijaya/pensieve/assets/css/main.scss).

## Research notes

*   [Syntax highlighting](https://mmistakes.github.io/minimal-mistakes/docs/stylesheets/#syntax-highlighting)
in Minimal Mistakes' documentation.
*   [L\*a\*b values](https://github.com/altercation/solarized/tree/master/vim-colors-solarized#the-values)
    mapping Solarized color names to their hex values and TERMCOL names.
*   [Styling Guidelines](https://github.com/chriskempson/base16/blob/main/styling.md#styling-guidelines)
    for typical uses of colors 0-16.
*   [`minimal-mistakes/_sass/minimal-mistakes/_syntax.css](https://github.com/mmistakes/minimal-mistakes/blob/8a67ce8e41ec850f2d7c373aa47739b2abfee6f1/_sass/minimal-mistakes/_syntax.scss)

TODO: insert color chart here

Next up in my Jekyll theme customization journey: fonts.

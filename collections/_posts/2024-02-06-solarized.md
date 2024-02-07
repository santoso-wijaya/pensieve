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
    // ... (color setup with solarized naming scheme)

    /* NOTE: minimal-mistakes uses roughly the following color naming scheme for
    *       syntax highlighting in code blocks:
    *       (see: _sass/minimal-mistakes/_syntax.scss)
    * $base00: (highlight background)
    * $base01: (unused)
    * $base02: (unused)
    * $base03: (unused)
    * $base04: comment, doc, (line numbers)
    * $base05: name, punctuation, builtin, entity, label, property, (highlight)
    * $base06: background
    * $base07: (unused)
    * $base08: error, exception, generic, constant, variable
    * $base09: literal, number
    * $base0a: type, class, namespace
    * $base0b: date, string, regex, symbol
    * $base0c: operator, namespace, decorator, tag
    * $base0d: attribute, function
    * $base0e: keyword
    * $base0f: (unused)
    */

    // ----------------------------------------------------------------------------

    // Considering all that, the Minimal Mistakes color scheme for
    // DARK solarized is:
    $base00: $-base02   !default; // background highlights
    $base01: $-base2    !default; // -
    $base02: $-base1    !default; // optional emphasized content
    $base03: $-base0    !default; // primary content
    $base04: $-base01   !default; // comments / secondary content
    $base05: $-base1    !default; // optional emphasized content
    $base06: $-base03   !default; // background
    $base07: $-base02   !default; // background highlights
    $base08: $-red      !default;
    $base09: $-orange   !default;
    $base0a: $-yellow   !default;
    $base0b: $-green    !default;
    $base0c: $-cyan     !default;
    $base0d: $-blue     !default;
    $base0e: $-violet   !default;
    $base0f: $-magenta  !default;
    // Note: To switch to LIGHT mode, all we need to do is to flip the $-baseXX
    //       leading zeroes.
    /*--- end theme customizations ---*/

    @import "minimal-mistakes/skins/{{ site.minimal_mistakes_skin | default: 'default' }}"; // skin
    @import "minimal-mistakes"; // main partials
    ```

    The full file:
    [`pensieve/assets/css/_solarized.scss`](https://github.com/santoso-wijaya/pensieve/assets/css/_solarized.scss).

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

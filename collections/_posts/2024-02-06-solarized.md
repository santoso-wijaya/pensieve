---
title:  "Solarized"
tags: colorscheme
---

I love the [Solarized](https://ethanschoonover.com/solarized/) color scheme. I
use it everywhere I code.

Today, I wanted to customize the blog engine powering this Pensieve to also
apply a Solarized color scheme.

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

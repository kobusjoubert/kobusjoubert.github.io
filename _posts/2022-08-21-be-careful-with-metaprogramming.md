---
layout: post
title: "⚙️ Be careful with metaprogramming"
tags: model
---

<div class='red'>
{% highlight ruby %}
# app/models/note.rb
class Note < ApplicationRecord
  %i[aussie british pirate].each do |dialect|
    define_method("#{dialect}_title") do
      "#{title} in #{dialect}."
    end
  end
end
{% endhighlight %}
</div>

<p><hr></p>

When using metaprogramming, add the generated method names to comments which will help you and future maintainers tremendously when using search and find in their text editors while debugging or building new features.

<!--more-->

<div class='green'>
{% highlight ruby %}
...

# Creates the following methods.
#
#   aussie_title
#   british_title
#   pirate_title
#
%i[aussie british pirate].each do |dialect|
  define_method("#{dialect}_title") do
    "#{title} in #{dialect}."
  end
end
{% endhighlight %}
</div>

---
layout: post
title: "Instance variables with before_action 🏹"
tags: rails controller
---

<div class='red'>
{% highlight ruby %}
# app/controllers/notes_controller.rb
class NotesController < ApplicationController
  # GET /notes/1
  def show
    @note = Note.find(params[:id])
  end

  # GET /notes/1/edit
  def edit
    @note = Note.find(params[:id])
  end
end

{% endhighlight %}
</div>

<p><hr></p>

Use a `before_action` to set instance variables used in more than one action.

<!--more-->

<div class='green'>
{% highlight ruby %}
# app/controllers/notes_controller.rb
class NotesController < ApplicationController
  before_action :set_note, only: %i[show edit]

  # GET /notes/1
  def show; end

  # GET /notes/1/edit
  def edit; end

  private

  def set_note
    @note = Note.find(params[:id])
  end
end
{% endhighlight %}
</div>

For consistency's sake, use the name of the instance variable as the function name prefixed with `set_`.

For `@note` use `set_note`.

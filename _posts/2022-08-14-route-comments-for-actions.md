---
layout: post
title: "🛣 Route comments for actions"
tags: rails controller
---

<div class='red'>
{% highlight ruby %}
# app/controllers/notes_controller.rb
class NotesController < ApplicationController
  def show; end
end
{% endhighlight %}
</div>

<p><hr></p>

Use comments to document possible routes for each action.

<!--more-->

<div class='green'>
{% highlight ruby %}
...

# GET /notes/:id
# GET /users/:user_id/notes/:id
def show; end
{% endhighlight %}

This makes it clear which parameters are used when loading different resources.

{% highlight ruby %}
# app/controllers/notes_controller.rb
class NotesController < ApplicationController
  before_action :set_user
  before_action :set_note

  # GET /notes/:id
  # GET /users/:user_id/notes/:id
  def show; end

  private

  def set_user
    @user = User.find(params[:user_id])
  end

  def set_note
    @note = Note.find(params[:id])
  end
end
{% endhighlight %}
</div>

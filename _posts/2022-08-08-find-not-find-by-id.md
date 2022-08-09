---
layout: post
title: "🔍 find(1), not find_by_id(1)"
tags: rails controller
---

<div class='red'>
{% highlight ruby %}
# app/controllers/notes_controller.rb
class NotesController < ApplicationController
  before_action :set_note

  # GET /notes/1
  def show; end

  private

  def set_note
    @note = Note.find_by_id(params[:id])
  end
end
{% endhighlight %}
</div>

<p><hr></p>

Use `find` instead of `find_by_id`.

<div class='green'>
{% highlight ruby %}
...

def set_note
  @note = Note.find(params[:id])
end

...
{% endhighlight %}
</div>

This way, an `ActiveRecord::RecordNotFound` exception will be raised instead of returning `nil` when the record does not exist.

It is not that useful displaying a page to a user with no content about the note. Instead, we want to let the user know that the requested resource does not exist.

When raising the exception, handle it in the current controller or the parent controller if the logic will be the same for other controllers.

<div class='green'>
{% highlight ruby %}
# app/controllers/application_controller.rb
class ApplicationController < ActionController::Base
  rescue_from ActiveRecord::RecordNotFound, with: :record_not_found

  private

  def record_not_found
    redirect_to root_path, alert: 'Record Not Found'
  end
end
{% endhighlight %}
</div>

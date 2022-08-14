---
layout: post
title: "1️⃣ One action for all content types"
tags: rails controller
---

<div class='red'>
{% highlight ruby %}
# app/controllers/notes_controller.rb
class NotesController < ApplicationController
  before_action :set_note

  # GET /notes/:id
  def show; end

  # GET /notes/:id/download
  def download
    send_data @note.to_s, filename: 'note.txt'
  end

  private

  def set_note
    @note = Note.find(params[:id])
  end
end

# app/views/notes/show.html.erb
<%= link_to 'Download', download_note_path(@note) %>
{% endhighlight %}
</div>

<p><hr></p>

You can use one action to render all content types, including downloadable files.

<!--more-->

<div class='green'>
{% highlight ruby %}
# app/controllers/notes_controller.rb
class NotesController < ApplicationController
  before_action :set_note

  # GET /notes/:id
  def show
    respond_to do |format|
      format.html
      format.text { send_data @note.to_s, filename: 'note.txt' }
    end
  end

  private

  def set_note
    @note = Note.find(params[:id])
  end
end

# app/views/notes/show.html.erb
<%= link_to 'Download', note_path(@note, format: :text) %>
{% endhighlight %}
</div>

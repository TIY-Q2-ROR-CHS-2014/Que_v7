Custom layouts:
  controller:
    def new
      @que = Que.new
      respond_with @queue, layout: 'new_layout'
    end
  view:
    app/views/layouts/new_layout.html.haml

  or:
  controller:
    class QuesController < ApplicationController
      layout 'new_queue'
      ...
    end
  view:
    app/views/layouts/new_queue.html.haml

$('selector').autocomplete({
  source: 'url',
  minLength: 3,
  select: function(event, ui){
    // ui.item.id
    // ui.item.label
    // set hidden field with the ID
    $(this).siblings('.user_name').val(ui.item.id)
  }
})
To get your URL:
  rake routes and grab the URI
    ex: '/hospitals'

Controller:
  return some json
  def index
    @patients = Patient.all
    respond_to do |format|
      format.json { render json: @patients.map{|p| {label: p.name, id: p.id }} }
    end

  end

https://developer.mozilla.org/en-US/docs/Web/Guide/API/DOM/Manipulating_the_browser_history
http://stackoverflow.com/questions/9340121/which-one-is-better-pushstate-or-location-hash
window.location = ''
window.pushState

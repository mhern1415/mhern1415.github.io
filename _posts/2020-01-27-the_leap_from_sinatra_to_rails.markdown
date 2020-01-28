---
layout: post
title:      "The Leap From Sinatra to Rails"
date:       2020-01-28 01:50:02 +0000
permalink:  the_leap_from_sinatra_to_rails
---


As soon as I began the rails section of the Flatiron School, I was excited to see the differences between what I had just done with my Sinatra project and performing the same actions within the rails framework. The repetition of the labs and lessons in Sinatra hammered down the basics and in all honesty, I was happy to be done with Sinatra. I expected Rails to be a bit more lightweight in regards to the amount of code in the project while appearing cleaner and DRY. I wanted to experience the “magic” of rails that was talked about in the intro lesson in the Rails section. 

Like my previous two projects, I wanted to create something practical that I would use on a daily basis. Thinking back to my Sinatra project, I had two models. A User and a “tank” which is another word for an aquarium. This time around, I wanted to see if I could somehow implement four models and after hours of contemplation, I concluded that I would be building a circuit trainer as my Rails project. 

As you’d expect with four models, I spent a majority of my time working through each controller and deciding how each model would interact with the other. I chose to have a User model, a Workout model, a Circuit model, and an Exercise model. Although the requirement calls for one nested resource, I wanted to include multiple nested resources because in a circuit training application, it would make sense for the user to see all exercises related to a circuit and all the circuits related to a workout. 

Throughout the Rails section, one of the differences I enjoyed the most was the ease of forms. Taking a look back at a form in my Sinatra project, the code was not messy by any means but compared to the Rails form using ```form_for```, it was defintely blocky in comparison. 


Sinatra:

```<div class="row">
  <div class="column side" style="background-color:#cce6ff;"><form class="" action="/tanks" method="post">
  <label for="title">Title:</label>
  <input id="title" type="text" name="title" value="">
  <br>
  <br>
  <label for="image_url">Tank Image URL:</label>
  <input id="image_url" type="text" name="image_url" value="">
  <br>
  <br>
  <label for="size">Tank Size:</label>
  <input id="size" type="text" name="size" value="">
  <br>
  <br>
  <label for="flora">Enter All Plants and Fish:</label>
  <input id="flora" type="text" name="flora" value="">
  <br>
  <br>  
  <input type="submit" name="" value="Add Tank">
</form></div>```


Rails: 

`<%= form_for @workout do |f| %>

    <%= f.label :title %>
    <%= f.text_field :title %>
    <br></br>
  
    <%= f.label :circuit_count, "How many circuits do plan on adding?" %>
    <%= f.number_field :circuit_count, min: 0 %>
    <br></br>
  
    <%= f.label :description %>
    <%= f.text_field :description %>
  
      <br></br>
  
    <%= f.submit%>
  <% end %>`
	
There is a noticeable difference in the amount of code when comparing both of these forms. Not only is the the `form_for`  method much cleaner, using partials can eliminate repetitive code when it comes to having both a new and edit view for any given model. 

One of the more interesting requirements of this portfolio project was the implementation of one or more scopes in my app. From the user's perspective, it woulld be extremely beneficial to see which exercises are being performed frequently. If I'm thinking about what kind of exercises I want to add to my circuit, I want to know what everyone else is doing first! This was an easy choice for one of my scopes as I was able to have my Exercise ``index`` page sorted by most popular exercise. How does it determine this? I used a ```left_joins``` to return all the exercises regardless of the amount of circuits involved with each exercise and then sorted them in descending order. Easy!

I was not too familiar with scopes going into this project but with the help of some useful documentation, I was able to add another minor scope on my user show page that displayed the top three workouts for logged in user. I saw this as a way to encourage users to add bigger and more difficult workouts containing higher amounts of circuits. 

Truth be told, I had a lot of fun styling my project using Bootstrap and in the future, I hope to implement Javascript in my projects. Whether your New Year's Resolution is to be more active or maybe try out as many pizza restaurants as you can, I hope we all hit our goals and remain healthy in 2020. I had a blast putting this project together and I can't wait to see what is in store for me as a developer in 2020! 




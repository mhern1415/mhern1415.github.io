---
layout: post
title:      "My Hobby in an App"
date:       2019-11-18 22:20:52 +0000
permalink:  my_hobby_in_an_app
---


One of my biggest passions in life has always been aquariums. The Sinatra project allowed me to give life to an idea that I've had ever since I started learning how to code. I wanted to build an application that allowed users to show off their aquatic creations with a unique profile to each of their tanks. It is quite common for the average hobbyist to have more than one tank and with this application, each user would be able to add a tank that had a unique profile. Each tank would include a picture of the tank, it’s size, and the fish and plants that live in the tank. 

Figuring out what to build was the easy part but soon after that, I had to begin wireframing my application. I had to determine the models, their attributes, and their associations. I knew my main model would be the user but the second model would of course be, the tank itself. My goal was to have each user display their tank/tanks so the once that was clear, I had to give each model it’s attributes. 

Once my wireframing was completed, I used the corneal gem for the first time and I was very impressed with how easy it was to build a gem from scratch. I loved that it created migrations for you! In fact, the whole experience was made much easier because of corneal. I used corneal to generate all of my migrations as well as my model classes. Once I created my seeds, it was time to code!

Coding the app turned out to be a lot easier than I had imagined. Leading up to the project, there were many labs that prepped me for multiple controllers and although it did take many hours, I was able to build out routes in both my ApplicationController and UsersController. 

The biggest hurdle I faced during my project was building out my patch routes when I was working on my CRUD actions. There were many times where I built my form wrong in my edit.erb. 

I failed to include the ```   <input type="hidden" name="_method" value=“patch"> ``` line of code and even after using pry, I was unable to determine the problem. I failed to understand the importance of having a ```hidden``` type with a name of ```_method```. This is very important when working on CRUD actions!

After completing my CRUD actions, my goal was to add validations. I made sure to add the validations to all of my forms to verify that each “attribute” had a “true” value when it came to the attribute’s presence. By adding this to my models, this keeps forms with empty fields from being submitted. This could cause issues especially when signing up as a new user. 

Finally, I wanted to take on flash messages utilizing ```sinatra-flash```. The documentation provided for ```sinatra-flash``` made the install very straight-forward and easy to use. Working alongside my validations, the flash messages would pop up whenever a form was submitted with an empty field or if a password/username could not be verified. This made my application safe from any unwanted errors that could occur.

Overall, the process of creating this application was challenging yet very fun. I do enjoy working on code that involves one of my hobbies. While it was my first time mixing the two, I do hope that it isn’t the last! This is why I got into coding right?

Thank you for reading.

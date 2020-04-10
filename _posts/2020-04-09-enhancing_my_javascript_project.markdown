---
layout: post
title:      "Enhancing my Javascript Project"
date:       2020-04-10 00:48:23 +0000
permalink:  enhancing_my_javascript_project
---


The main thing I wanted to demonstrate in my project was my understanding of how a backend API communicates with a frontend comprised of Javascript. One of the key differences in starting this project was the use of an API. Fortunately, Rails provides a way of making an API rather than making a Rails app that will include a lot of unnecessary files that are not required for an API. 

```
rails new <your_app> --api
```

I will not be covering my entire project build in this blog post! Instead, I wanted to focus on how I enhanced my application with a simple filter. Originally, my application simply displayed quotes that were created using a modal form and that was that. 

Because my application focuses on sport quotes with various athletes from different sports, I wanted to add a feature that allowed the user to filter through the quotes by sport. I started with the five major American sports and ended up with basketball, baseball, football, hockey, and soccer. I quickly realized that some of the most inspirational sports quotes were said by athletes that *didn't* play in those 5 mentioned sports. To remedy this, I added an *other*  category meant specifically for athletes who played in a sport not included in the five major American sports. 

This left me with six different categories of quotes. What if a user only wanted to see quotes from just one sport and not the others? I went through many ideas including searchable tables and a search bar near the top of the page. Using a table would make for a messy interface and a search bar would not be dependable when factoring in typos or capitalization. 

I stumbled upon filtering by `div` elements when I searched for a simple and reliable search method that didn't cause issues with my existing code. The way the filter element works is that the filter will add a "show" class when a certain sport is selected. When a sport is selected, only the sport with a class of "show" will be displayed while all other sports will not have the "show" class included in its `div` element. 

This is all started when a sport is selected and the filter function is triggered using an `onclick` event. In my example below, I set the variable `sportFilter` equal to the `div` that I will be filtering. Once I am able to grab that `div`, I can modify the class name with `.className` to add the keyword `sportFilter` followed by the sport attribute that belongs to the quote.

```
 const sportFilter = document.createElement(`div`)
 sportFilter.dataset.id = this.id 
 sportFilter.className = `sportFilter ${this.sport}`
```

All of the above code takes place in the `render` function of my `Quote` class. 

While that is going on, the filter function is grabbing each element that includes `sportFilter` in it's class name and is adding  or removing the "show" class which will hide or show any given sport. 

While this may sound like a lot, the simple function allows the user to show only the selected while reading quotes on my application. Enhancing the user experience is easily the most gratifying thing about being a developer and providing the best possible interface is what every developer should strive for. 

Thanks for reading and remember to keep it DRY! 

---
layout: post
title:      "My CLI Gem : FunCheapEventsSF"
date:       2019-08-15 02:51:06 +0000
permalink:  my_cli_gem_funcheapeventssf
---


I have finally arrived to my first project of the Flatiron School of Coding. The road to my first project was not an easy one. Due to a family emergency, I had to put coding in the back seat for a little while. It was hard for me to find the motivation to work on my project but I knew I had to keep my coding knowledge fresh so I worked on it when I could and watched a dozen videos on this very project.

I went through a difficult time to say the least but I managed to get back on track with this project and coding in general. I was a bit disappointed with the lack of progress but stressing out about it wasn't going to help.

When it finally came time to work on my project, I already knew that what website I was going to be scraping from. From the time I was in high school, I have been using [Funcheap](https://sf.funcheap.com/) as my only source of fun and cheap events in the Bay Area. The decision to scrape from said website was an easy one and once I had that figured out, I went ahead and starting planning on how a user would use my application. 

I started thinking about how I would structure my application and started with the general user experience. I wanted the user to be able to pick any date and see the events that will take place on that date. After hours of trying of experimenting, I realized that this would not come to fruition. Although I had a scraping tool, I was unable to figure out how to scrape what I wanted and I ended up going with plan B. 

I decided that instead of the user selecting a date to see events, the info that would be scraped would be the events for 'today'. In other words, the application would show the events for the day that the application was being used. Luckily for me, I was able to scrape this information from Funcheap's [Today](https://sf.funcheap.com/today/) page. 

Once I was able to scrape that events, I started looking at what type of information to scrape aside from the event details. Since the whole point of the website is to assist users in finding something cheap, I knew I had to be able to scrape the cost of the event. After finding that part of scrapeable information, I had everything I needed to be able to put this app together. 

In order to figure out my application structure, I went with a basic approach. I started structuring my CLI in the order that the user would see it. I started out with a quick welcome message and followed that with a "event_selection" method that contained most methods that had something to do with the user seeing the events and selection an event based on the selections available to my user. 

```
  def event_selections
    @selections = FunCheapEventsSf::Selection.all
    show_selections
    user_selection
  end

```

This method shows the scraped events to the user and is also responsible for getting the input of the user so that the selected event is shown in detail. 

After that, it was all about constructing my classes and making sure that my code was as DRY as possible. I looked back at my previous labs to refresh my memory when it came to class construction. The biggest issue I had during this portion was remembering the difference between a class and instance method. I can't stress enough how much Google can help in these situations! Everything is covered in our Learn lessons but when stress levels are high, digging through all of that information can be difficult. I ran into many bugs when trying to figure out my CLI structure but in the end, all it took were a few coding refreshers with previous labs, lessons, and video lectures. 

I am very relieved that I finished my first project but after going through a rough couple months, I have plenty of work to get through in order to get back on track. With the right mindset, I believe in myself and in my instructors to guide me through this process.




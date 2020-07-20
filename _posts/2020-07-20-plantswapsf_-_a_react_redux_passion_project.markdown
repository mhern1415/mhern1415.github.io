---
layout: post
title:      "PlantSwapSF - A React/Redux Passion Project "
date:       2020-07-20 15:29:04 -0400
permalink:  plantswapsf_-_a_react_redux_passion_project
---

As I look back at my time here at Flatiron, I noticed a consistent pattern with my projects so far. Each one incorporated a hobby of mine. With that in mind, I decided to base my final project on my biggest hobby. Houseplants!

For my final project here at Flatiron, I decided to build a web application based on a popular Facebook group that I am an active participant in. The aim was very simple. A user would be able to post a plant for sale and a user would be able to see a plant for sale and send an email directly to the seller. I wanted to make the interface as simple as possible while providing the user with all relevant information when it came down to the actual plant for sale. Whether the plant was a small cutting or a large potted plant with roots, the buyer would have every piece of necessary information. 

To accomplish this, I wanted to focus on the functionality and design of my application.


# Functionality

As you will see below, each individual post would have two buttons. One button would link them to an external plant database that would give the buyer more detailed information on the plant and the second button would create an email addressed to the seller. Each button required a bit of code to work correctly and I will go into more detail below. 


![picture](https://i.imgur.com/KUgRSnp.png)

Since I was already making use of my `MapStateToProps` function, I knew I had access to each individual plant title and seller contact. With that in mind, it was all a matter of creating a button with external links and plugging in the information with the use of `props`. 

The code below is a simple href that contains a template literal. If you're new to writing JSX in React, this is huge! If you are using interpolation to insert variables, it is absolutely necessary to make use of the backtick! Without it, your code will immediately break. 

```
< a target="_blank" href={`https://garden.org/plants/search/text.php?q=${post.title}`}><i className="info circle icon"></i>Plants Database Info</a>

```

What I did was simple. Using the title of the plant through the `post.title` prop, I used interpolation to insert the title at the very end of a `garden.org` search query. When clicked, the page will open up in a separate tab and a search query containing the title of the plant post will show. 

The second button also made use of `props` by inserting the title into the subject and message of the email. 

```
<a href={"mailto:" + post.contact + "?subject=" + post.title + " - Plant Swap SF" + "&body=" + message + post.title + message2} target="_blank"><i className="envelope outline icon"></i> Email Seller</a>
```

In order to streamline the entire process, I wanted to prepopulate the subject and message to allow the user to email several sellers in a short matter of time. By including the post title in the subject line and message, there was nothing else the user would need to add in order to specify which plant he/she was interested in purchasing. 

If you look closely at the snippet above, there are also `message` variables included in order to keep the code clean. These variables were declared in my `renderList` function. 

In regards to my application's functionality, these two buttons were integral components to making the user's experience quick and easy. 

# Design

Having previously used bootstrap, I wanted to use Semantic UI for it's ease of use and simplicity. 

To install, I inserted `    <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/semantic-ui/2.4.1/semantic.min.css" />
` in the `head` section of my index.html file. 

I decided to implement a four-column wide grid to my website in order to give the user a good view at multiple posts at once while not being too overwhelming. While the photos are only 300 pixels by 300 pixels on the home page, the user has the ability to see a much larger photo upon clicking on the image or title of the post. 

Semantic UI comes loaded with several icons to choose from that I used in several of my buttons including the Google icon for Google authentication. 

For more information on Semantic UI, click [here](https://semantic-ui.com/introduction/getting-started.html) for the documentation. 

# Conclusion
Nothing about this application was easy but in the end, I was very happy with the finished product. After listening to several of my fellow group members on how I could enhance the user experience, I believe I made something that will appeal to someone who wants a quick and easy way to list plants and to purchase plants from fellow houseplant enthusiasts. 

Thank you for reading!

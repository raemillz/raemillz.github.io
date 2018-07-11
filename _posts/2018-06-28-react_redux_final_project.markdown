---
layout: post
title:      "React/Redux: Final Project"
date:       2018-06-28 13:31:50 -0400
permalink:  react_redux_final_project
---


I’ve finally reached the monumental milestone of completing final project for Flatiron School. While I assume this will just be the first iteration of the app as a whole, getting a functional React/Redux app with a Rails API backend up and running for this project feels like a significant achievement at this point in my coding journey. I found this project to be the most challenging, whether that’s due to the the difficulty of the concepts or how the last section of curriculum relied a lot on the student’s due diligence to read outside sources on the subjects, I’m not sure, but I can say that I’ve come away it feeling much more confident in my craft. 

Ultimately, I decided to keep my project simple by making an app that acts as a suggestion site for ice cream flavors. When a user lands on the site, he/she is able to create an ice cream flavor and add a base and toppings to that flavor. Once it’s created, it is saved to the API and that user (as well as any other) is able to “like” that flavor along with the rest of the created flavors. The flavors are then ordered on the index page from most to least “likes”. 

While I am proud of the app I created, at the beginning of my project I had much larger plans for my app. I planned on integrating a login system, google places search and maps, along with other bells and whistles that would guarantee to impress any future employer. However, after two days on the brink of a nervous breakdown, I learned the tough lesson that with any new skill in life, especially React/Redux, one needs to learn to walk before they can run.

Upon deciding on the newly simplified version of my project, I reminded myself of the project requirements and how to first accomplish those (fancy bells and whistles can come once I pass the assessment). Those requirements are outlined below, along with how I accomplished them.

1. The code should be written in ES6 as much as possible
This was simple, as ES6 is what I was introduced to when learning javascript.

2. Use the create-react-app generator to start your project.
This was a new process for me, but was was easy to understand and follow once I watched this video walkthrough on the subject: https://www.youtube.com/watch?v=wDwb4srbw24

3. Your app should have one HTML page to render your react-redux application
Again, easy enough when following along with the video walkthrough and other docs on React.

4. There should be 2 container components
I ultimately ended up with four container components (container components have access to Redux state). These containers are a show component, card component, index component, and form component.

5. There should be 5 stateless components
Stateless components, as implied, do not have access to Redux state or any lifecycle methods. They are incredibly simple and functional, which is how I managed to make eight of them: Navbar, LikeButton, HomePageImage, Home, FormError, ErrorPageImage, Contact, and About.

6. There should be 3 routes
Routes in React/Redux were a bit difficult for me to understand conceptually, but figuring out what routes I needed was not. I decided on six: home, ice cream index, ice cream show, new ice cream form, about, and contact.

7.  The Application must make use of react-router and proper RESTful routing
This required some extra reading from the docs on how to install react-router-dom and what features to implement from the API. I ended up using withRouter, Route,  and Switch. 

8. Use Redux middleware to respond to and modify state change
Again, some extra reading on the subject was required to fully understand whats going on here. When reading the documentation, this excerpt especially comforting: 

> 	“Middleware sounds much more complicated than it really is. The only way to really understand middleware is to see how the existing middleware works, and try to write your own. The function nesting can be intimidating, but most of the middleware you’ll find are, in fact, 10-liners, and the nesting and composability is what makes the middleware system powerful.”

9. Make use of async actions to send data to and receive data from a server
After this sections curriculum, I actually felt pretty confident with the requirement. It reminded me a lot of the AJAX section curriculum and was relatively easy to implement.

10. Your Rails API should handle the data persistence. You should be using fetch() within your actions to GET and POST data from your API - do not use jQuery 	methods.
I loved setting up the Rails API. That is where I truly felt confident during this project. However, after scrapping the first go at this project due to overcomplicating things, I decided to just stick with one model, for ice creams, which I labeled sweets. This had base, ingredients, name, and likes attributes.

11. Your client-side application should handle the display of data with minimal data manipulation
This sounded much more complicated at first than it actually was. The video walkthrough I mentioned above helped me understand what this requirement meant.

12. Your application should have some minimal styling: feel free to stick to a framework (like react-bootstrap), but if you want to write (additional) CSS yourself, go for 	it!
Because I used bootstrap for my last two projects, I decided to write the css for myself. It’s very simple, and a work in progress, but it’s clean, fun and minimally stylish, so I’m happy with it.


All-in-all, I’m very happy with my app, but I would like to continue building it out to become more complex and feel like an actual app that people would use. But one step at a time, and right now the next step is graduating ;)

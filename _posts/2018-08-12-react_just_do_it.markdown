---
layout: post
title:      "First Take Home Project"
date:       2018-08-12 19:41:42 -0400
permalink:  react_just_do_it
---


Recently, I was given a code challenge as the next step in the interview process with a company I am really excited to have the opportunity to interview with. The guidelines were as followed: 

Build a simple web page that lets you search for recipes using this simple recipe API: (http://www.recipepuppy.com/about/api/) 

Requirements: 
* 		A responsive landing page with a search bar. The user should get a list of results as she types (no extra buttons). The page should work on both web and mobile. &#x2028;
* 		We don’t want to spam the recipe API, so we should send a request only when the user has stopped typing &#x2028;
		
So this seemed relatively straight-forward (albeit vague), but making API calls from a search bar was something I had never done before. Also, I had never used an external API that I hadn’t made. In this blog post I am going to explain my process of building this project.
		
First, I decided that I would build it out using React. I felt that starting a project with create-react-app would be a great was to quickly begin building a single page app. Next was figuring out how to make a search bar component and then connect what a user is typing in that search bar to the Recipe Puppy API. To do this, I researched and reverse engineered other react search components and found what I liked and what I thought would work best for this particular project.

Ultimately I decided to build four additional components (apart from App.js): SearchForm, RecipeList, Recipe, and NoRecipes. Of these components, three are stateless components, with only SearchForm having state. Because of this, I didn’t break them up into different directories, but if the project were bigger and contained more container components then I would separate the components into two different directories (Containers and Components).

The page is rendered from App.js, which is in the src directory, but outside of the Components folder. App.js has a recipes state that initializes with an empty array, and a loading state that initializes with the boolean of true. Once the component mounts (through componentDidMount(), a function called performSearch is called on self. This function preforms a fetch call to the Recipe Puppy API and then resets the recipes state to the API response data’s results and resets the loading state to false. If there is an error with the search or results, the error will show up in the console through console.log. If all goes well, the results will be rendered through the RecipeList component which then renders the Recipe component.

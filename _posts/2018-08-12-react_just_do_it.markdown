---
layout: post
title:      "React, Just Do It"
date:       2018-08-12 23:41:41 +0000
permalink:  react_just_do_it
---


Step 1: Download the template
You’ll find the template for the app at this GitHub repo, in the index.html file.

It’s setup with links to the React, jQuery (for Ajax requests) and other necessary libraries in the <head/> section of the file. There’s also basic component structure containing the necessary HTML tags, as I don’t want to spend time on this. You should be familiar with simple React components from first tutorial in this series.

This is how it looks:


Drag the file into the page, and you’ll see that it almost looks like the final app, though without any functionality.

Step 2: Adding State
In the first tutorial, we only used static data, which meant we could store it as props. This time, we’ll have data that changes, as we’ll display different results on the page based on what the user searches for. When you’re dealing with data that changes in React, you’ll need to involve state in at least one of the components.

Remember: state is mutable and private for the stateful component, while props are immutable and can be shared across components. If this confuses you, read the ‘Learn React.js in 8 Minutes’ article linked to below.
Learn React.JS in 8 Minutes

React.JS is a Javascript library for building user interfaces. It’s fast, easy to learn and fun to work with.
medium.com	
We initialize the App component with a state by adding getInitialState, in which we’ll return whatever we want the initial state to be.


All we’re storing in the state is an array (searchResults) of object. We’ll populate this array with the response from the iTunes API.

Step 3: Add Ajax
In order to get the data, we’ll need to setup our Ajax request in the very same component. Add these two methods below the getInitialState method:


The search method simply sends off an Ajax request based on a URL parameter. Once it gets a response from the API it calls this.showResults (this refers to the App component).

The showResults method puts the results into the state, which is done by the this.setState method. Although the response.results array contains a lot more data than we need (it’s a good practice to limit the amount of data in the state) we’re just going to add the entire thing to the state, for the sake if simplicity.

Notice that we’re binding this in the Ajax request. If we didn’t do this, then the this keyword would refer to the object you see within the Ajax request — the jqXHR object— instead of the React component.
To test that this works: first add the code below within the App component:

componentDidMount(){
   this.search('https://itunes.apple.com/search?term=fun');
},
Now simply console.log() the response in the showResults method. You should be able to see an array of results from the API in the console:


Have a look at the results array in this response, as that’s where we’ll find the content we’ll display on the page.

Note: The componentDidMount method is called automatically by React. This happens directly after the component has been mounted on the page (it only happens once). This is one of many life-cycle methods in React, which you can read more about here if you want.
Step 4: Passing the results down as props
Great. So now you’re able to fetch data from the API.

But the App component isn’t the one that’ll display the search results. That’s the ResultItem components’ job. So we need to make sure the data reaches the right components. Simply pass them down the way you learned to do it in the first tutorial.


In the above image, we’re grabbing the data from the state of the App component and passing it down as props to the Results component.

Once it’s sent down as props, it won’t change, as props are immutable.
To change the searchResults props in the Results component, you’ll have to change the state in App, which will trigger a re-render of the components using these props.

But we’re not finished yet, we need to pass the data all the way down to its final destination: the ResultItem component.

Below you’ll see how the ResultItem components are created. We’re mapping through this.props.searchResults in the Results component.


All of the ResultItem components are stored in an array called resultItems, which we render out between the <ul> tags.

When creating the ResultItem components, we give it a props called trackName, which holds the name of the app/movie/song, and a unique key, which React uses to keep track of the dynamically created elements.

Within the ResultItem component itself, all we need to do it render out a <li> tag which contains the name of the item:


If you drag the file into the browser now, you should see the results from the iTunes API be rendered out (given that you’ve kept the componentDidMount method in the code).

Step 5: Adding interactivity
The final step is to add the interactivity. We need to fetch the users input (both text and category) and use it it to compose the url for the Ajax request.

The first thing we’ll need to to is pass the this.search method down from the App component to the SearchBox component, as that’s where the function will be called (it’s being sent as a props, just as we’ve done with the search result data).


Secondly, we need to modify the JSX in the SearchBox component so that we can fetch the input data from the user:


Notice that we’re adding a few ref attributes to the tags. This enables us to grab the contents of these tags once we need it.

We’re also adding an onClick handler in the button. This is a part Reacts own event system, and it works very much like the onclick event handler you’d use in normal HTML.

In the onClick event listener, we specify which function we want to trigger when someone clicks the button, which is the this.createAjax, that we’ll create next (in the same component):


Here we’re storing whatever the user inputted in the text field and select box in two variables: query and category.

The way to do this is by calling ReactDOM.findDOMNode(), and pass in the reference to the variable we’re looking for. This is where the ref attributes come in handy, as you can see. We then fetch the value from the .value of those node objects.

Finally, we trigger the this.props.search function, passing in the composed URL as the argument.

And that’s it. Now you can refresh the file and try searching for something. Unless you have any syntax errors, it should work.

Congrats on building your second React.js app!

Thanks for reading! My name is Per, I’m a co-founder of Scrimba — a better way to teach and learn code.


If you’ve read this far, I’d recommend you to check out our React screencasts!

Oh, and here’s the full code for this tutorial:




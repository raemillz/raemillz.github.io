---
layout: post
title:      "An Introduction to React/Redux"
date:       2018-07-11 15:54:24 +0000
permalink:  an_introduction_to_react_redux
---


React and Redux were difficult concepts for me to wrap my head around, so in the spirit of continually improving, I’m going to write a blog post about it. First let’s go over some terms to all get on the same page:
React
React is a JavaScript library used for building user interfaces. In this case, it is in charge of showing views and requires the use of additional libraries for state management, routing, and interaction with the API.
Redux
Redux is another JavaScript library and keeps track of the current state of the application.
React & Redux
While both React and Redux are libraries of JavaScript, they are separate and we will need to connect them in order for a React/Redux library to work correctly. In order to do this, we need to forge a connection by using the library react-redux.
Store
The store is just an object with a few functions in it the is responsible for holding the whole state of your application. In order to change the state inside the store, you need to dispatch an action on it. Create the store by passing your root reducing function to ```createStore```.
Middleware
Middleware is used for a variety of things, including API calls, logging actions, and performing side effects like routing.
———————————————————————————————————
The flow of what is happening in a React/Redux app can be overwhelming upon first glance, so let’s walk through it:
	.	The store will dispatch an action that makes new API requests. These requests are asynchronous and Redux is synchronous, so don’t forget to add thunk middleware to your store.
	.	Once the promise is resolved, a new action is dispatched. Actions are produced by functions called action creators. 
	.	The reducer will receive the action of a specific type (ex:  ‘GET_ITEMS’) and create a new, updated copy of state, with all the items.
	.	The new updated state created by the reducer gets re-rendered in the component connected to the store via react-redux connect. Only stateful components should be connected to the store.



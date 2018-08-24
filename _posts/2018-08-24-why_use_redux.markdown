---
layout: post
title:      "Why Use Redux?"
date:       2018-08-24 19:03:35 +0000
permalink:  why_use_redux
---


In a recent interview, when discussing my past and current projects using React, I was asked about when it would be appropriate to implement Redux. When answering, I kept my response broad, saying that once many components contain state you may want to implement Redux to scale the project. Because I wish my answer would have been more specific, in this blog post, I will dive into when to use Redux.

* **Multiple container components use the same piece of application state.**
For example, with session state, information about the user needs to be shared with multiple components (ex: details in the navbar, username, etc.). It’s possible that these components don’t have any direct relationship, so Redux provides a convenient way to share state.
 
* **Props are being passed through multiple hierarchies of components.**
Another good indication that you should consider Redux is if a higher-level component is provided with a dozen props and uses only two of them, and the rest are passed down to a lower-level component. 

* **State management using setState is bloating the component.** 
If components are becoming increasingly complex, separating out the state management into a reducer breaks up the code and makes it more readable.

* **Caching page state.**
Users will often expect their data to be saved once they leave a page so they won't have to retrace their steps everytime they revisit a page. This can be addressed by saving the page state in the backend and recalling it on page load. However, because reducers typically initialize and live throughout the session, they can cache the page state so things remain the same.

---
layout: post
title:      "Rails Project with jQuery Front End"
date:       2018-06-14 02:00:04 +0000
permalink:  rails_project_with_jquery_front_end
---


In this post, I’ll be discussing my experience expanding my Rails Vitamin App to include a JQuery front end. The goal is to add dynamic features that are possible only through jQuery and a JSON Api for your app. Below are the requirements for the project and how I went about meeting them:

##### 1. Must render at least one index page via jQuery and an Active Model Serialization JSON Backend. 
##### 

With this requirement, I realized that I needed to decide which specific features to implement within the context of this application. While rendering  pages via jQuery and an Active Model Serialization can be useful and a great feature for a lot of applications, with my project it felt a bit unnecessary and overcomplicated. So, I decided to only implement these features on the users profile page, where they would be able to dynamically view their packs and the different vitamins within the packs, all without leaving their profile page.

Originally, I skipped making a vitamin_pack index page, and just listed the user's packs on their show page with rails; in order to make this feature work in this context, I created a vitamin_packs index page that could be fetched through AJAX. I also created an index template to be rendered through the index page. Both of these new files displayed the data created through the Active Model Serialization JSON backend, which I'll discuss in the below requirement.

##### 2. Must render at least one show page via jQuery and an Active Model Serialization JSON Backend. 
##### 

This requirement was pretty much the same process as the requirement above. In order for both of these features to work, I needed to build the JSON API using the Active Model Serializers gem. This gem allows you to specify the exact data you would like as a response and delivers it to you in useable format. So for this application, that meant accessing the vitamin_pack id, name, user_id, user, and vitamin_count attributes. This gem also allows you to specify relationships within the context of the model. With vitamin_packs, I included their belongs_to :user and has_many :vitamins associations.

##### 3. The rails API must reveal at least one has-many relationship in the JSON that is then rendered to the page. 
##### 

This was the easiest feature for me to implement, as I had already revealed a has-many relationship on a show page in my original project; at this point, all I needed to go was add the ajax functionality to a link on the show page. To do this, on the user show page (their profile page) I had a link to load all of their vitamin packs. Once they click on that link, ajax is triggered and told to prevent the default behavior of leaving the current page and loading the user vitamin pack index page. Instead, it grabs the data from the index page and renders it inside of a particular div on the show page. This data also includes links to the specific vitamin packs, showing the has-many relationship between vitamin_pack and vitamins.

##### 4. Must use your Rails API and a form to create a resource and render the response without a page refresh. 
##### 

This was the requirement that gave me the biggest headache. For whatever reason, while the form was rendering a new object to the same page, SQL was resubmitting the same query multiple times, causing the request to take over a full minute to complete. After a full days work of coding in circles, I still haven't figured out how I got around this, but somehow it is not longer taking as long.

##### 5. Must translate the JSON responses into Javascript Model Objects. The Model Objects must have at least one method on the prototype. 
##### 

While this wasn't the most frustrating requirement to fulfill, it was the most tedious. To meet this requirement, I creates a VitaminPack prototype object and added multiple functions to that prototype to concatenate (format) the vitamin pack's name and vitamins. I then used the object to append the vitamin pack information to the DOM. The tedious part was formatting the data output in the methods to render correctly on the page.

#### Final Thoughts
#### 

This project was incredibly beneficial in learning how to use multiple languages and functionality in one application. While I don't think that these features were the perfect fit for this project, I know that the knowledge of how to implement them will be incredibly useful in the future. With that being said, I will probably revert the majority of my project back to its original version in the future ;)



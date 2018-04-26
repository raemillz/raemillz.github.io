---
layout: post
title:      "Portfolio Project #3: Rails"
date:       2018-04-26 11:32:58 -0400
permalink:  portfolio_project_3_rails
---

Rails was such a fun tool to add to my coding toolbelt. It allowed me to create a flexible and clean CRUD application and build off of my previous Sinatra project to create a more sophisticated and user friendly application.

# The App
Rails Vitamin App ia an application that allows users to create a profile to track their vitamin regimen. They do this by first creating a vitamin pack (or multiple should that choose) and then choosing vitamins to put into said pack. If they do not see a certain vitamin they would like in their pack, they have the ability to create vitamins to add to the overall vitamin index as well.

# Associations
![](https://imgur.com/a/QorBgF3)

The associations quickly became tricky, as I wanted the objects to exist independently and associate freely. I decided to have four main objects: Users, VitaminPacks, Vitamins, and Benefits. Because VitaminPacks also acted as a join table between Users and Vitamins, I only needed to create two separate join tables: VitaminBenefits and VitaminPackVitamins.

As shown in the above diagram, 

* a User has_many VitaminPacks
* a VitaminPack belongs_to a User
* a VitaminPack has_many Vitamins through the VitaminPackVitamin join table (& viceversa)
* a User has_many Vitamins through VitaminPack (& viceversa)
* a Vitamin has_many Benefits through the VitaminBenefit join tabble (& vicevera)

Originally, I aslo had a UserVitamin join table, but eventually realized that it was unncessary with the VitaminPack table.

# Implementation
I decided to build my own authentication process from scratch, but I hope to learn more about devise at a later point. I just felt that my focus was better utilized elsewhere with this project. Also, I made third-party authentication available through Facebook.

After logging in, a user can see a list of - and CRUD -  their vitamin packs, along with the ability to follow  links to view all currently listed vitamins and benefits. A user is able to create new vitamins and benefits, as long as a they doesn’t already exist in the system. 

Something I am pretty proud of accomplishing with this project is the layout and user experience. CSS and HTML are two things that were extremely lacking in my last two projects, so I set a goal for myself to make this site pretty.

# Reflecting Back
Looking back on this project, I think that I have learned the most and also had the most fun with rails. Although this app could be a lot more sophisticated, I think that it has improved immensely from my first draft of it with Sintatra. This project has also helped me pinpoint certain topic that I’d like to spend more time on in the future, including:
* nested forms, becuase I think that my understanding is still a bit shaky in that subject.
* HTML and CSS, becuase I feel that those will be so applicable to junior developer jobs once I start my career search. They are also such vast topics, I know that I've only scratched the surface.
* SQL. I've really enjoyed working with databases and their associations. However, again I feel that I've only scratched the surface in this knowledge.

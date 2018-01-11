---
layout: post
title:      "A Reflection on my 1st Project"
date:       2018-01-09 23:27:46 -0500
permalink:  a_reflection_on_my_1st_project
---


The first thing that comes to mind when I think of this project is "WOW. That took longer than expected." As much as I would love to blame my prolonged process with this project on the holidays, traveling, etc., etc., when it comes down to it I think my extreme tardiness boils down to two things: 

1. My sheer arrogance in believing I could complete my first project in a day or two, and
2. The crippling fear that ensued upon realizing that this would be far more difficult than I had originally anticipated.

I would also love to say that once I passed that crippling fear it was smooth sailing until I created the CLI Data Gem of my dreams, but that would also be a lie. The truth is, once I passed that initial fear, I only made it a few more steps until I met an even more paralizing panic. This was a pattern that continued for *far* too long, and finally lead me here. I have completed my CLI project, and although it's not the flawless gem I envisioned in my mind weeks ago, I am proud of what I have built and excited by how much I learned through this process.

The idea of my gem came surprisingly easy to me: a directory of great bars in what I believe to be the greatest city in the world, New York. I live here, I drink here, it's very applicable. Next was deciding what website I would be scraping; also an easy choice for me as I trust The Infatuation for any bar or restaurant decision for a night out on the town. However, what I didn't realize was that while this site is extremely trustworthy for your dining and drinking needs, it is a little less reliable in regards to cleanly scraping data (but we'll get to that later).

The first wall of panic I ran into was when I opened up my terminal and saw a blank screen. Yes, that was surprisingly fast. "This is why you got into coding", I reminded myself, "you're learning new things and pushing yourself to be better!" This reminder and encouragement fell on deaf ears, but luckily there were multiple tools (videos and study groups) to help me through my wavering confidence. 

And just like that I was back on track; until, very suddenly, I wasn't. I followed along with Avi's video, he made it seem *very* doable and easy to accomplish, but once it was my turn I struggled piecing it all together. The idea was simple enough: a Manhattan bar directory that greets the user, gives the user a numbered list of neighborhoods, asks the user in which neighborhood it would like to see information on bars, gives the user a numbered list of bars in the previously selected neighborhood, prompts the user to choose a bar, and then gives a description of that bar. Easy, right? 

As I have previously mentioned, the website I chose to scrape from wasn't as straighforward as I had been expecting it to be. While I wanted this gem to be 100% object oriented, I did have to hard-code certain aspects of this project to make it work. Once again, I made it through the challenge with the help from the tools the Flatiron school offers; this time the help of 1:1 video chat specifically for my project. The issue I was facing was that while the description of the bars were children of the bars themselves (i.e. the description was within the section of its bar), the bars were not children of their neighborhoods. There was actually what seemed to be *no* correlation between the bars and the neighborhood to be found while inspecting the HTML of the website. I was comforted to find that this flabbergasted my 1:1 tutor as much as it did myslef. 

I eventually found a way around this by itterating over the neighborhoods, and creating many "if" and "elsif" statements that lead to "bar objects". From that point on, the majority of my setbacks were mental, worrying about the next problem that would lead to having to refracture my whole project. Funnily enough, even this blog was a looming fear of mine. But I kept going, in inconsistent bursts of productivity, until I had a properly working CLI gem. 

Throughout this process, I found, as many find in life, that the things that scare you are often the most rewarding. Reflecting on this project reminds me of how much I learned, how much I struggled, and that I created something from nothing, which is pretty amazing.


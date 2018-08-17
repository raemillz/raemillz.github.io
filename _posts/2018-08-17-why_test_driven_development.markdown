---
layout: post
title:      "Why Test Driven Development"
date:       2018-08-17 15:46:49 +0000
permalink:  why_test_driven_development
---


After graduating from the Flatiron School, I had become familiar with Test Driven Development (TDD), but had yet to actually write many tests for myself. In all of our labs leading up to graduation, we would follow the practice of “red, green, refractor” and know to look in our test folder if we needed to get a better idea of what direction we needed to take to complete the lab. However, writing tests myself is something I have only just begun to explore; While I’ve been aware that writing tests would become all too necessary for larger programs that take a team of people to complete, they never seemed necessary for my own small and modest applications. When it was recommended to me that I start practicing TDD in order to not only be prepared to be a part of a larger team, but to also be taken seriously as a developer, I took that advice in earnest and began reading up on the subject immediately.  I this blog post, I’m going to give a brief summary into my introduction and exploration of TDD.

As I had mentioned above, as a student at the Flatiron School, I was familiar with the process of “red, green, refractor”. That mantra represents, is the steps to take in preforming TDD, also referred to as Test First Development. These steps are:

1. 	Add a test (as a student, these tests were written for us).
2. 	Run all tests and see if any test fails.
3. 	Write some code to make the test pass.
4. 	Run tests and refractor your code to make it DRY.
5. 	Repeat.

While I had become familiar with the above process and knew that it would be used with teams dealing with larger projects, I only vaguely knew why. After researching the subject, I found that the “why” of TDD can be clearly broken down into three reasons:

1. 	Better, cleaner code 
* Because refactoring is a built-in step with TDD, there is normally less duplications, edge cases, and better architecture in applications built with TDD. Still not convinced pretty code is a priority? Think about bringing on (or being) a new developer to a team. They will have to spend a certain amount of time becoming familiar with your code and learning how the different parts of the application interact. Clean code means less mental overhead, confusion, and time when building out new features or fixing bugs.
2. 	The application works as planned   
* There will be less discrepancies between the way the application was envisioned to work in planning and how it actually works in practice, because the tests serve as a specification of what the program *should do*. The code your team will continually be writing will constantly serve to that end.
3. 	It saves you time and money
* The test suite that is built when practicing TDD will cover nearly every line of code your team writes; this means that the entire program can be tested in a matter of minutes. Regardless of the refactoring you do, the typos you make, or the new features you implement, you will rarely have to retrace you steps and waste time finding the source of what broke the program because you have tests to check your progress every step of the way. 

I hope that this blog post has shed some light on the “what” and “why” of TDD. In future posts I will offer a more detailed and specific look into the actual practice of writing your own tests.



---
layout: post
title:      "Rails Portfolio Project"
date:       2018-03-18 18:27:05 +0000
permalink:  rails_portfolio_project
---


Having just completed the Rails Portfolio project, this post will give a brief overview of the app I built and the issues I had.

The App is called `FindADev` and is intended to be used by founders or non-tech individuals who have an idea for a Web app or Saas application and need to find a developer(s) to build it. Users, whether developers or founders, first signup and create a profile. Founders can view the listing of registered developers, add a new project, and then message any developer of interest. Developers can view the list of available projects and message any founder to indicate they're interest.

The only major issue I had is Rails itself. The Rails module in the course is so large that by the time I reached the project, I found that I had forgotten a lot of what I had learnt since the begining. So I spent a month working through the rails labs again, plus creating a couple of Rails demos using Devise (my method of choice for authentication) and using third party providers such as Facebook, Github and Google. If you decide to roll your own authentication check out Michael Hartl's Rails tutorial, if you haven't already. He has a whole section on creating your own authentication.

Going through the Rails module again made building the app far simpler since so many of the concepts were now fresh in my mind. The first part I tackled was the authentication using Devise and included sign via Github and Google. I built the app using BDD/TDD as much as I could. I added a series of Cucumber scenarios to test authentication and then built the code to make the tests pass. 

The controllers and models were built using a combination of writing tests and then writing the code to make them pass or writing the code and then adding the tests subsequently.  Even writing the tests afterwards I found a huge help since they act as regression tests catching any errors that subsequent changes make. That I found was a big help. By constantly running the tests after any change I made I was quickly catching any errrors to previous pieces I had created and so found my debugging quicker and simpler.

Building the app has certainly solidified a lot of what I have learnt so far, but the time I took going through the Rails module again made the whole experience quicker, more enjoyable and certainly a lot less frustrating than I have often found in the past.

You can find the code at the following [Gite repo](https://github.com/theBoyMo/Find-A-Dev)

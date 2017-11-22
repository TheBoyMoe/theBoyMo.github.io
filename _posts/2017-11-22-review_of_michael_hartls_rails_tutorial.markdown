---
layout: post
title:      "Review of Michael Hartl's Rails Tutorial"
date:       2017-11-22 18:34:10 +0000
permalink:  review_of_michael_hartls_rails_tutorial
---


Having just completed [Michal Hartl's Rails Tutorial](https://www.railstutorial.org/book) I thought I'd write a few words about what I thought.

Put simply, It's the best tutorial/technical book I've read. Not only does the code work (use the Gemfile and ruby version suggested), but the book is well written and easy to follow. 

After a couple of introductory chapters, the tutorial takes you step by step through building a Twitter clone. You cover all the usual Rails concepts, models , views, controllers, routes, active record, associations, forms, databases, etc. What set this book apart for me was the amount of testing (although not quite TDD, since often the code was written before the test) and user authentication. It's well worth working through the book just to see how you would 'roll your own' user authentication system without using 3rd party gems. The book also includes pushing the app to Heroku.

I know I'll be going through the book again. Especially since I wrote the tests in RSpec and Capybara - as was used in previous editions. I left a out quite a few of the tests since I didn't know enough RSpec/Capybara. I'm currently reading Myron Marton and Ian Des' 'Effective testing with RSpec 3', so I'll be going back to the Rails Tutorial and finish off those tests when I'm finished.

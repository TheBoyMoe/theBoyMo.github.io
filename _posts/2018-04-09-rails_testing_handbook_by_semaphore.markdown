---
layout: post
title:      "Rails Testing Handbook by Semaphore"
date:       2018-04-09 06:13:43 +0000
permalink:  rails_testing_handbook_by_semaphore
---


If you're interested in learning more about testing your Rails apps with Cucumber, RSpec and Capybara using a BDD approach, then check out the 'Rails Testing Handbook' by Marko Anastasov and the Semaphore team. The book describes BDD and the 'outside in' approach to building Rails apps. Having read the book and coded along the to example app, I can say that the approach has finally made sense. 

Starting out from the feature perspective with a Cucumber scenario and then dropping down to unit tests using RSpec I always found confusing.Before I would always start a feature from say the model, or perhaps connecting to an api and then built outwards. But this always ended in making the same mistakes in that I hadn't properly thought out the feature, the data flows or the model design and meant having to go back and change major parts of what I had already done.  By following BDD you get a better understanding of the feature's behaviour and can more appropriately design and implement it. I implemented this approach to build the Rails ([FindADev](https://github.com/theBoyMo/Find-A-Dev)) app I submitted for the Rails part of the course and found the process easier and strainghtforward. No major re-writes required.

The book also describes integrating the app with Semaphore's CI (30 day free trial), so you can see the app being tested and built in the cloud.

The book is free, [you can get a copy here](https://semaphoreci.com/blog/2018/04/05/rails-testing-handbook-free-ebook.html).  You can see an example of the app [here](https://github.com/theBoyMo/Rails-BDD-Semaphore-Demo)

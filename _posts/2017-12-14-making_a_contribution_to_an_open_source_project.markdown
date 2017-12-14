---
layout: post
title:      "Making a contribution to an Open Source Project"
date:       2017-12-14 14:35:16 +0000
permalink:  making_a_contribution_to_an_open_source_project
---


I've just made my first pull request to an open source project this morning, and it's been accepted. So I'm well pleased. Even though it was a minor fix, just correcting a typo, what I've learn't through the Learn platform (together with the material in edX's Agile development with Rails) gave me the confidence to tackle the issue.

The project in question is the website for Agile Ventures. Agile Ventures is an official UK Charity co-founded by Sam Joseph, Associate Professor of Computer Science at
Hawaii Pacific University and one of the instructors on the edX course. Agile Ventures is dedicated to crowdsourced learning and project development. They follow an Agile approach to software development, using services such as Google Hangouts to enable  remote pair programming. Anyone at any skill level can join and participate.  There are a number of projects currently in progress for real customers in the non-profit sector. Various technologies are in use, from Rails, Node/Javascript, React, Elixir and Ethereum. You can find out more on the [projects page](https://www.agileventures.org/projects).

The first stage involved forking the project and setting it up locally. This involved a number of steps.  The project itself if approx. 320MB, so it took a while to download before i got to installing node, postgresql, bower and various ruby gems. At that point I could run the specs, jasmine and cucumber tests. Just the cucumber tests on my machine took 20 minutes to run, 355 scenarios in total. The documentaion was clear and easy to follow so I didn't have any problems.

Every project follows an agile methodology, so you have to write acceptance/unit tests first before any code. Luckily for me there was already a cucumber scenario that looked for the link text in question. So all I had to do was correct the scenario with the correct spelling, watch the test fail, fix the appropriate erb template, re-run the test and this time watch it pass. It was then simply a case of making a commit, pushing the fix to the fork I had made and then submitting a pull request. Job done.

I know Sam is looking for more volunteers, there's more work than people. No matter you're experience it's well worth checking out. You can find out more about the various membership types [here](https://www.agileventures.org/pricing). You can view the actual [Agile Ventures Git repo](https://github.com/AgileVentures/WebsiteOne) and [contribution guidelines](https://github.com/AgileVentures/WebsiteOne/blob/develop/CONTRIBUTING.md). 

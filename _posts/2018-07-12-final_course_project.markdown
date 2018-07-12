---
layout: post
title:      "Final Course Project"
date:       2018-07-12 18:42:58 +0000
permalink:  final_course_project
---


For my final project I chose to build a clone of [Unsplash](http://unsplash.com),  the royalty free image sharing site. As per the project requirements the front end is built using React, with a Rails backend Api. The actual Unsplash site is built with React and Rails combo!

To upload images users need to sign in. Authentication is provided by the knock gem which returns a JWT token to the client and is saved to sessionStorage in the browser. Although not required to view any galleries, the token is submitted by the client to enable the user to actually upload images.

Image uploading was setup using the paperclip gem. Currently all images are uploaded and saved locally on the server. This setup would thus not work on hosting providers such as Heroku. Currently galleries can be created and viewed. Edit and delete are features that I will add in the future.

The Fetch API was used to login, signup and fetch gallery images via redux async tasks. To upload images I fell back to using the axios client since I just could not find a way to submit the form data using fetch. 

One thing I found in developement when using the Foreman gem to proxy requests from the React client to the Rails api is that I could not debug the api from the console using 'byebug'. I thus switched to running the client and server in their own console windows during development and only switched back to using Foreman at the very end.

You can find the code on [github](https://github.com/theBoyMo/React-Rails-Image-Gallery), and a walkthrough of the app on [youtube](https://www.youtube.com/watch?v=MmOR_5yI3Gs&feature=youtu.be)

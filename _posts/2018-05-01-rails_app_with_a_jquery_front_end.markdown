---
layout: post
title:      "Rails App with a jQuery Front End"
date:       2018-05-01 12:11:32 -0400
permalink:  rails_app_with_a_jquery_front_end
---

In this post I'll cover my experience of upgrading my previous Rails project, [FindADev](https://theboymo.github.io/rails_portfolio_project), to serve json data and include a number of dynamic features through jquery ajax requests.

The app was required to render both a list of items and an individual item through a jquery get request without requiring a page refresh. Implementing the json API on the back-end was straight forward by using the 'respond_to' method in the controllers show and index actions and creating a serialized version of the model using the ActiveModelSerializer gem. I then used a web browser and by adding the .json extension to the end of the url I could see the data that the get request woould recieve. It was then simply a case of adding/removing attributes from the serializer file(not forgeting to include any models that have a 'belongs_to' or 'has_many' relationship to the file - and creating serialzed versions of these models) to fetch all the required properties.

The list items I implemented as a search feature on the Developers page. Clicking the search button executes the jquery get request that returns an array of hashes matching the request. This only worked on the first time, and not subsequently unless the page was refreshed. I discovered that it was turbolinks causing the problem. Turns out it tries to mimick ajax in loading the body of the page without refreshing the whole page. A simple fix is to include the 'turbolinks:load' item when loading the dom:

```
$(document).on('turbolinks:load', function(){
    // your code .....
});
```

To show individual items via ajax I added 'Next/Previous' links to the 'Project' show page allowing users to load the next project in the sequence without requiring a page refresh.

The final dynamic feature I added was to allow users to send messages via form via a jquery post request. If a user clicks on a conversation link they're taken to a list of all the messages that make up that particular conversation. The form at the bottom of that page allows the user to submit a follow up message with out requiring a page refresh - the message item is appended to the bottom of the current list.

One additional requirement was to create a Javascript model object from a function constructor and to define at least one method on the prototype. To fullfill this requirement I created a Project function contructor, together with two methods to actually render the Project item as html before jquery inserts the item into the DOM.


You can see the code [here](https://github.com/theBoyMo/Find-A-Dev).



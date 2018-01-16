---
layout: post
title:      "Integrate authorisation into your Rails app using the Petergate gem"
date:       2018-01-16 19:50:27 +0000
permalink:  integrate_authorisation_into_your_rails_app_using_the_petergate_gem
---


In the Rails module we saw how to integrate authorisation into a Rails app using the Cancancan gem or using Devise roles. In this post I'm going to explain how you can implement authorisation using the Petergate gem.

I'm starting with a Rails 5 app that already has login, logout and signup already setup using Devise so that we can focus on [Petergate](https://github.com/elorest/petergate) setup. 

Make sure your User model is called User. Petergate depends upon this and will automatically provide you with some helpful methods such as 'user_signed_in?'. Devise does this for you when you run the installation. Start off by adding the Petergate gem to your Gemfile, I use [rubygems](https://rubygems.org/gems/petergate) to get the version number.

Next, run the rails generator to install petergate and run the database migration. 

```ruby
  bundle exec rails generate petergate:install
  
  bundle exec rails db:migrate
```


This will add a number of roles to your user model by default, :user and :root_admin. Two other roles are added, :admin and :editor. These can be found in the User model, and can be removed or changed to fit the requirements of the app. In this case I'm going to leave both them. All we'll need for this example are the :user (anyone who is not signed in),  :editor (who is a logged in user, and can create, update and delete posts) and :admin(can do everything) roles.

Before defining what access different roles have to a particular resource, we need a resource for them to access. We'll create a blog using the Rails scaffold generator.

```ruby
  bundle exec rails generate scaffold blog title:string content:text user:references --no-test-framework
	
  bundle exec rails db:migrate
```	


Each blog post item will have a title, content field, add user_id (creating the belongs_to :user relationship in the blog model). Include the '--no-test-framework' option so as to avoid creating any test files. Don't forget to add 'has_many :blogs' to the user model.  I've also added validations to the blog model requiring a title and content.

At the moment any user can create, edit or delete a blog post. Users should be logged in to create a post, and should only be able to edit/delete their own posts. Guest users, not logged in, should only be allowed to read posts. Admins can do everything.

First will lock down post creation, update and destroy using Petergate with the following code, which we'll add to the blogs controller:

```ruby
  access [:all, :user] => [:index, :show], [:editor, :admin] => [:index, :show, :new, :create, :edit, :update, :destroy]
```

This limits post creation, update and deletion to the :editor and :admin roles. Other users are limited to the 'index' and 'show' actions and so can only list or view blog posts. 

Next we will display the edit/destroy links on the blog show and index views only to users logged in as either an :editor or :admin.

By default all users inherit the :user role. We'll give all logged in users the :editor role when the user account is created. In the User model define the 'set_role' method and call it when the user instance is created by using the 'after_create' active record callback.

```ruby
  after_create :set_role

  def set_role
    self.roles = 'editor'
  end
```


All logged in users can now create, edit and delete blogs. Only problem is that they can do that to all blog posts. The final change is to amend the blog controller's 'edit', 'update' and 'destroy' actions to execute the action if the id of the current user is the same as that of the blog's user_id or the current logged in user is an admin.

One last tweak is to remove the user field from the blog form partial which reqires you to enter the user id so as to associate the blog with the user when creating a new blog. This was added by the rails scaffold generator. Instead we'll associate the blog with the user in the blog 'create' action with the following code:

```ruby
   @blog = current_user.blogs.build(blog_params)
```

You can find the full demo at the following [repo](https://github.com/theBoyMo/devise-petergate-demo)




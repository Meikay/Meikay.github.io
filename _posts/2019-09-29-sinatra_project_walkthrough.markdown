---
layout: post
title:      "Sinatra Project Walkthrough"
date:       2019-09-29 22:28:22 -0400
permalink:  sinatra_project_walkthrough
---


How to build a CRUD app using Sinatra and MVC?

My Homework Log app is made for users to be able to log in/signup/logout of a homework assignment as well as be able to edit and delete their homework assignments.

# MVC Structure
Before diving into the project, I thought about what my MVC would look like. What type of data do I need in my models? How do I set up my routes and connect everything in my controllers? And what would all this look like in my views? Instead of building out the MVC structure from scratch, I used a gem named [Corneal](http://github.com/thebrianemory/corneal) created by Brian Emory which scafolds the MVC structure for you. It's simple installation makes set up a breeze! 

I built a `User` model and a `Homework_assignment` model for my project.

# Active Record Associations
For this project, we were required to use at least one `has_many` relationship on a `User` model and one `belongs_to` relationship on another model. Each user `has_many` homework assignments and each homework assignment `belongs_to` a user. 

# Password Encryption
Password encryption was required to protect user accounts from getting hacked. It uses a hashing algorithm to scramble and salt passwords. In order to implement this we installed a gem called [bcrypt](http://github.com/codahale/bcrypt-ruby) and my User's table had a `password_digest `column. I then added `has_secure_password` to my User model and now have all the functionalities of the bcrypt gem.

# Database Migrations
We've been using SQLite for our projects so far which is light weight and simple to use. In db/migrate I created a `users` table and a `homework_assignments` table to which I added the data that was needed to make this app usable. I ran` rake db:migrate` to create a schema file which is a graphical depiction of your database. 

# Render your View 
At this point, we should test out our app adding `get '/' do erb:index end` to your application_contoller.rb . we should see a welcome page that states everything has been setup up successfully if you're using Corneal.

# Controllers
I built three controllers which include the application_contoller, a homework_assignments_controller and a users_controller. They all contain the neccessary routes to help the user sign-in/sign-out, sign-up, and edit.

# Login/Signup
We use the `action` and `method` attributes in HTML to connects to the` /signup` and ` post` routes in the controllers.

# Profile Page
It's time to be redirected to the user's profile page. This happens when iterating over the user object and then set the dynamic route to print out the user name of the current user using the user.username route.

# Edit
To support `PATCH` and `DELETE` method types, you would need to add `Rack::MethodOverride` inside of the config.ru file. Secondly, set up the input like so  `<input type="hidden" name="_method" value="patch">`.

# Ensure User can only edit and delete their own content
At this point, I need to search for the saved user ID in the database that matches the entered username and displays the user's Homework assignements matching the username.

# Validate User's data input
In order for the user to be redirected after signing up, their input needs to be validated so that bad data does not get saved into the data base which will cause problems down the road. I decided to use active record for this where in the models/user.rb I added   
```
validates :username, presence: true  
validates :username, uniqueness: true
```







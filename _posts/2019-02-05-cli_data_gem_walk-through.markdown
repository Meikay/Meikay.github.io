---
layout: post
title:      "CLI Data Gem Walk-Through"
date:       2019-02-06 02:09:32 +0000
permalink:  cli_data_gem_walk-through
---


I was interested in remote full stack positions so I decided why not build that for my portfolio project? I built a Command Line Application that uses object oriented programming to scrape remoteok.io for their top 100 full stack developer jobs. The application is able to do a second level scrape to retrieve the job description. It can be installed as a gem on your local environment as well. My project uses the Nokogiri gem which is an open source software library to parse HTML and XML. 

I will be going through how I built my CLI Data Gem project in the following steps:

# Step 1 Install Bundler gem
In your terminal type
`bundle install remote_jobs`

# Step 2 Add Necessary Files
At this point I had to map out the models I will be using through out my program. I decided to name my folder within lib, remote_jobs and within that folder, I added 3 more files that contained my classes. 


# Setup File Environment
Then , I required the files in remote_jobs.rb to set up my project’s environment. At this point, I had to figure out what objects to build and what their attributes were going to be.


# Add Dependecies
In my remote_jobs.gemspec file, I added the necessary dependecies such as Nokogiri, colorize, and pry. I also added information about my gem such as its name, version, description, authors and homepage.


# Suedo Code
I imagined how my CLI would behave and wrote down some steps. Then, I thought about what methods I would use to make my CLI behave that way. I also needed to find out what data I need to scrape.

# Scrape
I looked for the the data's css selectors so that I am able to access them through their children. I decided to scrape the first 100 full stack jobs from remotok.io and iterated over each job object to grab the job name, company name, and url. On the second scrape, I scraped the description of each job. However, instead of scraping many times and potentially being locked out of the website, I only scraped if the job the user chose does not have a description. 



# Problems I Ran Into & How I(We) Solved It
So inevitably, I ran into difficulty. During this project I was not allowed to reach out to technical coaches for help, so I relied on my tried and trusted friend Google as well as reaching out to my peers for some advice! When you need to code a project from scratch,  you start to realize your weak points. So I figured out that my understanding of object orientation was not as strong as I thought. I re-watched some videos on that subject and implemented my understanding to my project. 

As you can see in the caption above, I said I(we). This was meant to encourage you to ask for help when you get stuck and have tried googling everything you can and searched stack overflow but have still yet to come to a solution. Which comes to the next problem I bumped into, the data on the second scrape was not displaying the way I thought it should. There were {linebreak} everywhere I looked in the description when I ran my program. So I asked a fellow peer to take a look and see what he thought was causing the issue. We played around with the code in pry(debugging tool) and came up with using gsub to fix the issue. This method globally substitutes the first argument with the second argument. This allows us to replace {linebreak} with a literal linebreak everywhere it is found within the description.

```
clean_description = description.gsub("{linebreak}", "\n")
        puts "#{clean_description}".colorize(:blue)
```



All in all, I am grateful to have gone throught this experience and can't wait till my next project!









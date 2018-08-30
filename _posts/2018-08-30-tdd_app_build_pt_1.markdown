---
layout: post
title:      "TDD App Build pt. 1"
date:       2018-08-30 20:26:42 +0000
permalink:  tdd_app_build_pt_1
---


In one of my previous posts, I wrote about Test Driven Development (TDD) - what it means and why it's beneficial to developers. In this post, I'm going to walk though the specific steps I took to build a web app using TDD. This post will most likely be broken up into multiple parts.

The app that I'll be building is similar to Kickstarter; there will be a campaign model that has a title, description, a goal of the amount in donations the campaign is trying to reach, and the amount that has been pledged. 

Setting up: use the `rails new ` command in your terminal. I also used the `--api` flag to specify that I am building an api. What this flag does is removes all of the action/view, along with the asset pipeline. With this app, we won't need to actually render information with HTML, and we won't need an asset pipeline to render the Javascript, CSS, images, or logos; All we will be returning will be JSON or XML. If you decide to use this flag, be sure to have Rails V5 or higher.
Another note: if you're planning on deploying this app to Heroku, I suggest specifying the Postgres database : `rails new kickstarter-inspo --api --database=postgresql`. I decided to just use SQLite3, so I left out that flag. Once you run this code, it shouldn't take long to build since there is less to create when using the `--api` flag.

Next, open up the new project: 
```
cd kickstarter-inspo
```
```
atom .
```
When you open up the Gemfile, you will notice that it is already light; I decided to make it even lighter by deleting jbuilder, redis, capistrano, and bcrypt since there will be no need to use those in this project. However, I did need to add rack cors (because we'll need that eventually) and ActiveModelSerializers for serialization.

I also set up some gems for testing purposes: 
* `rspec-rails` 
* `factory_girl_rails` - for creating facotries that allow easy model testing 
* `shoulda-matchers` - great for testing you models and factories, relationships, and validations
*  `faker` - to easily fake data in out database
*  `database_cleaner` - so when the tests are run, you don’t have to keep clearing out your database

After these steps, my gemfile looked like this:

```
source 'https://rubygems.org'
git_source(:github) { |repo| "https://github.com/#{repo}.git" }

ruby '2.3.3'

# Bundle edge Rails instead: gem 'rails', github: 'rails/rails'
gem 'rails', '~> 5.2.0'
# Use sqlite3 as the database for Active Record
gem 'sqlite3'
# Use Puma as the app server
gem 'puma', '~> 3.11'
# Use ActiveModelSerializers for JSON serialization
gem 'active_model_serializers', '~> 0.10.0'

# Reduces boot times through caching; required in config/boot.rb
gem 'bootsnap', '>= 1.1.0', require: false

# Use Rack CORS for handling Cross-Origin Resource Sharing (CORS), making cross-origin AJAX possible
# gem 'rack-cors'

group :development, :test do
  # Call 'byebug' anywhere in the code to stop execution and get a debugger console
  gem 'byebug', platforms: [:mri, :mingw, :x64_mingw]
  gem 'rspec-rails', '~> 3.5'
end

group :test do
  gem 'factory_girl_rails', '~> 4.0'
  gem 'shoulda-matchers', '~> 3.1'
  gem 'faker'
  gem 'database_cleaner'
end

group :development do
  gem 'listen', '>= 3.0.5', '< 3.2'
  # Spring speeds up development by keeping your application running in the background. Read more: https://github.com/rails/spring
  gem 'spring'
  gem 'spring-watcher-listen', '~> 2.0.0'
end


# Windows does not include zoneinfo files, so bundle the tzinfo-data gem
gem 'tzinfo-data', platforms: [:mingw, :mswin, :x64_mingw, :jruby]
```


 Then run `bundle install` since you’re adding new gems. 
 Then `rails g rspec install`. This will create our spec file and spec folder with a Rails helper and Spec helper. You can remove the original test file that has the mini tests in it: `rm - rf test/`





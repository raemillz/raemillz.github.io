---
layout: post
title:      "TDD Build pt. 2"
date:       2018-09-07 20:17:42 +0000
permalink:  tdd_build_pt_2
---


Continuing from where I left off in my [previous post](http://rachelannemiller.com/tdd_app_build_pt_1), I’m going to start this post off by finishing setting up the gems I added to this project.

I want our tests to respond with a documentation look and color. In order to do this, you need to define the rspec options in the `.rspec `folder:

```
--color
--require spec_helper
--format documentation
```

To get the gems we installed to work with rspec, we need follow the gems’ documentation and insert specific ‘require’ statements into the `rails_helper.rb` folder:

`require ‘database_cleaner’`

And we also need to set up ShouldaMatchers:

```
ActiveRecord::Migration.maintain_test_schema!

  Shoulda::Matchers.configure do |config|
    config.integrate do |with|
      with.test_framework :rspec
      with.library :rails
    end
  end

Along with Factory Girl and Database Cleaner:

RSpec.configure do |config|

  config.include FactoryGirl::Syntax::Methods 

  config.include RequestSpecHelper, type: :request

  config.before(:suite) do
    DatabaseCleaner.clean_with(:truncation)
    DatabaseCleaner.strategy = :transaction
  end

  config.around(:each) do |example|
    DatabaseCleaner.cleaning do
      example.run
    end
  end
```

As mentioned above, all of this info is in the top level of documentation for these gems, so no need to memorize!

Next, we’re going to define what our Campaign model will actually look like. As mentioned in my previous post, we want the campaign to have a title, description, goal, and pledge amount. There will also be a comment model the will have content and a campaign that the comment is correlated with. In the database, it will look something like this:

**Campaign Model:**
Title:String
Description:Text
Goal:Integer
Pledged_Amount:Integer

**Comment Model:**
Content: Text
Campaign_ID:Foreign_Key

To implement this, create a factories folder within you `spec` folder. In this folder, create a `campaign.rb` file that will contain the following code:

```
FactoryGirl.define do
  factory :campaign do
    title { Faker::Lorem.word }
    description { Faker::Lorem.paragraph }
    goal { Faker::Number.between(1000, 100000) }
    pledged_amount { Faker::Number.between(0, 10) }
  end
end
```

And then, in the console, run: 

`rails g model Campaign title description:text goal:integer pledged_amount:number`

This will create a Campaign Model.

Now click on your `campaign_spec.rb` file in your model folder within your spec folder. Within this file is where we put to work our sholda gem and talk about what our model should have and how to validate it. Change the code within this file to the following, which will ensure the Campaign model has the correct relationships and attributes:

```
require 'rails_helper'

RSpec.describe Campaign, type: :model do
  it { should have_many(:comments).dependent(:destroy)}
  it { should validate_presence_of(:title) }
  it { should validate_presence_of(:description) }
  it { should validate_presence_of(:goal) }
  it { should validate_presence_of(:pledged_amount) }
end
```

If you run rspec now, you should see that we have 5 examples and 5 failures. The first failure is telling us that we don’t have an association called “comments”, so our next step should be to create that model and association.


To add the comment model, `run rails g model Comment content:text campaign:references `
This will create the comment model with the `belongs_to` relationship to a campaign. Within the `campaign.rb` file in the models folder, add the following to complete this relationship:

```
class Campaign < ApplicationRecord
  has_many :comments, dependent: :destroy
end
```

Now when you run `rspec`, you should be passing the previously failing test. 

To pass the remaining tests, let’s add some validations to our campaign model:

```
  validates :title, :description, :goal, :pleged_amount, presence: true
```

Great! Now all of the tests should be passing.

Now let’s go back to the `spec` folder and build our comments factory. Create a file within the `factories` folder called `comments.rb` and add the following:

```
FactoryGirl.define do
  factory :comment do
    content { Faker::Lorem.paragraph }
    campaign_id nil
  end
end

```











#Setup Heroku#

Go to **Gemfile**,
Move

 `gem 'sqlite3' `

Like the following

    group :development, :test do
       gem 'sqlite3'
      # Call 'byebug' anywhere in the code to stop execution and get a debugger console
      gem 'byebug'
    end

Then type at the end

     group :production do
    	gem ‘pg’
    	gem ‘rails_12factor’
    end

Now type in

    bundle install –without production
Which makes changes to <a href = "heroku.com">Heroku</a> with those two specific **gems** (not locally)


Now install heroku toolbelt with

 `wget -O- https://toolbelt.heroku.com/install-ubuntu.sh | sh`

Type 

    heroku login

Check if you committed all this stuff to github before you run this <a href = "heroku.com">Heroku</a> test (remember from the last chapter, we test this with `git status`)

Type

    heroku keys:add 
    Y 
    heroku create -> git push heroku master


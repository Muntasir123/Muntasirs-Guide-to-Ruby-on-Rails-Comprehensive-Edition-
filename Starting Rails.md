#Ruby on Rails#
By #Muntasir Alam#

Please ensure you have an understanding of ruby before embarking on the miserable road of rails!


##Running Our Server##

To start the server simply type 

**`rails s -b $IP -p $PORT`**

To start making routes head to **config -> db - > routes.rb**

We can type something like 

    root 'welcome#home'
    get 'welcome/about',to:'welcome#about'

This will set the homepage to **welcome/home**. To go to the about page we simply do **welcome/about** in our search bar. 

To see route types do **rake routes**. You should then see something like



    root GET  /welcome#home
    welcome_about GET  /welcome/about(.:format) welcome#about

We will come back to this in a second.

For now make a file in controllers called **welcome_controller.rb**
Inside write:


    Class WelcomeController < ApplicationController 
    	def home
    	end
    	def aboue
    	end
    end



Now under **views** make a folder called welcome with a file called **home.html.erb** in it and also **about.html.erb**

Lets start linking in the next chapter
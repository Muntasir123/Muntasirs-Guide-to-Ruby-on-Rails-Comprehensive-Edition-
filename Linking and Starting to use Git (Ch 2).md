#Linking and Git#

Now to link **home.html.erb** to **about.html.erb** put this inside **home.html.erb**

    <%= link_to 'About',welcome_about_path %>

**`<% %> `** is needed to let the parser know we are using ruby, you could think of it as **`<?php ?>`** The equal sign is needed for rendering

welcome\_about comes from the **`rake routes`**. Then we add **\_path**. Do similarly for **about.html.erb** except **root_path**

###Starting GIT baby ###

We will be using <a href = "c9.io">C9</a> for our rails application ( you can use nitrous too). 

Do the following in **order**

    git config -global user.name "Rails Projects"
    git config --global user.email alam11o@uwindsor.ca

This is the default data for our repo

To track all the info in our app do

    git init
    git add -A
    git commit -m "Setup rails app"
    
Nice! You can delete a folder ( for ex **config**) by

    rm -rf config

Of course if you always forget you can track changes (any changes, file modification and in this case the deleted folder) with 

    git status

To undo this deletion do 

`git checkout -f`

Alright, now we need to set up an SSH key in <a href = "github.com">Github</a>. Go to your <a href = "github.com">Github</a> profile and delete your old **SSH** key if you had one

To set up SSH key for github do 

`cat ~/.ssh/id_rsa.pub` 

Then put this in in your  <a href = "github.com">Github</a> profile.

Make a repository now then click on ssh. And push the existing repo to command line **Remember to use the SSH version** ( just follow <a href = "github.com">Github</a> instructions `git remote add origin` etc etc ..) 

`git remove -v`  will list the origins

Now we can finally push all this stuff

    git push -u origin master

If you change anything, you can once again check with

    git status

And do

    git add -A
    git commit -m "modified (put whatever you modified or whatever is a good description)"
    git push
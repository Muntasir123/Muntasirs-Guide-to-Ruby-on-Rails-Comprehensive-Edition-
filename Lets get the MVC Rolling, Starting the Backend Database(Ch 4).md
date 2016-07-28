#The Backend#

Some table naming methodologies for rails

Consider the `model name: Article` (we will use this for our app, so get used to it :) )

Heres how it works
_______________________________

**`Model name: Article`**

**`Table Name: articles`**

**`Model name filename: article.rb`**

**`Controller name : articles_controller.rb`**

______________________________________________


Type in

 `rails generate migration create_articles`

Go under **migrate** and see the new file made for you, something along the lines of `create_articles` with some
number in the beginning

Type in the following in the `do` loop

    t.string:title
	t.text:description

Lets consider now though, that we forgot to put in `t.text:description`. How would we go about changing this?

The best way is 

    rake db:migrate

However we can do 

    rake db:rollback

to wipe out the title we put in the schema as well, now we can go back to that `create_articles` file and add 
`t.text:description` and `rake db:migrat`e to update the **schema** (This isn't considered good form, but will work. Usually this is ok if you aren't working in a team)
    

Go to the new file under **migrate **`(description_to_articles.rb)`. In the `def change` add

    add_column :articles, :description, :text
    add_column :articles, :created_at, :datetime
    add_column :articles, :updated_at, :datetime

`rake db:migrate ` again, to update.


Go to the new file under **migrate** `(description_to_articles.rb)`. In the `def change` add

    add_column :articles, :description, :text
    add_column :articles, :created_at, :datetime
    add_column :articles, :updated_at, :datetime

`rake db:migrate` again

Let move on and use **rails console ** to test connections
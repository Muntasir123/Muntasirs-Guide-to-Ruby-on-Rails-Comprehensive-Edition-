## Rails Console and using our first SQL statements ##

Now under app and models put a new file called **article.rb**

Type in `class Article < ActiveRecord::Base`

Now test our table by doing 

    rails console

Since there is info in the **schema**, rails gives us getters and setters, so the console lets us access a database to add stuff into our program.

To test our connection we can simply do

    Article.all

Now lets create a new variable which is empty

    article = Article.New


Lets add a title
    
    article.title = “This is my first title”

Type `article` to see our new variable with new title

    article.description = “This is the description”

Now save this with 

    article.save

we can now see everything by doing `Article.all` again
We can do this process is one line by doing

    article = Article.new(title: "This is my second article",description: "This is my second description")

Then `article.save` then `Article.all` to view our input.


We can also do

    Article.create(title: “This is my third article”, description “The third articles description”)

This automatically inserts it into the database, we don’t need to save.  We can see this with `Article.all`


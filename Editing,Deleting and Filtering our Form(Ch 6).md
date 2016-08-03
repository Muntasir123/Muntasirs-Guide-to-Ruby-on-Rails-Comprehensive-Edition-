## Editing/Deleting and Filtering our form ##


###EDIT##
To edit an article. We must first grab that article.

To grab the second article do (in `rails console`)

    article = Article.find(2) // grab second article
Now we can see this variable we grabbed by simply typing in `article` in the console

We can edit the title by doing

    article.title = "This is an edited article title"
    article.save

We can view the edited article by doing `Article.all`

###DELETE###

Lets delete the third article.

    article = Article.find // grabs third article
	article.destroy
	Article.all // view the our new articles after we delete

###Filtering###

There is a slight problem. Suppose we say `article = Article.new`. We will end up adding an `Article` with **nil** parameters into our database. For this reason, we want to have some conditions that will validate these **nil** queries.

in **models - > articles.rb** type the following inside the **article** class

    validates :title, presence:true

Now make sure to **RELOAD RAILS CONSOLE** ( `Ctrl+C` to do so and `rails console` the command line)

Now try the following

    article = Article.new(description: "This is the test article desc")
    article.save

This will give an error due to our added validation


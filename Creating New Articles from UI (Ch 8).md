#Creating New Articles from UI #

To make sure the **/articles/new directory** exists so we can add from UI, we need to add the actual **route** for it.

Go to **config -> routes.rb**

Inside put `resources :articles` (this gives us a path to **delete,show,index** article path etc)

Type in rake routes to see this path.

Now we need to make `articles_controller.rb `under **controller-> concerns**

Inside write

    Class ArticlesController < ApplicationController
  	  def new
    	end
    end

Now under **views -> articles**, make a new file called **new.html.erb**

Inside Type `<h1>Create an article</h1>` to test out the link out. Now we need to add a form so type

    <%= form_for @article do |f| %>
    <% end %>

Now the code doesent know what `@article` is, so we need to define this at `@article.`


Go back to **articles_controller.rb.** 
Type in 

`@article = Article.new` inside `def new ` to initialize `article` instance variable.


Now go inside new.html.erb. Type in the following Inside `<%= form_for @article do |f| %>` For Title

    <p>
      <%= f.label :title %>
      <%= f.text_field :title%>
    </p>
  

Now make a new `<p>` type in 

For **Description**

    <p>
       <%= f.label :description %><br/>
       <%= f.text_area :description %>
    </p>

For **submit**

    <p>
      <%= f.submit %>
    </p>



 Now we need the **Create Article Button **to actually work, since there is no action create in **articles_controller.rb** 

Go to **articles_controller.rb**
Type in
    
    def create
       render plain: params[:article].inspect
       @article = Article.new(article_params)
       @article.save
    end
    private
    def article_params
     params.require(:article).permit(:title, :description)
       end
    

Now article is hitting the database but once the article is saving it doe-sent know what to do.


If you go to `rails console`, and type in `article.all` you can see that what we type in is indeed hitting the database although we get an error. We need to get it to go to the show template once it saves.


Under `@article.save` in **articles_controller.rb**


Type in `redirect_to articles_show(@article)` 

to go to the article path. Now we need to build the show action. Make sure to `git add -A, git commit -m “New controller stuff”` then `git push` after.


Lets do rake routes again, we realize we messed up the route for **articles\_show** in **articles\_controller.rb** so go to **articles_controller.rb** and replace this with **redirect\_to article\_path(@article)** usually inside `def create` we do

    def create
    @article = Article.new(article_params)
    If @article.save
    #do something
       flash[:notice] = “Article was successfully created”
    redirect_to article_path(@article)
    else
       Render ‘new’
    End


However when we display our notice “Article was successfully created” we want to show this in **application.html.erb **as well since this comes on every page so do this inside the body of **application.html.erb**


    <% flash.each do |name,msg| %>
      <ul>
    <li><%= msg %></li>
      </ul>
    <% end %>

Now we need to display our errors in **new.html.erb** so type in under the` <h1> create and article </h1>`


    <% if @article.errors.any? %>
    <ul>
      <% @articles.errors.full_messages.each do |msg| %>
    <li>  <%= msg %> </li>
      <% end %>
    <ul>
    <% end %>


Now **title can’t be blank, title is too short** etc etc, appears at the top. Now after the `if statement` we can write `<h2> The following errors prevented the article from getting created </h2>`, Just to let us know that the stuff under are the exact errors.

Now we may get the error The action ‘show’ could not be found for `ArticlesController` 
Go to **articles_controller.rb **and add 

    def show
    @article = Article.find(params[:id]);
    End
    
Now we are missing a template for **articles/show**


Now lets create a template under views -> articles create a new file called **show.html.erb**
	
    <h1> Showing Selected Articles </h1>
    <p>
    Title: <%=@article.title %>
    </p>
    <p>
      Description: <%= @article.description %>
    </p>

##Checking Errors and more validation##

In the last chapter we got errors because of our validation. To see exactly whats going on we can do (please stay in `rails console`)

    article.errors.any?

For an specific error do 
	article.errors.full_messages

###More Validation###

Lets add validation for the description as well
Inside our `Article < ActiveRecord::Base`  class we have

    validates :title,presence:true
    validates :description, presence:true

Now we check for validation for useless entries like

     article = Article.new(title:"a",description:"b")

Obviously the solution here, is to add a length validation

To do this simply add length parameters to our extended article class before 

     validates :title, presence: true, length: {minimum: 3, maximum: 50}
      validates :description, presence: true, length: {minimum:10, maximum:300}
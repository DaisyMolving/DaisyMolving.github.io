---
layout: post
comments: true
title: "Ruby: More Encapsulation"
date: 2016-03-10 12:30:30 +0000
---

I previously explained a bit about encapsulation as one of the principles of [Object Oriented Programming][intro-oop-post], but will now take a look at it in a little more depth. Encapsulation is the control of method visibility to users. We control this so that our programme is more secure and less fragile. We can keep features unchanged and only allow users to view and edit information that is applicable to them. After all, we don't need the user to understand <i>how</i> the programme works, we just want it to be working properly in the first place. Encapsulation creates channels through which information is passed and how that is controlled.

<strong> Private and Public Methods </strong>

Encapsulation uses the keywords `private` and `public` to control visibility of methods. By default all methods are public. The `private` keyword hides methods from view, but these methods are still available to be called in other methods within that class. Any method underneath `private` will be hidden unless the `public` keyword is used. For instance:

{% highlight ruby %}

class SecretDiary

	def initialize(owner, text)
		@owner = owner
		@text = text
	end
		
	def tell_secret
		read_diary
		find_secret
		save_to_memory
	end

private
	def save_to_memory 
		secret = find_secret	
		puts "The secret of #{@owner} is #{secret}"
	end

	def find_secret
		secret = ""
		words = read_diary(text)
		words.each_with_index do |word, index|
			if word == "secret:"
				secret << "#{word[index + 1]} #{word[index + 2]} #{word[index + 3]} #{word[index + 4]}"
			end
		end
		secret
	end

public
	def get_owner
		@owner
	end

private
	def read_diary
		@text.split("")
	end
	
diary_1 = SecretDiary.new("Barbara", "Today I went to the mall. I saw Mark. The next part is secret: My crush is Mark!")
diary_1.tell_secret #=> "The secret of Barbara is: My crush is Mark!"
diary_1.get_owner #=> "Barbara"
{% endhighlight %}

The user of this silly programme only wants to know people's secrets. They don't need to know how the programme obtains them from the diary. So any methods that work together to get that information are made private. If the user is friends with the owner of the diary, they might feel bad about learning their secrets so immorally. It would be good to be able to check who the owner is before you call `tell_secret` on this diary. Look how the `get_owner` method is made public. Phewf! 

<strong> Protected Methods </strong>

Private methods can only be called by other methods within the same class. The keyword `protected` is used when you would like to make a method also available to be called in the subclasses of the current class. 

[intro-oop-post]: http://daisymolving.github.io/2016/02/17/introduction-to-OOP.html

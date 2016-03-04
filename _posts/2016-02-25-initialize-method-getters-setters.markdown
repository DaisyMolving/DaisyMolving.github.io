---
layout: post
comments: true
title: "Getting, Setting and Accessing Class Attributes"
date: 2016-02-25 12:30:30 +0000
---

<strong> Initialize and Instance Variables </strong>

We had a look at the initialize method in the previous post and saw how it assigns values to instance variables via arguments when a class is instantiated. Below is a review of how the `Book` class uses the initialize method to assign the attributes `title` and `author` to any new book instance.

{% highlight ruby %}
class Book

	def initialize(title, author)
		@title = title
		@author = author
	end

end

book_1 = Book.new("The Algebraist", "Iain M. Banks")
{% endhighlight %}

Now the `@title` in this instance is assigned to "The Algebraist", and the `@author` in this instance is "Iain M. Banks". Any other methods within `Book` can use methods to act upon these instance variables.

<strong> Getting and Setting </strong>

If we want to be able to return the `title` or `author` of the `book_1` we must write a "getter" method. A getter method accesses and presents attributes. This can be thought of as reading attributes. A getter method can be written like:

{% highlight ruby %}
class Book
	initialize(title, author)
		@title = title
		@author = author
	end

	def get_title
		@title
	end
end

book_1 = Book.new("The Algebraist", "Iain M. Banks")
book_1.get_title #=> "The Algebraist"
{% endhighlight %}

You can see how `get_title`'s purpose is simply to return the instance variable. Also notice how an instance variable can be passed around all methods within the class, where the methods are called upon instances.

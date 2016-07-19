---
layout: post
comments: true
title: "Ruby: Getting, Setting and Accessing Class Attributes"
date: 2016-03-02 12:30:30 +0000
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

If we want to be able to return the `title` or `author` of the `book_1` we must write a "getter" method. A getter method accesses and presents attributes. This can be thought of as <i>reading</i> attributes. A getter method can be written like:

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

To change the title of an instance, or set it, we can create a setter method. Setting an attribute is akin to <i> writing</i> an attribute. Here is an example.

{% highlight ruby %}
class Book
	def initialize(title, author)
		@title = title
		@author = author
	end

	def get_title
		@title
	end

	def set_title=(new_title)
		@title = new_title
	end
end

book_1 = Book.new("The Algebraist", "Iain M. Banks")
book_1.get_title #=> "The Algebraist"
book_1.set_title("The Wasp Factory")
book_1.get_title #=> "The Wasp Factory"
{% endhighlight %}

Here the set_title method is using an argument that the instance is passed to reset the instance variable.

<strong> Attribute Readers and Writers </strong>

We can see how getter methods are like readers and setter methods are like writers. It also seems that potentially writing two methods for every attribute that we want to read and write is quite long and tedious. Luckily Ruby has some helpful alternatives, called attribute readers and writers. If we want to only read attributes we use the keyword `attr_reader`, if we want to write we can use `attr_writer`and if we want to be able to do both then `attr_reader` will be the keyword to use. Here are some examples of how these keywords are used:

{% highlight ruby %}
class Book

attr_accessor :title
attr_reader :author
attr_writer :year

	def initialize(title, author, year)
		@title = title
		@author = author
		@year = year
	end

end

book_1 = Book.new("The Violent Bear It Awry", "Flannery O'Connor", 1959)

book_1.title #=> "The Violent Bear It Awry"
book_1.title("The Violent Bear It Away")
book_1.title #=> "The Violent Bear It Away"

book_1.author #=> "Flannery O'Connor"

book_1.year(1960) 
{% endhighlight %}

See how `attr_accessor` allows us to read and write the title of `book_1`, `attr_reader` allows us to only read the author of `book_1` and `attr_writer` allows us to only write the year (of publication) for `book_1` but not to view it.

There you have it!

P.S. "The Violent Bear It Away" by Flannery O'Connor is a real-life instance of `Book` I would highly recommend.

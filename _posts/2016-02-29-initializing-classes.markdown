---
layout: post
comments: true
title: "Classes"
date: 2016-02-29 12:30:30 +0000
---

In Object Oriented Programming we work with objects. They are the models that represent absolutely everything in our programming universe. They give us information, perform tasks and calculations, and return answers in the form of new objects. A Class is one of these objects, a collection of methods that will be used by an instance of itself. A Class can inherit from a parent Class, and have a child Class that inherits from it. We use Classes when we are modelling objects. An example could be if we wanted to model a book in our local library.  We can do this like so:

{% highlight ruby %}
class Book

#tasks and messages for the book does go here!

end
{% endhighlight%}

Its as simple as that to create a Class! Notice how a Class uses CamelCase? This is an important syntax to define a Class from other objects. Within our Class we would write methods for the Class to perform, think of them as tasks or messages.

<strong> An Instance of a Class </strong>

A Class by itself is abstract. That means that it represents a concept but it does not exist until an instance is created. Our `Book` Class might contain all sorts of parts that a book would have and tasks it might perform, but until we apply it to a real life instance of an actual book it doesn't do anything. So let's create an instance of a book for the `Book` class to act upon. We can do this like so:

{% highlight ruby %}
book_1 = Book.new
{% endhighlight %}

The variable that we assigned it to, `book_1`, is the name that we will give to this particular instance of the `Book` class.

<strong>What Does the Class Contain? </strong>

What sorts of methods or attributes might the `Book` class have? Well it would be helpful if the book had a title and an author that appear upon creation. For this we would use the a method called `initialize`. When a new instance of `Book` is created it looks at the attributes in the `initialize` method and gives these qualities to the given instance.

{% highlight ruby %}
class Book

	def initialize(title, author)
		@title = title
		@author = author
	end

end
{% endhighlight %}

The `initialize` method takes the parameters `title` and `author` and then assigns them to something called instance variables inside the method. Instance variables are the variables there that are prefixed with an `@` sign (`@title` and `@author`). This means that we can instantiate `Book` like this:

{% highlight ruby %}
book_1 = Book.new("The Algebraist", "Iain M. Banks")
{% endhighlight %}

Now the `@title` in this instance is assigned to "The Algebraist", and the `@author` in this instance is "Iain M. Banks". Any other methods within `Book` can use methods to act upon these instance variables.

<strong> Inheritance </strong>

Inheritance is one of the pillars of Object Oriented Programming, and in Ruby each class inherits only from a single parent. A child class implicitly inherits its parent's features, but could also override features that apply to it differently as well as having its own new features. Here is an example:

{% highlight ruby %}
class Animal
	
	def breathe
		puts "This animal breathes."
	end

end

class Mannatee < Animal

	def swims
		puts "Mannatees swim."
	end

end

manuel = Mannatee.new
manuel.swim #=> "Mannatees swim."
manuel.breathe #=> "This animal breathes."
{% endhighlight %}

See how even though there is no `breathe` method in the `Mannatee` class, it can still be called upon an instance of `Mannatee` (called `manuel`) because the `breathe` method is implicitly inherited from the `Animal` class.

If you wanted to override a method in the superclass that the subclass inherits you can do this by simply re-writing the method in the subclass with the same name but a new action. It will mean that the subclass performs this method entirely differently to its parent, but the parent is not affected by the change.

<strong> Super </strong>

There is a keyword `super` which calls information from the parent of the current class, that is in a method of the same name. Sometimes we might want to use a method that the current class's parent defines, and modify it. Usually if we use a method with the same name it will override the parent's method, but not if we use `super`. For example:

{% highlight ruby %}
class Animal

	def move
		print "This animal moves..."
	end

end

class Mannatee < Animal

	def move
		super + "by swimming!"
	end

end

manuel = Mannatee.new
manuel.move #=> "This animal moves...by swimming!"
{% endhighlight %}

<strong> Self </strong>

`self` refers to the class object itself. Usually a method is called upon an instance of a class, like `manuel.move`, but self would allow you to call a method upon `Mannatee`. Another way to say this is that you are using the method to send a message to the class within which it resides. It works like this:

{% highlight ruby %}
def Mannatee < Animal

	def self.also_known_as
		puts "Also known as a sea-cow."
	end

	def speak
		puts "Squeak!"
	end

end

manuel = Mannatee.new
manuel.speak #=> "Squeak!"
manuel.also_known_as #=> NoMethodError: ...
Mannatee.also_known_as #=> "Also known as a sea-cow."
{% endhighlight %}

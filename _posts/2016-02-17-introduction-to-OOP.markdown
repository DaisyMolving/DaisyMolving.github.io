---
layout: post
comments: true
title: "Object Oriented Programming"
date: 2016-02-17 12:30:31 +0000
---

Everything in Ruby is an object, and that means that everything in Ruby shares certain behaviours. These behaviours are the four aspects of Object Oriented Programming. They are called Abstraction, Inheritance, Polymorphism and Encapsulation.

<strong> Abstraction </strong>

Abstraction is the process of making something easier to understand by ignoring details that are unimportant and defining the things that are. In Ruby we do this by creating classes and specifying the qualities that they have and therefore the actions that we want them to take. Imagine you are the director of a birdwatching club in New Zealand. You are concerned with the identifying birds based on their plumage, their call and their habits. You could model them as a Class called Bird. The Bird class will be well defined so that we have only the relevant qualities of what identifies a bird. We don't need to include any information what a bird eats or what their eggs look like. Let's start by simply defining a general bird.

{% highlight ruby %}
class Bird

	def fly
		puts "birds can fly!"
	end

	def call
		puts "makes some noises"
	end

	def plumage
		puts "has feathers"
	end
end
{% endhighlight %}

<strong> Inheritance </strong>

Inheritance is the relationship between a child class and its parent. A child class inherits all the features of its parent class, but can also override certain features as well as have its own unique attributes. In Ruby a class can only inherit from a single other class. For instance, a tui, a kākāpō, a pīwakawaka and a korimako are all belong to the class Bird, but have qualities that make them different birds to the others.

{% highlight ruby %}

class Tui < Bird
	def call
		puts "click cackle squeak"
	end

	def plumage
		puts "mostly black with white tuft at throat"
	end
end

class Piwakawaka < Bird
	def call
		puts "cheet cheet cheet"
	end

	def plumage
		puts "white 'eyebrows' and a fanning tail"
	end
end

class Korimako < Bird
	def call
		puts "sounds like chiming bells"
	end

	def plumage
		puts "acid green with black-tipped wings and tail"
	end
end

class Kakapo < Bird

	def call
		puts "boom, skreech"
	end

	def plumage
		puts "green speckled feathers with 'whiskers' on the face"
	end

	def fly
		false
	end
end
{% endhighlight %}

<strong> Polymorphism </strong>

Polymorphism comes from Greek, meaning "many forms". In Ruby it specifically means the ability to send the same message (through methods) to different objects and get different results. 

You might have noticed in the example above how each bird inherits from the class Bird, but each bird has a different output when asked for information about their call and plumage. All inherit the fly method unchanged, except the kakapo, a flightless parrot. 

In essence all birds inherit from the Bird class but each can modify the attributes it passes them to suit their specifications.

<strong> Encapsulation </strong>

Encapsulation is hiding implementation details of a class from other objects. In essence, the Birdwatching Club Director simply wants to identify birds, based on their appearance and call. We can pack all of the information that we need to identify a bird into a single component and hide how it works. This is important so that the function works as we expect, and others using our classes cannot mess how they work. We hide the internal data by making it `private`. Now the `identify` method can access its own data but another object using the method cannot. Encapsulation decreases complexity by ensuring the internal components of an object are hidden from the outside.

{% highlight ruby %}

class Kakapo < Bird

	def identify
		appearance
		call
	end

	private

	def appearance
		plumage = plumage
		beak = beak
		legs = legs
		puts "This bird has a #{beak} with #{legs} and #{plumage}."
	end

	def plumage
		puts "green speckled feathers with 'whiskers' on the face"
	end

	def beak
		puts "a large grey beak"
	end

	def legs
		puts "short legs with large feet"
	end

	def call
		puts "boom, skreech!"
	end

end
{% endhighlight %}

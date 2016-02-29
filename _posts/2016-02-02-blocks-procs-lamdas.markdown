---
layout: post
title: "Blocks, Procs and Lambdas"
date: 2016-02-02 12:30:30 +0000
---

<strong> What is a Block? </strong>

A block is a chunk of code that runs to produce an outcome. We have seen them a lot so far. A block is not a method, but can exist within one, or outside of it. A block is not an object either, an exception to Ruby's "Everything is an Object" rule. Yeah, they lied! Blocks can be identified by their syntax of `do...end` or are between curly braces `{}`. An example might be:

{% highlight ruby %}
10.times do
	puts "I am a block!"
end
{% endhighlight %}

So a block is not a method, but can be passed to one with the `#yield` method. This can be done like so:

{% highlight ruby %}
def harry_meet_sally
	puts "Hello I'm Harry, what's your name?"
	yield
end

harry_meet_sally { puts "Hello Harry, my name is Sally"}

#=> "Hello I'm Harry, what's your name?"
#=> "Hello Harry, my name is Sally"
{% endhighlight %}

The method there is called `harry_meet_sally` and exists between the `def` and `end`. The method is an object, and can be called again and again. The yield within the method is calling the block that exists outside of it. The `#yield` method can also be used with parameters, like so:

{% highlight ruby %}
def sally_gets_eaten(name)
	puts "Hello what's your name?"
	yield(name)
	yield("Sally")
	puts "GULP!"
end

sally_gets_eatern("Tahm Kench") { |n| puts "My name is #{n}." }

#=> "Hello what's your name?"
#=> "My name is Tahm Kench."
#=> "My name is Sally."
#=> "GULP!"
{% endhighlight %}

Notice here that when yield is called with the `name` parameter it finds `"Tahm Kench"` in the block and calls it within the message. Next yield is passed `"Sally"` which overrides `"Tahm Kench"`. 

<p align="center">
<img src="http://i.imgur.com/3nowvoF.jpg">
</p>


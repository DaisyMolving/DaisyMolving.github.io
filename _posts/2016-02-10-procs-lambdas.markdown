---
layout: post
comments: true
title: "Procs and Lambdas"
date: 2016-02-10 12:30:30 +0000
---

<strong> Procs </strong>

Blocks cannot be assigned to variables to be reused dynamically because they are not objects. If you want to store a block for repeated use, you can do this using a Proc.

Proc objects are blocks that have been assigned to a variables. Once assigned, the code may be called in different contexts again and again using those variables. Create a Proc by instantiating it with the `#new` method, and are then called using an ampersand (`&`).

{% highlight ruby %}

square_numbers = Proc.new do |n|
	n ** 2
end

[1, 2, 3].collect!(&square_numbers)

#=> [1, 4, 9]

[4, 5, 6].map!(&square_numbers)

#=> [16, 25, 36]
{% endhighlight %}

Procs are very useful because they help to keep your code DRY (Don't Repeat Yourself) and also have all the qualities of objects where blocks don't. Procs can be `yield`ed and `call`ed, like so:

{% highlight ruby %}
def banana
	yield
end

peel = Proc.new do
	puts "ready to eat!"
end

banana(&peel)

#=> "ready to eat!"
{% endhighlight %}
{% highlight ruby %}
def banana
	peel.call
end

peel = Proc.new do
	puts "ready to eat!"
end

#=> "ready to eat!"
{% endhighlight %}

<strong> Symbols as Procs </strong>

The ampersand can be used to convert a Symbol into a Proc. Ruby method names can be Symbols. This means we can use the ampersand to pass around methods! That is a bit cool, right? Check out this example to see how this works:

{% highlight ruby %}
numbers = [1, 2, 3, 4, 5]

strings = numbers.map!(&:to_s)

#=> ["1", "2", "3", "4", "5"]
{% endhighlight %}

<strong> Lambdas </strong>

A lambda belongs to the Proc class and so inherits all its methods, but has a few key differences. A lambda can be thought of as a method with no name, as it acts very much like a method. You see, where a Proc will run its code even if it holds an incorrect number of arguments (it just assigns `nil` to unaccountable ones), a lambda will throw an error. It checks the number of arguments for its parameters just like a method. The other difference is that when a lambda is returned it passes control back to the calling method, whereas when a proc is returned it behaves like it is part of the calling method itself and exists inside it. This will present itself like this:

{% highlight ruby %}

def show_lambda_result
	lambda { return "we just returned from the block" }.call
	return "we just returned from the calling method"
end

puts show_lambda_result
#=> "we just returned from the calling method"

def show_proc_result
	Proc.new { return "we just returned from the block" }.call
	return "we just returned from the calling method"
end

puts show_proc_result
#=> "we just returned from the block"
{% endhighlight %}

See how the lambda is called then passes control to the return within the method, whereas the Proc calls and returns so the following line is not returned.

<p align="center">
<img src="http://savethe80s.com/Articles/IC_awfulgenesis/DJWHOA.jpg">
</p>

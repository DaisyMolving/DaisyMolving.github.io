---
layout: post
title: "Procs and Lambdas"
date: 2016-02-03 12:30:30 +0000
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

<strong> Lambdas </strong>



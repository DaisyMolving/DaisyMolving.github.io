---
layout: post
title:  "Ruby Splat"
date:   2016-01-24 12:29:31 +0000
---

<strong> Splat! -> Collecting Remaining Arguments </strong>

The Ruby splat is represented by an asterisk (*) and marks a parameter that collects many arguments taken by a method. It is useful when a method will be passed several parameters or blocks and it would not be especially fun to write them all out. It is also great if you will be continually creating more blocks for the method to process. Here is a simple example:

{% highlight ruby %}

def predator(animal, *foods)
	foods.each do |food|
		puts "#{animal} predates #{food}"
	end
end

#now call it with several arguments

predator("Lion", "Zebra", "Antelope", "Buffalo")

#=> "Lion predates Zebra"
#=> "Lion predates Antelope"
#=> "Lion predates Buffalo"
{% endhighlight %}

So here you can see that `*foods` uses the splat operator and therefore stands in for `Zebra`, `Antelope` and `Buffalo`, while `animal` stands only for the first argument that the `predator` method takes, `Lion`. The splat helps us to pass the method several arguments without having to put these arguments inside an array. You can see that the splat treats the remaining arguments as though they really are arguments and for this reason splats can also be used for...

<strong> ...Creating Arrays </strong>

The splat operator can be used as a shortcut to making a range into an array, instead of using `.to_a`, like so:

{% highlight ruby %}
array_of_numbers = *1..10

print array_of_numbers
#=1 [1, 2, 3, 4, 5, 6, 7, 8, 9, 10]
{% endhighlight %}

<strong> Flattening Arrays </strong>

Splat operators also allow us to flatten arrays. This can be done in the following way:

{% highlight ruby %}

first_array = [7, 16, 23, 1]

second_array = [*first_array, 56, 2, 9]

print second_array

#=> [7, 16, 23, 1, 56, 2, 9]
{% endhighlight %}

Here the splat is telling the second_array to access and insert every element within first_array.

<strong> Coverting Hashes to Arrays </strong>

Another use for the splat is to convert a Hash into an Array. This is simply done like so:

{% highlight ruby %}

hash_to_array = *{"hello" => "this", "look" => "that"}

print hash_to_array

#=> [["hello", "this"], ["look", "that"]]
{% endhighlight %}

<p align="center">
<iframe src="//giphy.com/embed/acj7QJGgBBeUg" width="240" height="180" frameBorder="0" class="giphy-embed" allowFullScreen></iframe></p>

<strong> Beware </strong>

By far the best use of a splat is when we want to collect remaining arguments to be passed to a method. This will be very helpful in many situations. However the other uses shown here should be used with caution, because while `*` can essentially stand in to `to.a`, `.to_a` has the safety of only achieving one goal and so does not make your code any more complex or confused when adding extra functionality.


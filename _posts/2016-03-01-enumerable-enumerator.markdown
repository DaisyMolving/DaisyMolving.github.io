---
layout: post
comments: true
title: "Enumerable Module"
date: 2016-03-01 12:30:30 +0000
---

A module that we have used many times before is the `Enumerable` module. It is a collection of iterative methods, and is included in the `Hash` and `Array` classes. Enumerable methods give us a more concise way of iterating over elements in a collection than a `for` loop, and also provide us with many useful operations. 

Let's have a look at a few of these enumerable methods.

<strong> Each and Map </strong>

`#each` is a method that iteratates over each element in an array, running the block for every element and returns the original elements that it was called upon. For example:

{% highlight ruby %}
["a", "b", "c"].each do |element|
	element + "a"
end

#=> ["a", "b", "c"]
{% endhighlight %}

In order to get a return of the `abc` string array as changed by the expression within the block, a new empty array would have to be declared, the changed elements shovelled into it, and the new array returned OR `#map` could be used. `#map` sets the current element in the iteration to the return value of the block, and returns the changed element. For example:

{% highlight ruby %}
["a", "b", "c"].map do |element|
	element + "a"
end

#=> ["aa", "ba", "ca"]
{% endhighlight %}

Here you can see how the method "maps" each element to a new state.

<strong> Select and Reject </strong>

Select iterates over a list of elements and returns a new list where the elements fit a certain criterium, or certain criteria, that it was passed. For instance, if we want to find and return numbers in an array that are divisible by three, we could use `#select` like so:

{% highlight ruby %}
numbers = [1, 4, 5, 3, 6, 10, 57, 48, 9, 11, 20, 21]

numbers.select do |element|
	element % 3 == 0
end

#=> [3, 6, 48, 9, 21]
{% endhighlight %}

When we want to do the opposite, and return elements that <i>don't</i> fit the criterium of being divisible by three, we can instead use `#reject`. For example:

{% highlight ruby %}
numbers = [1, 4, 5, 3, 6, 10, 57, 48, 9, 11, 20, 21]

numbers.reject do |element|
	element % 3 == 0
end

#=> [1, 4, 5, 10, 57, 11, 20]
{% endhighlight %}
<strong> Inject </strong>

`#inject` iterates over elements and runs a block where element `a` interacts with the next element `b`, the result of which interacts in the same way with element `c`. This is particularly useful when you want to sum elements within an array, like so:

{% highlight ruby %}
array = [1, 2, 3, 4]

array.inject do |result, element|
	result + element
end

#=> 10
{% endhighlight %}

What inject is doing here is this:

{% highlight ruby %}
array = [1, 2, 3, 4]

array.inject do |result, element|
	result + element
end

# inject iterates over first element of array, names this "result" 
# and adds it to next element of the array, which is calls "element".

	 array = [1, 2, 3, 4]
	 array = [result, element, 3, 4]
	 array = [result + element, 3, 4]
	 array = [1 + 2, 3, 4]
	 1 + 2 = 3
	 array = [3, 3, 4]

# so now, as result has been added to element the array is changed, 
# and it iterates over the next element with the same process:

	 array = [3, 3, 4]
	 array = [result, element, 4]
	 array = [result + element, 4]
	 array = [3 + 3, 4]
	 3 + 3 = 6
	 array = [6, 4]

# and continues...

	 array = [6, 4]
	 array = [result, element]
	 array = [result + element]
	 array = [6 + 4]
	 6 + 4 = 10
	 array = [10]

# inject returns result
#=> 10
{% endhighlight %}

Of course, another way to look at what `#inject` essentially did, was that it put a `+` in between every element and then returned the result. It <i>injects</i> every element with addition. So naturally, Ruby has a nice way to call `#inject` more concisely, like so:

{% highlight ruby %}
array = [1, 2, 3, 4]

array.inject(:+)

#=> 10
{% endhighlight %}

<strong> Enumerators </strong>

An `Enumerator` is another Ruby class that uses the `Enumerable` module. `Enumerable` is the collection of methods that iterate over elements, it is the collection of iterative processes. Therefore an `Enumerator` can be thought of as an object form of `Enumerable`, a tool that performs iteration. `Enumerator` is a class, and can therefore be instantiated. If you use an `Enumerable` method on an Array or Hash without passing it a block, an instance of `Enumerator` will be created. Then you can cycle through the Array or Hash using the `Enumerator` method `#next`, like so:

{% highlight ruby %}
hash = { a: 1, b: 2, c: 3 }

new_enumerator = hash.each
#=> #<Enumerator: {:a=>1, :b=>2, :c=>3}:each>

new_enumerator.next
#=> [:a, 1]

new_enumerator.next
#=> [:b, 2]

new_enumerator.next
#=> [:c, 3]

new_enumerator.next
#=> StopIteration: iteration reached an end
{% endhighlight %}

If you would like more explanation about this, Avdi Grimm's Ruby Tapas episode for [Enumerator][enumerator-ruby-tapas] provides an excellent video tutorial.

[enumerator-ruby-tapas]: http://www.rubytapas.com/episodes/59-Enumerator

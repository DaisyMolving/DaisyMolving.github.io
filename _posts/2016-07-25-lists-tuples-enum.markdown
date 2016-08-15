---
layout: post
comments: true
title: "Elixir: Lists, Tuples and Enum"
date: 2016-07-25 12:00:30 +0000
---

Elixir has many collection types, and two of these are lists and tuples. Lists look similar to arrays in Ruby, but there are some important differences. Elixir also ahs an enum module, which contains more functions which can be used to iterating over these collections.

<strong>Lists</strong>

A list is a collection of items, notated between square brackets and separated by commas. Lists can store anything, like so:

`i_can_store_anything = ["hello", :something, 100, [1, 2, 3]]`

Lists can be added together using `++`, or items removed using `--` like so:

{% highlight elixir %}
iex> 	even_digits = [0, 2, 4, 6, 8]
#=> [0, 2, 4, 6, 8]

iex> 	odd_digits = [1, 3, 5, 7, 9]
#=> [1, 3, 5, 7, 9]

iex> 	all_digits = even_digits ++ odd_digits
#=> [0, 2, 4, 6, 8, 1, 3, 5, 7, 9]

iex> 	digits_without_multiples_of_three = all_digits -- [3, 6, 9]
#=> [0, 2, 4, 8, 1, 5, 7]
{% endhighlight %}

<strong>List Functions</strong>

List functions can be used upon lists as you might usually think of them (`[:this, :is, :a, :list]`) as well as upon charlists (`'hello'`). For instance, using the `List.first` function:

{% highlight elixir %}
iex> List.first([7, 3, 2, 5, 1])
#=> 7

iex> List.first('hello there')
#=> 'h'
{% endhighlight %}

This is true for all list methods, as well as when using `++` and `--` as above. Here are some more examples of list methods:

{% highlight elixir %}
iex> List.last([7, 3, 2, 5, 1])
#=> 1
{% endhighlight %}

The delete method will remove a specified element. However, if there is more than one instance of the specified element only the first found will be deleted.
{% highlight elixir %}
iex> List.delete([7, 3, 2, 5, 1], 2)
#=> [7, 3, 5, 1]

iex> List.delete([:bee, :bee, :mosquito:, :bee, :mosquito], :mosquito)
#=> [:bee, :bee, :bee, :mosquito]
{% endhighlight %}

{% highlight elixir %}
iex> List.delete_at([7, 3, 2, 5, 1], 1)
#=> [7, 2, 5, 1]

iex> List.delete_at([7, 3, 2, 5, 1], -1)
#=> [7, 3, 2, 5]
{% endhighlight %}

{% highlight elixir %}
iex> List.duplicate("more!", 4)
#=>["more!", "more!", "more!", "more!"]  
{% endhighlight %}

{% highlight elixir %}
iex> List.flatten([[7, 3], [[2, 5], 1]])
#=> [7, 3, 2, 5, 1]
{% endhighlight %}

{% highlight elixir %}
iex> List.insert_at(["i", "love", "spiders"], 1, "don't")
#=> ["i", "don't", "love", "spiders"]
{% endhighlight %}

{% highlight elixir %}
iex> List.replace_at(["i", "love", "spiders"], 1, "dislike")
#=> ["i", "dislike", "spiders"]

iex> List.replace_at(["i", "love", "spiders"], -1, "ice cream")
#=> ["i", "love", "ice cream"]
{% endhighlight %}

{% highlight elixir %}
iex> List.wrap(100)
#=> [100]
{% endhighlight %}

{% highlight elixir %}
iex> List.to_tuple([:am, "i", "a tuple", :yet?])
#=> {:am, "i", "a tuple", :yet?}
{% endhighlight %}

<strong>Tuples</strong>

Tuples are very similar to lists in a lot of ways, in that they store values as collections in memory. However they do that in a different way, and for this reason have some different functions. Finding the size of a tuple, returning an element at a given position and replacing elements is very simple, due to how tuples are stored <i>contiguously</i>. 

{% highlight elixir %}
iex> tuple_size({:hi, 1, 2, "three"})
#=> 4
{% endhighlight %}

{% highlight elixir %}
iex> elem({3, 7, 4, 1}, 1)
#=> 7
{% endhighlight %}

{% highlight elixir %}
iex> put_elem({3, 7, 4, 1}, 1, 20)
#=> {3, 20, 4, 1} 
{% endhighlight %}

What does it mean for something to be stored contiguously? It refers to the way in which elements are stored as part of the unit that is array, tuple or linked list. Depending on what data type it is, a collection can take up more or less memory, but this gives it certain advantages or disadvantages for actions that are called upon it. You can learn more about how this works in [this post][linked-lists-tuples-explained].

<strong>Enum</strong>

The Enum module is a collection of functions that can be used on Lists. Some of these require an inner function to be written to indicate how the Enum function is to be used, such as with `map`, `find_index`, `any?` and `reduce`. Below are some examples:


{% highlight elixir %}
iex> Enum.count([1, 6, 2, 7, 18, 3, 4])
#=> 7
{% endhighlight %}

{% highlight elixir %}
iex> Enum.member?([73, 8, 20, 1, -300], 1)
#=> true
{% endhighlight %}

{% highlight elixir %}
iex> Enum.sort([4, 7, 8, 3, 5, 2, 6, 1])
#=> [1, 2, 3, 4, 5, 6, 7, 8]
{% endhighlight %}

{% highlight elixir %}
iex> Enum.uniq([1, 2, 2, 2, 2, 2, 2, 2, 3, 3, 4, 3, 4, 3, 5])
#=> [1, 2, 3, 4, 5]
{% endhighlight %}

{% highlight elixir %}
iex> Enum.all?([1, 2, 3, 4], fn(x) -> rem(x, 2) == 0 end)
#=> false
{% endhighlight %}

{% highlight elixir %}
iex> Enum.any?([1, 2, 3, 4], fn(x) -> rem(x, 2) == 0 end)
#=> true
{% endhighlight %}

{% highlight elixir %}
iex> Enum.find_index([1, 2, 3, 4], fn(x) -> x == 2 end)
#=> 1
{% endhighlight %}

{% highlight elixir %}
iex> Enum.reduce([1, 2, 3, 4], fn(x, y) -> x * y end)
#=> 24
{% endhighlight %}

{% highlight elixir %}
iex> Enum.map([1, 2, 3, 4], fn(x) -> x * 2 end)
#=> [2, 4, 6, 8]
{% endhighlight %}

[linked-lists-tuples-explained]:http://daisymolving.github.io/2016/08/01/linked-list-vs-tuples-and-arrays.html

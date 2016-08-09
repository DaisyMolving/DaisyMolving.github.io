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

What does it mean for something to be stored contiguously? It refers to the way in which elements are stored as part of the unit that is array, tuple or linked list. Depending on what data type it is, a collection can take up more or less memory, but this gives it certain advantages or disadvantages for actions that are called upon it. 

<strong>Linked Lists vs Arrays and Tuples</strong>

Your computer's memory can be thought of as a series of sections, each with a storage capacity, at a certain position. If we had a tuple `{1, 2, 3}` to store in memory it would be stored contiguously. This means all its elements would be stored in order right next to each other, like they are in the diagram below. This is useful when we need to access an element, because it can easily be found. A tuple's size is fixed upon it's creation. This means that we know how many elements there are in the collection at all times. When accessing elements we can find them with a simple equation, using the first position of the tuple and adding to it the number of elements to traverse multiplied by their size. 

<p align="center">
<img src="../../../../../../../assets/array_tuple_in_memory.png">
</p>

For instance the tuple above has 5 integers, each taking up 3 bytes of memory. To find the element at the index `3`, we would multiply that index number by the amount of bytes of memory needed to reach that position (3) and add that to the first position.

`3 * 3 + 100 = 109`

Now we can access the element at position 109 easily. Look again at the functions that the Tuple module uses. They are involved with finding elements in this way, and also replacing them. Finding the `tuple_size` is also simple, because of the fact that tuples are a fixed size upon creation. Recalling this information is instant.

There are some disadvantages to storing collections contiguously also. One of these is when we want to add an element to a tuple. Because tuples are a fixed size upon creation we cannot simply expand them to insert a new element into them. The tuple has to be copied to a new location with the new element where there is enough space to hold the entire collection contiguously again. This means that this type of operation is not instant, rather it takes as much time as moving each element, a linear function. 

<p align="center">
<img src="../../../../../../../assets/moving_resizing_array_tuple.png">
</p>

This can cause memory wasteage as well as less efficient functions. In the above diagram the dark blue space represents memory that used by other mystery data types and the new tuple to be created in a new location. As you can see we added `72` here to the 2nd index position of the tuple `{13, 4, 8, 2, 56}`.

Lists in Elixir are a data type called linked lists. They are not stored contiguously like tuples or arrays in ruby. In a linked list each element has its value as well as a pointer to the location of the next element. This means that when adding or removing elements we need only to change where the pointers are pointing, and any new elements can be stored absolutely anywhere in the computer memory. Linked lists use memory efficiently as well as allowing for instant additions and removals, however they do not allow for instant recall of elements at individual positions.

<p align="center">
<img src="../../../../../../../assets/linked_list.png">
</p>

This is because to find the element at a particular index we must follow each pointer and look at each element along our way to it. This means that finding elements is not a constant operation, rather a linear function.

Deciding whether to use a tuple or a list in your algorithm or program may be important when considering what you need to be doing. If you need to collect data that is constantly needing to be added to, then a list may be best. If you need to input data only once upon creation, but will need to access it constantly, then a tuple will be more efficient.

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


---
layout: post
comments: true
published: false
title: "Elixir: Keyword Lists, Maps and Map Sets"
date: 2016-08-02 10:30:30 +0000
---

Keyword Lists and Maps are associative data structures, which means that they contain values that are assigned to keys. This would make them similar to a hash in Ruby. This is useful to return a value by accessing its key. 

<strong>Keyword Lists</strong>

Keyword lists contain key-value pairs inside square brackets, like an Elixir linked-list. The key-value pairs inside a linked list can be thought of as 2-item tuples. Here is an example:

{% highlight elixir %}
#a keyword list
iex> pets_of_sally = [cats: 3, dogs: 1, tortoises: 2, iguana: 1]
{% endhighlight %}

To access a value we can simply:

{% highlight elixir %}
iex> pets_of_sally[:tortoises] 
#=> 2
{% endhighlight %}

Because keyword lists are essentially list that contain 2-item tuples, where the key is an atom and the value is a different data-type, they can also be written as:

{% highlight elixir %}
iex> pets_of_sally = [{:cats, 3}, {:dogs, 1}, {:tortoises, 2}, {:iguana, 1}]
#=> [cats: 3, dogs: 1, tortoises: 2, iguana: 1]

iex> pets_of_sally == [cats: 3, dogs: 1, tortoises: 2, iguana: 1]
#=> true
{% endhighlight %}

It is possible to have a keyword list with repeated keys, however only the first can be accessed. For example, if Sally's `:dogs` key is repeated:

{% highlight elixir %}
iex> pets_of_sally == [cats: 3, dogs: 1, tortoises: 2, iguana: 1, dogs: 2]
#=> [cats: 3, dogs: 1, tortoises: 2, iguana: 1, dogs: 2]

iex> pets_of_sally[:dogs]
#=> 1
{% endhighlight %}

Also, remembering [how linked lists work][linked-lists-post], and knowing that keyword lists have the same structure, we know that keyword lists will have an order that is set by the developer, and finding values by their key occurs in a linear fashion. It is therefore not an instant recall. 

<strong>Maps</strong>

<strong>Map Sets</strong>

[linked-lists-post]:

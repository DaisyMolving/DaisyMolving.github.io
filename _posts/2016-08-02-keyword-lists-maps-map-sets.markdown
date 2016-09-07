---
layout: post
comments: true
title: "Elixir: Keyword Lists and Maps"
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

<strong>Using Keyword Lists as Functions</strong>

Keyword lists are very convenient for use as function options. A function whose option is the key of the keyword list can store a boolean value that will cause the function to be called or not. For instance:

{% highlight elixir %}
double_up = fn(str, opts) -> 
  if opts[:duplicate] do
    String.duplicate(str, 2)
  else
    str
  end
end

iex> double_up.("double", duplicate: true)
#=> "doubledouble"

iex> double_up.("trouble", duplicate: false)
#=> "trouble"
{% endhighlight %}

<strong>Maps</strong>

A map is another associative data structure, and they use curly braces preceded by a percentage sign, like so:

{% highlight elixir %}
iex> my_map = %{:key_one => "value_one", :key_two => "value_two"}
#=> 2
{% endhighlight %}

Maps represent structured data. It is useful for representing a collection of attributes relating to an object, like a person. For example:

{% highlight elixir %}
iex> @person == %{first_name: "Wednesday",
    second_name: "Addams",
    age: 6, 
    pets: "Homer the Spider"}
#=> %{first_name: "Wednesday", second_name: "Addams", age: 6, pets: "Homer the Spider"}
{% endhighlight %}


[linked-lists-post]:http://daisymolving.github.io/2016/08/01/linked-list-vs-tuples-and-arrays.html

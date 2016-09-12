---
layout: post
comments: true
title: "Elixir: Pattern Matching and Operators"
date: 2016-08-05 10:30:30 +0000
---

In Elixir the `=` symbol is not for assignment but used as a symbol for pattern-matching. This means that when a variable name is matched to some data it can be rematched, just like in other languages variables are reassigned, but there are some differences. For example:

{% highlight elixir %}

iex> a = "hello"
#=> "hello"

iex> b = "goodbye"
#=> "goodbye"

iex> a = b
#=> "goodbye"

iex> a
#=> "goodbye"

iex> "goodbye" = a
#=> "goodbye"

iex> "caramel" = b
#=> ** (MatchError) no match of right hand side value: "goodbye"

{% endhighlight %}

As you can see in the last two examples, this is not assignment. Assignment would throw an error for expression `"goodbye" = a`, because it would instead expect an expression of equality, such as `"goodbye" == a` (returning a boolean). However with Elixir's pattern-matching it is checking that the right and left-hand sides are the same. It is only when they are not that an error is raised, because `"caramel"` does not match `"goodbye"`.

<strong>Pattern-matching on Collections</strong>

Collections can be pattern matched on using a pipe operator, like so:

{% highlight elixir %}
iex> list_of_numbers = [1, 2, 3, 4, 5]
#=> [1, 2, 3, 4, 5]

iex> [ first_element | remaining_elements ] = list_of_numbers
#=> [1, 2, 3, 4, 5]

iex> first_element
#=> 1

iex> remaining_elements
#=> [2, 3, 4, 5]
{% endhighlight %}

The pipe operator, or `|`, is splitting the first element of a list with the remaining elements. This is because an Elixir list is a [linked-list][linked_list_post], and so `[1, 2, 3]` can be thought of as `[1 | [2 | [3]]]`. Therefore we could also use a pipe operator like so:

{% highlight elixir %}
iex> list_of_numbers = [1, 2, 3, 4, 5]
#=> [1, 2, 3, 4, 5]

iex> [ first, second | remaining ] = list_of_numbers
#=> [1, 2, 3, 4, 5]

iex> first
#=> 1

iex> second
#=> 2

iex> remaining
#=> [3, 4, 5]
{% endhighlight %}

In the same way a list of tuples can be pattern-matched like so:

{% highlight elixir %}
iex> list_of_tuples = [{"one", 1}, {"two", 2}, {"three", 3}]
#=> [{"one", 1}, {"two", 2}, {"three", 3}]

iex> [{word, digit} | remaining_tuples] = list_of_tuples
#=> [{"one", 1}, {"two", 2}, {"three", 3}]

iex> word
#=> "one"

iex> digit
#=> 1

iex> remaining_tuples
#=> [{"two", 2}, {"three", 3}]

iex> { word, digit }
#=> {"one", 1}
{% endhighlight %}

<strong>Pattern-matching Arguments</strong>

Pattern-matching is very useful in recursion because arguments can be matched again and again. For instance, if we wanted to iterate over a list of elements we could continuously recurse over the remaining elements, which would grow smaller each time. Here is an example:

{% highlight elixir %}
defmodule Summation do

  def sum([]), do: 0
  def sum([current_number | remaining_numbers]) do
    current_number + sum(remaining_numbers)
  end

end
{% endhighlight %}

When `sum` is called with a list of numbers, it splits the list into `current_number` and the `remaining_numbers`. It adds the `current_number` to the recursive call of the `sum` function on the `remaining_numbers`. When it is called recursively the `remaining_numbers` is treated as a new list to be split into an updated `current_number` and an updated `remaining_numbers`. This continues until the list is empty i.e. there are no more numbers to recurse over. In this case it matches the function `def sum([]), do: 0`. That is, when the list is empty, `[]`, return `0` to be added to the final sum.

Here we can see how pattern-matching was useful for splitting the current number to be added from the remaining numbers in the list, <i>and</i> how pattern-matching was useful in setting a base case so that when the list matched an empty list the recursion ends.

[linked_list_post]:http://daisymolving.github.io/2016/08/01/linked-list-vs-tuples-and-arrays.html

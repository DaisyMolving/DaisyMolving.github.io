---
layout: post
comments: true
title: "Elixir: Understanding Recursion"
date: 2016-07-13 12:30:30 +0000
---

Functional Programming languages write loops in a different way to other languages, they use recursion. Recursion is when a function is called recursively inside itself. This means that the function will be called again and again until certain criteria are reached to make it break. Functional languages use recursion because they cannot mutate elements or types like other languages. 

In Ruby we could write a loop like so:

{% highlight ruby %}

def repeat_greeting(greeting, num_of_repeats)
    while num_of_repeats > 0 do
        puts greeting
        num_of_repeats -= 1
    end
end

repeat_greeting("Hey there!", 3)
#=> "Hey there!"
#=> "Hey there!"
#=> "Hey there!"
{% endhighlight %}

However in Elixir, using recursion, the same function would look like this:

{% highlight elixir %}
defmodule Recursion do
    def repeat_greeting(greeting, num_of_repeats) when num_of_repeats <= 1 do
        IO.puts greeting
    end

    def repeat_greeting(greeting, num_of_repeats) do
        IO.puts greeting
        repeat_greeting(greeting, num_of_repeats - 1)
    end
end

Recursion.repeat_greeting("Hey there!", 3)
#=> "Hey there!"
#=> "Hey there!"
#=> "Hey there!"
{% endhighlight %}

_jekk

<strong>What is it Doing?</strong>

When `3` is passed in as the `num_of_repeats`, the first `repeat_greeting` function is checked. But wait! It will only be called if the `when` condition is true, that `3 <= 0`. Because that statement is not true, the next `repeat_greeting` function is called. It puts the `greeting`, which was passed in as `"Hey there!"`. It then calls the `repeat_greeting` function again <i>recursively</i>, this time with `1` subtracted from the `num_of_repeats`. It checks the first, conditional, `repeat_greeting` function, this time with the `num_of_repeats` being `2`. Again, the criteria is not met. It will call the second function, and again puts `"Hey there!"`. And so on, until `num_of_repeats` reaches `1`, meeting the conditional function.

<strong>Recursion in the Roman Numerals Kata</strong>

Below is an example of how recursion could be used in the Roman Numerals Kata, for the arabic numbers 1, 2, 3 only. The `convert(arabic` function is being called in the tests with an arabic number as the argument. This function checks the second `convert` function to meet the condition, and if it does not, the third `convert` function is called. This third function calls `convert` recursively, subtracts `1` from the `arabic` number and stores the `roman` argument as a list to which a single `"i"` is added at the last position. It checks the conditional `convert` function and continues to recur until the conditional statement is `true`. When this happens it joins the list that is matched to `roman` and returns a string - the roman numeral!

<p align="center">
<img src="../../../../../../../assets/recursion_elixir_roman_nums.png">
</p>

Phew.

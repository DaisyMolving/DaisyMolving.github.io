---
layout: post
comments: true
title:  "Odin and Ruby"
date:   2016-01-16 12:29:31 +0000
---

As part of the plan for learning with Cedric I am working through The Odin Project, specifically the section on [Ruby Programming][odin-ruby-programming-overview]. The Odin Project aims to give people to tools to become web developers and enter the tech industry, and its free. 

There is also a more involved programme with mentorship available, where the fee is a percentage of your income on your first year of industry work. But I am just picking and choosing what I need from their [beta][odin-project-home] site. It is worth a read through to see what might be relevant to you, and some of the great resources they provide.

In Odin's Ruby Programming section it is suggested to undertake Codecademy's [Ruby exercises][codecademy-intro-ruby] along with tutorials, quizzes, articles and excerpts from Ruby lit-er-a-ture, but I will let you read through it.

Hey, wanna know some things I did today?

<strong>Integers and Floats</strong>

Integers and Floats both belong to the Numeric class, but an Integer is a fixed whole number where a Float is a decimal number. For instance `6` and `6.0` are equal but the first is an Integer and the second is a Float. 

If a Float exists within an equation, the equation will always evaluate to a Float. For instance, `4.0 / 2 = 2.0` and `5 / 2.0 = 2.5`. In both these examples at least one of the numbers in the equation is a Float and so they both evaluate to Floats.

If there are solely Integers as elements in the equation, the equation will always have an Integer conclusion, so `4 / 2 = 2` but also, strangely, `5 / 2 = 2`. Of course the second equation does not give us the answer that we would expect. For this reason Floats can be incredibly useful to give us accurate mathematical evaluations, but Integers are useful to give us answers that have material applications such as the amount of likely guests attending an event (where, hopefully, there are only whole-guests and not decimal ones).

<strong>Equals Does Not Always Equal Equals?</strong>

The difference between `=`, `==` and `===`:

`=` is used to assign a variable. It is the assignment operator.
For instance, `this_variable = 20`

`==` is used to check equality.
For instance, {% highlight ruby %}
def variable_value
  puts "It really is 20!" if this_variable == 20
end
{% endhighlight %}

and

`===` is used to check case equality, it checks whether the value on the right belongs to the thing on the left and returns a boolean value.
For instance, `Integer === 3` evaluates to `true`.

<strong>Ranges</strong>


A Range is a collection of consecutive numbers, or a collection of consecutive letters, between two points. For instance the Range `1..3` contains the numbers from `1` to, and including, `3`. It is `1, 2, 3`. The Range `"a".."e"` contains the letters from `"a"` to, and including, `"e"`. It is `("a", "b", "c", "d", "e")`.


A Range can be created in two ways. One way is to use the `..` and `...` literals between two points, and the other by declaring a new instance of the class Range. For instance:

`this_new_range = 1...7`

`that_new_range = Range.new`


The `..` literal denotes a Range that encompasses its first element, travelling consecutively towards, and <strong>including</strong>, its second element, whereas the `...` literal denotes a Range that encompasses its first element, travelling consecutively towards, and <strong>excluding</strong>, its second element.


[odin-ruby-programming-overview]: http://www.theodinproject.com/ruby-programming
[odin-project-home]: http://www.theodinproject.com/home
[codecademy-intro-ruby]: https://www.codecademy.com/learn/ruby

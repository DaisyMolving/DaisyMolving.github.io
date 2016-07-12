---
layout: post
comments: true
title: "Elixir: Integers, Floats, Operators and Arithmetic"
date: 2016-07-11 12:00:30 +0000
---

Integers and Floats are types of number that are used in Elixir. Integers are whole numbers, whereas Floats are floating point numbers, they have a decimal point value. For instance, `5` is an Integer, `5.0` is a Float. In order to check, Elixir provides `is_integer()` and `is_float()` methods. They are used like so:

{% highlight elixir %}
is_integer(20)
#=> true

is_float(5)
#=> false

is_integer("int")
#=> false

is_float(6.789)
#=> true
{% endhighlight %}

<strong>Integer and Float Methods</strong>

Some more Integer and Float methods, and how they behave:

{% highlight elixir %}
require Integer

Integer.is_odd(3)
#=> true

Integer.is_even(3)
#=> false

Integer.digits(12345)
#=> [1, 2, 3, 4, 5]

Integer.undigits([6, 7, 8, 9, 0])
#=> 67890

Integer.to_char_list(1357)
#=> '1357'

Float.to_char_list(3.57)
#=> '3.57'

Integer.to_string(1337)
#=>"1337"

Float.to_string(808.3773)
#=>"808.3773"

Float.ceil(13.2)
#=> 14

Float.floor(3.7)
#=> 3

Float.round(7.5)
#=> 8

Float.round(7.4)
#=> 7
{% endhighlight %}

<strong>Parsing</strong>

The parse method ( `.parse()` ) runs the argument against the preceding module and returns the argument as an instance of that module (if it can find one, otherwise it presents an `:error`), followed by the 'leftovers'. For instance if an Integer is parsed with an argument of `"45Z"`, the `45` is converted into an integer and the `"Z"` is returned, remaining a string. 

The return would look like `{45, "Z"}`, a tuple. Here are some more examples of how Integers and Floats act when parsed:

{% highlight elixir %}
Integer.parse("1")
#=> {1, ""}

Integer.parse("76W")
#=> {76, "W"}

Integer.parse("2349")
#=> {2349, ""}

Float.parse("3.4E")
#=> {3.4, "E"}

Float.parse("DAISY")
#=> :error

Integer.parse("3.5")
#=> {3, ".5"}
{% endhighlight %}

<strong>== and ===</strong>

`==` is used for equivalence, as we have seen before. `5` and `5.0` are the same amount, and so `5 == 5.0 == true`. However `5` and `5.0` are not the same <i>thing</i>, as one is an integer and one is a float, and so there is `===`, the case operator. With the case operator `5 === 5.0 == false`.

<strong>Basic Arithmetic</strong>

Elixir provides operators for basic arithmetic. It is easy as `1 + 2 == 3`. Here are the basic operators for this:

<div align="center" style="margin-bottom: 30px;">
<table style="border-spacing: 0px; border: #111162 solid 2px;">
<tr>
<td style="width: 200px; padding: 10px; border: #111162 solid 1px; margin: 0px; color: #111162; background-color: #eeeeff">arithmetic operator</td>
<td style="padding: 10px; border: #111162 solid 1px; margin: 0px; color: #111162; background-color: #eeeeff">means:</td>
</tr>
<tr>
<td style="padding: 10px; border: #111162 solid 1px; margin: 0px;">+</td>
<td style="padding: 10px; border: #111162 solid 1px; margin: 0px;">adds</td>
</tr>
<tr>
<td style="padding: 10px; border: #111162 solid 1px; margin: 0px;">-</td>
<td style="padding: 10px; border: #111162 solid 1px; margin: 0px;">subtracts</td>
</tr>
<tr>
<td style="padding: 10px; border: #111162 solid 1px; margin: 0px;">*</td>
<td style="padding: 10px; border: #111162 solid 1px; margin: 0px;">multiplies</td>
</tr>
<tr>
<td style="padding: 10px; border: #111162 solid 1px; margin: 0px;">/</td>
<td style="padding: 10px; border: #111162 solid 1px; margin: 0px;">divides, always returns a float</td>
</tr>
<tr>
<td style="padding: 10px; border: #111162 solid 1px; margin: 0px;">div</td>
<td style="padding: 10px; border: #111162 solid 1px; margin: 0px;">divides, returns a whole number without any remainder</td>
</tr>
<tr>
<td style="padding: 10px; border: #111162 solid 1px; margin: 0px;">rem</td>
<td style="padding: 10px; border: #111162 solid 1px; margin: 0px;">remainder, this returns a value that is the remainder when one number is divided by another</td>
</tr>
</table>
</div>

When using `div` and `rem` the syntax is different to using the other operators. Creating an expression with these operators looks like so:

{% highlight elixir %}
div 10, 3
#=> 3

rem 10, 3
#=> 1
{% endhighlight %}

<div align="center" style="margin-bottom: 30px;">
<table style="border-spacing: 0px; border: #111162 solid 2px;">
<tr>
<td style="width: 200px; padding: 10px; border: #111162 solid 1px; margin: 0px; color: #111162; background-color: #EEEEFF">Comparison Operator</td>
<td style="width: 500px; padding: 10px; border: #111162 solid 1px; margin: 0px; color: #111162; background-color: #EEEEFF">Means:</td>
</tr>
<tr>
<td style="padding: 10px; border: #111162 solid 1px; margin: 0px;">==</td>
<td style="padding: 10px; border: #111162 solid 1px; margin: 0px;">Is equal to</td>
</tr>
<tr>
<td style="padding: 10px; border: #111162 solid 1px; margin: 0px;">!=</td>
<td style="padding: 10px; border: #111162 solid 1px; margin: 0px;">Is not equal to</td>
</tr>
<tr>
<td style="padding: 10px; border: #111162 solid 1px; margin: 0px;">></td>
<td style="padding: 10px; border: #111162 solid 1px; margin: 0px;">Greater than</td>
</tr>
<tr>
<td style="padding: 10px; border: #111162 solid 1px; margin: 0px;"><</td>
<td style="padding: 10px; border: #111162 solid 1px; margin: 0px;">Less than</td>
</tr>
<tr>
<td style="padding: 10px; border: #111162 solid 1px; margin: 0px;">>=</td>
<td style="padding: 10px; border: #111162 solid 1px; margin: 0px;">Greater than or equal to</td>
</tr>
<tr>
<td style="padding: 10px; border: #111162 solid 1px; margin: 0px;"><=</td>
<td style="padding: 10px; border: #111162 solid 1px; margin: 0px;">Less than or equal to</td>
</tr>
</table>
</div>
																				  
Here we can see that the `!` acts as a negating character, and basically says 'is not' to the operator that it sits with. For instance `!>` would be the same as putting `<`. The comparison operators can also be used to compare data types. For instance:

{% highlight elixir %}
1 < :atom
#=> true

"string" == :atom
#=> false

Integer < String  
#=> true
{% endhighlight %}

---
layout: post
comments: true
title: "Elixir: Booleans, Strings, Chars, Atoms and Sigils"
date: 2016-07-08 12:30:30 +0000
---

Elixir has some of the same data-types as Ruby, and many different ones. The basic types are integers, floats, booleans, strings, atoms, lists and tuples. In this post we are going to look at Boolean values, Strings, Chars and Atoms, as well as Sigils. 

<strong>Boolean Values</strong>

Boolean values are `true` and `false`. To figure out if a value is Boolean, Elixir provides the method `is_boolean()`:

{% highlight elixir %}
is_boolean(false)
#=> true

is_boolean("hello")
#=> false
{% endhighlight %}

As in Ruby, Elixir uses `||`, `&&` and `!` as symbols for `or`, `and` and `not`. It is also possibly to use the words `and` and `or` instead of the symbols. `==` is used for equivalence. Remember that in a logic statement using an `or`, only one side of the expression has to be true for it to evaluate to true, whereas an `and` logic statement must be true on both sides of the expression.

{%highlight elixir %}
true || false == true
#=> true

true && false == true
#=> false

true and true == true
#=> true

false or false == true
#=> false

!(false) || false == true
#=> true
{% endhighlight %}

<strong>Strings and Chars</strong>

Strings in Elixir must be inside double quotes ( `"goblin"` ), because single quotes denote Chars( `'a'` ), or Char Lists( `'ace'` ). A Char, or character, can only contain one element. A Char can be a symbol, number or letter. Char Lists are collections of Chars.

<strong>String Methods</strong>

Let's take a look at a few String methods, and what they do:

{% highlight elixir %}
String.contains?("slowpoke", "slow")
#=> true

String.replace("What's up?", "up", "down")
#=> "What's down?"

String.split("cool bananas and tough biscuits", " ")
#=> ["cool", "bananas", "and", "tough", "biscuits"]

String.reverse("backwards")
#=> "sdrawkcab"

String.upcase("louder")
#=> "LOUDER"

String.capitalize("daisy")
#=> "Daisy"

String.strip("                     hello?")
#=> "hello?"

String.duplicate("echo", 3)
#=> "echoechoecho"
{% endhighlight %}

To concatenate Strings the `<>` symbol is used, like so:

{% highlight elixir %}
"Hello" <> " old" <> " lady!"
#=> "Hello old lady!"
{% endhighlight %}

<strong>Atoms</strong>

Atoms look like Ruby Symbols and act very much like Strings. An Atom is prefixed by the `:` symbol. You can convert easily between Atoms and Strings, for example:

{% highlight elixir %}
Atom.to_string(:atom_ant)
#=> "atom_ant"

String.to_atom("string_thing")
#=> :string_thing
{% endhighlight %}

To check if something is an Atom, one can use the `is_atom()` method. It is surprising what can be an atom:

{% highlight elixir %}
is_atom(:hello)
#=> true

is_atom(String)
#=> true

is_atom("string")
#=> false

is_atom(Boolean)
#=> true

is_atom(true)
#=> true

is_atom(false)
#=> true

is_atom(List)
#=> true

is_atom([1, 2, 3])
#=> false
{% endhighlight %}

As you can see Modules can be Atoms, as can Boolean values. Apart from Boolean values, all other instances of data-types/modules are not Atoms.

<strong>Sigils for Strings</strong>

Sigils are similar to percentage literals in Ruby, but instead of being prefixed with a `%`, they are prefixed with a `~`. The sigil to represent a String looks like `~s` or `~S`. It is written like so:

{% highlight elixir %}
~s(The sigil tells us to treat the words inside parentheses as a String)
#=>"The sigil tells us to treat the words inside parentheses as a String"
{% endhighlight %}

I first thought, 'How could it be easier to write a string inside a sigil? Surely it is quicker and easier to use double quotes when representing a String!', but there are some instances where they are much more useful than double quotes, such as when you need to show speech inside a string. For example:

```
~s("Hello," said the cat.)
```

is much more straightforward than having to use escape characters like so:

```
"\"Hello,\" said the cat."
```

<strong>Sigils in String Concatenation </strong>

What is the difference between `~s` and `~S`? The lowercase sigil allows for string concatenation, whereas the uppercase sigil does not. For example:

```
~s(Ten divided by Two equals #{div 10, 2})
#=>"Ten divided by Two equals 5" 

~S(Ten divided by Two equals #{div 10, 2})
#=>"Ten divided by Two equals \#{div 10, 2}"
```

<strong>Other Sigils</strong>

There are many other sigils applicable in different Elixir situations. They are:

`~r()` is another way to write a regular expression.

`~c()` creates a char list.

`~w()` gives a list of words.

Sigils can use a number of different delimiters. For instance, as well as seeing sigils written like `~s()`, they can also be written as `~s{}`, `~s[]`, `~s//`, `~s'||` and many more.


---
layout: post
comments: true
title: "Elixir: Require, Use, Alias and Import"
date: 2016-07-19 12:30:30 +0000
---

Elixir allows special permissions to rename and use functions and macros in a variety of circumstances, using the keywords Alias, Use, Import and Require. Each have a specific meaning and purpose.

<strong>Alias</strong>

Alias allows you to rename, and therefore shorten, module names using an alternative. One can then call the functions of the original module using its alias, like so:

{% highlight elixir %}
#"attach" the alias to the end of the module name:
defmodule longLongLongLongLongName.lilName do
  def sayYourName do
	  "Daisy"
  end
end

#alias the name using alias keyword. Will use the last part of module name 
#by default:
alias longLongLongLongLongName.lilName
#or if you want to be more specific, below is different syntax for the same 
#action:
alias longLongLongLongLongName.lilName, as: lilName

#use the alias to call methods from the original module:
lilName.sayYourName
#=> "Daisy"
{% endhighlight %}

<strong>Use</strong>

Use allows you to use functions from a different module in your current module. Set up a macro defined as `__using__` like this:
{% highlight elixir %}
defmodule Cats do
  defmacro __using__(_things) do
	  def make_some_noise do
		  "Miaow!"
		end
	end
end
{% endhighlight %}

_Then call the module being used with `use` keyword in the new module like so:
{% highlight elixir %}
defmodule Noises do
  use Cats
end

Noises.make_some_noise
#=> "Miaow!"
{% endhighlight %}

One can call the used module's functions (if they are within the `__using__` macro) in the new module.

<strong>Import</strong>

Allows you to select specific, or even use all, functions from a module, without having to use their module name as a prefix for the function. For instance, if we wanted to use `Enum`'s `count` function, we need to use the module name to define the function, otherwise we get a compiling error:
{% highlight elixir %}
iex> Enum.count([1, 2, 3])
#=> 3

iex> count([1, 2, 3])
# ** (CompileError) : undefined function count/1
{% endhighlight %}

But using `Import`:
{% highlight elixir %}
iex> import Enum
#=> Enum

iex> count([1, 2, 3])
#=> 3
{% endhighlight %}

To select specific functions we can name them like so:
{% highlight elixir %}
import Enum, only: [count: 1]
{% endhighlight %}

<strong>Require</strong>

Require supplies us with macros that are executed and expanded at run-time - "code that generates code". These kinds of macros are only available through use of the `require` keyword. `require` is only applicable for these macros, for instance we only need `require` a module if we want to use its macros, it is not needed for its functions. An example is the `.is_odd()` macro from the `Integer` module:

{% highlight elixir %}
iex> Integer.is_odd(3)
# ** ((CompileError)) : you must require Integer before incoking the macro...

iex> require Integer
#=> Integer

iex> Integer.is_odd(3)
true
{% endhighlight %}

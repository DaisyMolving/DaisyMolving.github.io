---
layout: post
title: "Case Statements and the Ternary Operator"
date: 2016-01-28 12:30:31 +0000
---

In looking at some basic [conditionals][conditionals-post] we discovered some super cool syntax that Ruby uses to shorten large blocks of conditional code. Ruby has more tricks up its sleeve, and those tricks come in the form of the case statement and the ternary operator.

<strong> The Case Statement </strong>

If we have a conditional statement that has a lot of possible cases, the case statement is the way to go. If looks like this:

{% highlight ruby %}
case language
when "French"
	print "Bonjour"
when "German"
	print "Guten Tag"
when "Danish"
	print "God Dag"
when "Welsh"
	print "Diwrnod da"
when "Japanese"
	print "良い一日"
else 
	print "I don't know that language"
end
{% endhighlight %}

As you can see the case statement allows us to not write `language ==` in every condition over and over. But guess what! Even that is too long! And Ruby let's us write it like this instead:

{% highlight ruby %}
case language
when "German" then print "Guten Tag"
when "Swahili" then print "Siku njema"
when "Danish" then print "God Dag"
when "Welsh" then print "Diwrnod da"
when "Japanese" then print "良い一日"
else print "I don't know that language"
end
{% endhighlight %}

<strong> The Ternary Operator </strong>

The ternary operator is a good option for an if/else statement that only has two cases, that is one option if the case is true and one option if the case is false. It looks like this:

`boolean ? do this is boolean is true : do this if boolean is false`

For instance:

`13 < 7 ? "13 is greater than 7!" : "That's not right..."`

would output `"That's not right..."` because `13 < 7` is `false`

[conditionals-post]: http://daisymolving.github.io/2016/01/18/ruby-conditionals.html

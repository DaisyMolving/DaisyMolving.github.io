---
layout: post
comments: true
title:  "Ruby Conditionals"
date:   2016-01-21 18:29:31 +0000
---

<strong>Ruby is Cool</strong><img src="https://rfclipart.com/image/small/42-ba-c9/isolated-cartoon-orange-sun-in-sunglasses-Download-Royalty-free-Vector-File-EPS-46737.jpg">

Conditionals, if/else statements and all that... Compared to other languages, Ruby has a couple of things that make it way-cool in regard to conditionals, and this is to do with its more real-person-non-roboty-human-type syntax. Let's look at a basic conditional, an if/else statement:

{% highlight ruby %}

num = 100
# variable of num is assigned value of 100

if num == 30
  	print "num is 30"
#nope, num is not equal to 30, so code is not evaluated we move coolly on
elsif num == 60
	print "num is 60"
#again, the statement is incorrect so on we go
else
	print "num is neither 60 nor 30"
#well phewf, we found a statement that is true, this is the one we will print!
end

#=> "num is neither 60 nor 30"

{% endhighlight %}

So nothing too unexpected with a regular if/else statement then. As you can see it is very similar to any other language's equivalent. But Ruby has another trick, the Unless statement. When thinking of our code syntactically like a sentence, as Ruby allows us, sometimes it might be more applicable or easier to understand when we use "unless" instead of "if". Take a decisive step in the direction of your choosing.

{% highlight ruby %}

kind = true

unless kind
	print "I ain't got the time"
else
	print "hello!"
end

#=> "hello!"

{% endhighlight %}

<strong>Wait, Ruby is Ice Cold</strong><img src="http://www.abeka.com/BookImages/ClipArt/232149/46x46y50fx50fh/232149-Purple-Ice-Pop-with-a-bite-missing-color-png.png">

Even c-o-o-l-er is that instead of writing these large sections of code as above, an if/else or unless statment in Ruby can be written in one line, like so:

`print "it's true" if true`

or 

`print "it's false" unless true`

Well, flip.

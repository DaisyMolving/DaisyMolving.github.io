---
layout: post
title: "Something in Nothing"
date: 2016-01-26 12:30:31 +0000
---

<strong> Straight Nil </strong>

In the Ruby language everything is an object. This includes Nil, which is stands for nothing, but isn't really nothing, because as an object Nil can have methods called upon it. To check if something has the value of `nil`, we can called a method called `#nil?` upon it.

{% highlight ruby %}

void_of_nothingness = nil

return void_of_nothingness.nil?

#=> true
{% endhighlight %}

Nil class also has several other methods such as `#to_a`, `#to_h`, `#to_f`, `#to_i` and `#to_s`. This converts a nil value into other data-types in the following ways:

what is blank?

what is empty?

examples where they are used

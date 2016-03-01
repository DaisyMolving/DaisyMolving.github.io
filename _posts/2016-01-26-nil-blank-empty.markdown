---
layout: post
comments: true
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

{% highlight ruby %}
nil_to_array = nil.to_a
return nil_to_array
#=> []

nil_to_hash = nil.to_h
return nil_to_hash
#=> {}

nil_to_float = nil.to_f
return nil_to_float
#=> 0.0

nil_to_integer = nil.to_i
return nil_to_integer 
#=> 0

nil_to_string = nil.to_s
return nil_to_string
#=> ""
{% endhighlight %}

<strong> The `#empty?` Method </strong>

When an Array, Hash or Strings length is equal to `0`, i.e. it has no elements, it is called empty. The `#empty?` method returns a boolean value as to whether or not this is the case. For instance:

{% highlight ruby %}
[].empty?
#=> true

{a: 1, b: 2, c: 3}.empty?
#=> false

{}.empty?
#=> true

"".empty?
#=> true
{% endhighlight %}


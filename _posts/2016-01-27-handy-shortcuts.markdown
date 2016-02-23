---
layout: post
title: "Some Handy Ruby Shortcuts"
date: 2016-01-27 12:30:31 +0000
---

<strong> A Better Way </strong>

Ruby has several shortcuts that make it quick to write and easy to read, without too much clutter. Isn't it nice to have cute and concise code? And especially great to build programmes with spec and implementation files quickly!

<strong> +=, -=, *=, /= </strong>

When we started writing loops we would increment a counter or index like so:
`index = index + 1`
That is, the index now equals one more than before. There is a better way of writing this, and that is using the `+=` operator:
`index += 1` means exactly the same as `index = index + 1` 

So following along, `index = index - 1` can be written as `index -= 1`, `index = index * 1` is the same as writing `index *= 1` and `index = index / 1` is equivalent to `index /= 1`.

In a loop this would look like:

{% highlight ruby %}
index = 1
while index < 5
  puts "shortcuts!"
  index += 1
end

#=> "shortcuts!" "shortcuts!" "shortcuts!" "shortcuts!"
{% endhighlight %}

<strong> Percentage Literals Shortcuts </strong>

Writing an array of strings can take a long time as there are many keys to navigate. Thankfully `%w()` can be very useful for this. Ruby recognises `%w(one two three)` to be the same as `["one", "two", "three"]`. You must seperate your string elements with spaces, but there are no commas or quote marks needed. This is especially helpful when you have a very long array of string elements. But beware, if one of you strings is, for instance, `"ham sandwich"` this percentage literal will split it in two because of the space. Instead you could make it `"ham_sandwich"`.

Here are some more percentage literals:

`%r()` is another way to write a regular expression.
`%x()` is a shell command
`%i()` gives an array of symbols (Ruby >= 2.0.0)
`%s()` turns foo into a symbol (:foo)

<strong> Parallel Assignment </strong>

Parallel assignment is where multiple variables are assigned to multiple values in one operation. So far we have seen assignment like `number = 7` but parrallel assignment looks like `letter, number = "a", 1`. This means `letter = "a"` and `number = 1`. This can be helpful in many instances, for instance if we want to swap values in variables.

A magician has three upturned cups that have wierd objects underneath, they are in the swap_cups array. We will use parallel assignment to assign each object in the array to a variable and then we can see where the objects have travelled after the magician has shuffled his cups.

{% highlight ruby %}
swap_cups = ["caramel", 37, :gherkins]

good, bad, ugly = swap_cups[0], swap_cups[1], swap_cups[2]

#shuffle
good, bad, ugly = ugly, good, bad

return swap_cups
#=> [:gherkins, "caramel", 37]
{% endhighlight %}


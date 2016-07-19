---
layout: post
comments: true
title: "Ruby: Modules, and How They Interact"
date: 2016-03-06 12:30:30 +0000
---

<strong> What is a Module? </strong>

A module is a collection of methods that a class in Ruby can have access to. A module is not the same as a class, so multiple classes can inherit from it while still maintaining single inheritance between classes. For instance `Hash` and `Array` classes both inherit from a class called `Class`. `Array` and `Hash` have similarities that would make a lot of methods useful to both of them. Perhaps they could both inherit these methods from `Class`? But `Class` also has another child called `String`, and yet another called `Integer`. `Integer` and `String` are very different from `Array` and `Hash`, so it wouldn't make sense to give `Class` many methods that are common to `Array` and `Hash`, and then override all of them within `String` and `Integer`. It would make more sense if these methods might be collected somewhere where they can be accessed by both `Hash` and `Array`, but not be needed for `String` or `Integer`. This particular collection that is used by `Hash` and `Array` is called the `Enumerable` module. The `Enumerable` module contains many useful `Hash` and `Array` methods such as `#each`, `#reduce`, `#select` and `#map`.

<strong> Why is a Module Useful? </strong>

A module is useful to mix methods into classes where it doesn't make sense for these methods to be accessed from a parent class. It is useful to share methods accross many classes that might be common. Modules are not the same as classes, and so cannot be instantiated. They act only as a collection of objects that can be used to pass messages and perform tasks on class instances. 

<strong> Extending and Including </strong>

Some modules are already included within classes, as the `Enumerable` module's methods are already included within `Array` and `Hash`. Where they are not, the `include` keyword is used to add methods to instances of the class, and the `extend` keyword for adding class methods. You can extend on a class to mix in a module, that is give it more methods to use. For example:

{% highlight ruby %}
module Adolescent
  def risky
    "Dangerous? Cool!"
  end
end

class Person 
	include Adolescent
end

class Gazelle
	extend Adolescent
end

andy = Person.new
andy.risky #=> "Dangerous? Cool!"
Person.risky #=> NoMethodError...

Gazelle.risky #=> "Dangerous? Cool!"
Gazelle.new.risky #=> NoMethodError...
{% endhighlight %}

You can see above how `include` gives a teenage instance of Person, `andy`, access to methods from the `Adolescent` module, whereas `extend` gives the `Gazelle` <i>class</i> access to the methods of the `Adolescent` module. Extend treats the module's methods as though they are class methods, include treats them as though they are instance methods.

<strong> Namespacing </strong>

Modules use something called namespacing in order to reduce confusion about where a method is coming from. Let's say I want to compare caterpillars that eat different types of lettuce, and also measure whether their movement might follow a cosine curve. I might have a class called `Caterpillar` that includes a module called `Diet` and also includes the `Math` module that already exists in Ruby. But there is a problem. From the `Math` module I would like to use the `cos` (cosine) method, and from the `Diet` module I would like to use the `cos` (lettuce) method (this is a ridiculous example). But how can I tell which is which? This is where namespacing comes in.

We might nest our Caterpillar classes each within the module they are using in each case, so we can specify what methods we would like to use.

{% highlight ruby %}
module Diet
  class Caterpillar
    def cos
      "That was a delicious cos lettuce!"
    end
  end
end

module Math
  class Caterpillar
    def cos
      "I arch like a cosine wave"
    end
  end
end

hungry_caterpillar = Diet::Caterpillar.new
arching_caterpillar = Math::Caterpillar.new

hungry_caterpillar.cos #=> "That was a delicious cos lettuce!"
arching_caterpillar.cos #=> "I arch like a cosine wave"
{% endhighlight %}

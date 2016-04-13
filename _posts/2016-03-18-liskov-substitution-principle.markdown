---
layout: post
comments: true
title: "SOLID: Liskov's Substitution Principle"
date: 2016-03-18 12:30:30 +0000
---

The L in SOLID stands for Liskov's substitution model. It states, "Let `x` be a property provable about objects `x` of type `T`. Then `y` should be true for objects `y` of type `S` where `S` is a subtype of `T`." Right.

What that is saying is that if an object inherits from another, it should be able to replace its parent element in a programme and not have the programme break or have to create exceptions. If it does, then this is not a true example of inheritance. We can think about the example in the previous post about the Open/Closed Principle in this way. The `PaymentProcessor` class can easily be replaced by the `Stripe` or `NewProcessor` classes in that they have the same types of attributes. Liskov's Substitution Principal does not state that we should do this, but rather that we should be able to, and it's something we should keep in mind. It helps us decide which objects should inherit from others, and which objects should stand alone.

Basically we ought to be able to pass all the subclasses around and treat them like their superclass. Any subclasses that are found to be exceptional, are probably better situated somewhere else. 

One example is if we were to have a programme whose task was to draw shapes. We have a `Shapes` class, and we want to be able to draw a `Square`, a `Rectangle` and a `Circle`. How might we set this out, in terms of which classes should inherit from others? Well, `Square`, `Rectangle` and `Circle` are all shapes, so the `Shapes` class would be a superclass. We also know that a `Square` is a type of `Rectangle` as it has four sides. We could visualise our set-up like so:

<p align="center">
<img src="../../../../../../../assets/lsp-violation.jpg">
</p>

Why might this get us stuck? Let's think about the attributes that each class has. If we describe the Shape class, it is "a two-dimensional geometric figure". Is a rectangle "a two-dimensional geometric figure"? Is a circle? Yes, and yes. So here we can see how L.S.P. works, where each shape that inherits from the Shape class could individually replace it. But what about the relationship between a rectangle and a square? A square is a kind of rectangle because it has four sides, just like its parent. But our programme calls for us to draw shapes, and for that we need to consider dimensions. A rectangle is "a two-dimensional geometric figure with a height and a width". A circle is "a two-dimensional geometric figure with a radius". When we draw them we will use these dimensions in equations such as `rectangle_1 = height x width` or `circle_1 = π x radius ** 2`. But will this work for a square? Is a square "a two-dimensional geometric figure with a height and a width"? Well yes, but we know that the height and width will always be the same. What if someone enters heights and widths for squares that are not the same? Then we would have to write code to prevent this from happening and in doing so create an inheritance exception, which violates L.S.P. Flip! A square is not a true child of rectangle in this programme! Let's look at what a square is. Is a square "a two-dimensional geometric figure"? Yes it is, so it can inherit from `Shape`. Now we know that our programme is much better laid out like so:

<p align="center">
<img src="../../../../../../../assets/happy-lsp.jpg">
</p>

Now when we look at how each shape would draw based on their dimensions, we can see how they can each be passed around and act as their parent class. Let's look a little bit more into how those classes look:

{% highlight ruby %}
class Shape

	def initialize(dimension*)
		@dimension = dimension
	end

end

class Circle < Shape

	def initialize(dimension)
 		@radius = dimension
	end

end

class Rectangle < Shape

	def initialize(dimension_1, dimension_2)
		@height = dimension_1
		@width = dimension_2
	end

end

class Square < Shape

	def initialize(dimension)
		@side_length = dimension
	end

end
{% endhighlight %}



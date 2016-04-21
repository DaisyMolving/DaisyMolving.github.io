---
layout: post
comments: true
title: "SOLID: Dependency Inversion Principle"
date: 2016-03-23 12:30:30 +0000
---

The last letter in the SOLID acronym stands for The Dependency Inversion Principle, or The Dependency Injection Principle. It states, "Depend upon Abstractions, not upon Concretions". That is, do not allow high-level, broad objects to depend upon low-level, specific objects, instead create layers of abstraction in mid-level objects to "invert" the dependency.

The more abstracted objects are, the less likelihood of breakage if one of those objects is altered, and it also means that more functionality can be added with ease. Let's look at an example. Let's say we have created an online Media Store, which <i>reads audio files</i> from its library and <i>writes</i> them as downloads when people buy them. Considering the basic requirements at face value, it might look something like diagram below:

<p align="center">
<img src="../../../../../../../assets/violating_dip.jpg">
</p>

However, this set up causes the high level object of `MediaStore` to be very dependent on the low level specific objects of `AudioFileReader` and `AudioFileWriter`. The low level objects' specificity makes them very concrete. This means that if we were to edit these low level file accessors, we risk altering the entire high level function. And what if later requirements considered adding movie files? That might mean we would have to duplicate a lot of read and write functionality in order to create alternative specific movie objects. To keep things clear and minimise fragility we should add a layer of abstraction, like so:

<p align="center">
<img src="../../../../../../../assets/dip-example.jpg">
</p>

Here we have used a level of abstraction in `Reader` and `Writer` to "invert" the dependency. Now the media store depends on reader and writer classes that are non-specific, and that also means that the reader and writer classes need only concentrate on the specific details of reading and writing movie or audio files. We can see how Dependenry Inversion/Injection Principle is very closely related to the [Single Responsibility Principle][srp-post] and the [Open Closed Principle][ocp-post] in this way.

<strong>Dependency Injection</strong>

Some people like to talk about D.I.P. as being about Dependency Inversion, and others about Dependency Injection. I like to think of it as Dependency Inversion being what the principle achieves, and Dependency Injection as how it acheives it. To me it must be both of these things, the 'what' and the 'how'. Dependency Injection is more clearly seen within the code itself. Let's think about software written to operate a copier. The copier must read from one source and write to another source. Let's say it reads from the computer keyboard and writes to a printer. How might that look?

{% highlight ruby %}
class Copier
	def self.copy
		reader = KeyboardReader.new
		writer = Printer.new
	end
end
{% endhighlight %}

Can you see how concrete this example is? The `Copier` class function depends heavily on the `KeyboardReader` class for reading and the `Printer` class for writing. This is not great. Let's look at something preferable:

{% highlight ruby %}
class Copier
	def initialize(reader, writer)
		@reader = reader
		@writer = writer
	end
end

keyboard_to_print_copy = Copier.new(KeyboardReader.new, Printer.new)
{% endhighlight %}

The above example is much more abstract, and therefore less fragile and more open to extension. The "injection" comes into play when we inject the copier's dependencies on instantiation, at `Copier.new(KeyboardReader.new, Printer.new)`. This is open to extension in the sense that the `initialize` method would just just easily take other types of readers and writers such as a `ScanReader` to an `ImagePreviewWriter`. 

[srp-post]:http://daisymolving.github.io/2016/03/13/single-responsibility-principle.html
[ocp-post]:http://daisymolving.github.io/2016/03/15/open-closed-principle.html

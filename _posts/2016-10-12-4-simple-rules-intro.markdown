---
layout: post
comments: true
title: "Exploring the 4 Rules of Simple Design"
date: 2016-10-12 10:30:30 +0000
---

I have been reading <i>Understanding the Four Rules of Simple Design</i> by Corey Haines, a book about Kent Beck's design rules written during his development of Extreme Programming in the late 90's. Corey Haines' book talks about application of the four simple rules at different stages while programming [Conway's Game of Life][conway-game-of-life].

The Four Rules of Simple Design are:

* Pass Tests
* Express Intent
* Minimise Duplication
* Make Things Small

The rules are in order of importance, although there is some debate as to whether Express Intent and Minimise Duplication should be swapped around. Let's look at why each rule is important, and how it aids simple design.

<strong>Pass Tests</strong>

If you are a practioner of TDD it seems pretty obvious that your code should pass tests. After all, our program may be simple and elegant, but first of all we need to know it works. Tests are important because they help us to monitor our code, and see that it behaves as expected. 

For this reason we must also consider that not only are out tests passing, but that our tests themselves are asserting the right things. 

* Our tests should make assertions based upon behaviour rather than state. 
* Our tests should express intent clearly. 
* Our tests should be nicely abstracted so that irrelevant details are not present in them. 
* Our tests should also minimise duplication and aim to be small.

Pass Tests is not only first in order because it is deemed the most important, but also highlights that tests should be conceived before any production code is written.

<strong>Express Intent</strong>

Expressing intent in our code helps us to form sensible classes or modules. This is to group things together in a way that is easy to follow and not difficult to change. For example, naming methods or functions is a simple way to express intent. Naming can be difficult, but it is important to tell us what each function is doing. Such names can help us to collect together in modules the functions that are acting upon the same things. This allows us to enact the Single Responsibility Principle, where all functions that have the same purpose, or reason to change, are grouped together. This will give our application a structure that is easy to follow and easy to extend.

Expressive naming also helps us to understand when individual functions are doing more than one thing. Sometimes when it is difficult to name a function, it is because the purpose of the function is not clear. It may be unclear because it is doing several things. A clear warning that the Single Responsibility Principle is being violated is when our accurate function naming produces an "and", such as in the case of `get_average_british_wage_and_convert_to_euros`.

Naming functions accurately should help us to find single purposes so that <i>accurate</i> naming can become <i>expressive</i> naming.

<strong>Minimise Duplication</strong>

Duplication in our code is often unneccessary and can add confusion. Several functions that all contain the same element often points to another violation of the Single Responsibility Principle, because the duplication is a responsibility used by each function that is not central to its intended purpose. Extracting duplications into their own functions can reduce the clutter and coupling in our code. 

The DRY (Don't Repeat Yourself) principle introduced by Andy Hunt and Dave Thomas states, "Every piece of knowledge must have a single, unambiguous, authoritative representation within a system". This means that no piece of knowledge need be represented twice. 

However, sometimes two seemingly identical lines of code can in fact represent different things, and refactoring them to remove such duplication actually couples two things that are not directly related. Corey Haines calls this "Naïve Duplication". He explains how this can be avoided with expressive naming and increasing abstraction to show intent. 

The example that Haines gives is a from a Ruby implementation of Conway's Game of Life. In it, a cell can survive until the next generation if there are enough other living cells nearby. Alternatively, if the cell is dead it can be revived if there are enough living cells nearby. The rules for this game can be read by clicking on the link at the top of this page. Below is a method that checks if a cell is alive or dead in the next generation:

{% highlight ruby %}
class Cell
  attr_reader :alive

  def alive_in_next_generation? 
    if alive
      number_of_neighbors == 2 || number_of_neighbors == 3
    else
      number_of_neighbors == 3
    end
  end
end
{% endhighlight %}

To make this method dry one might remove the duplication of `number_of_neighbors == 3` like so:

{% highlight ruby %}
  def alive_in_next_generation?
    (alive && number_of_neighbors == 2) ||
		  number_of_neighbors == 3
  end
{% endhighlight %}

However in this case each instance of `number_of_neighbors == 3` represents a different outcome. One instance, when optioned against `number_of_neighbors == 2` checks that the cell's surroundings are stable (i.e. that it will not die), and the other instance checks that the cell's surroundings are fertile (i.e. that it will not remain dead). This is an important distinction. So let's distinguish it, as Corey Haines suggests, with extracting each instance into its own expressively named function, and therefore increasing the level of abstraction.


{% highlight ruby %}
class Cell
  attr_reader :alive

  def alive_in_next_generation? 
    if alive
      stable_surroundings?
    else
      fertile_surroundings?
    end
  end
end
{% endhighlight %}

<strong>The Four Rules Order Debate</strong>

There are two camps generally when it comes to the priority of the the four rules. Some follow them as they are written here, others feel that minimising duplication is more important than expressing intent. 

I think the most insightful readings of the priority here have been from those who suggest that the two middle rules act in a feedback loop, one always introducing the other. It is easy to see how closely related they are in the game of life cell example above, when expressive naming prevents unneccessary, and potentially harmful, removal of duplication. On the other side of the coin removal of duplication creates more specific functions, which in turn clearly expresses intent.

<strong>Make Things Small</strong>

The final rule is to make things small. This means to keep functions to a single purpose and to create classes and modules that have only one reason to change. Keeping things small also means ensuring that unneccessary functionality is not created, as the simpler an application the more extensible it is. 

The YAGNI, or You Aren't Going To Need It, principle states that a programmer should not add functionality until deemed necessary. By removing anything that does not serve the application we are also advocating the Open/Closed Principle, that is that your code should be open to extension and closed to modification. 

The smaller the function the better it serves its purpose, and the smaller the class or module the more obvious its containment of such functions.

[conway-game-of-life]:https://en.wikipedia.org/wiki/Conway%27s_Game_of_Life

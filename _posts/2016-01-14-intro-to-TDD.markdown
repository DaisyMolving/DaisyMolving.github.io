---
layout: post
title:  "An introduction to TDD"
date:   2016-01-14 12:29:31 +0000
---

Today I met with Cedric and he gave me a problem: 

  Find all the numbers under a limit of n that are divisible by 3 or 5, and then return the sum of these numbers.

He wanted me to think through the problem before I solved it, and I wrote out my scramble thoughts in bad [pseudo code][pseudo-code]:

{% highlight ruby %}
# We want the Multiples 3 and 5 under limit of n, 
# and to then give the value of the sum of these multiples.

# We will have:
  an_empty_array_to_shovel_multiples_into = []
  a_limit = n

# We can use modulus to find the multiples of 3 and 5

if multiple % 3 == 0 or multiple % 5 == 0 
# then shovel multiple into our array

# For instance:
a_limit = 10
an_empty_array_to_shovel_multiples_into == [3,5,6,9]

# Then to find the sum we can:

an_empty_array_to_shovel_multiples_into.reduce(:+)

# Therefore in this case the sum is returned as:

#=> sum == 23

{% endhighlight %}

Not an incredibly clear structure, but the idea was to figure out the problem in my head first, before I attempted to solve it. We were going to do a TDD exercise, so to know the problem is to know what tests to write and what their outcomes should be.

In the words of [Uncle Bob][uncle-bob-TDD-rules], the three rules of Test Driven Development are:

  1. You are not allowed to write any production code unless it is to make a failing unit test pass.
  2. You are not allowed to write any more of a unit test than is sufficient to fail; and compilation failures are failures.
  3. You are not allowed to write any more production code than is sufficient to pass the one failing unit test.

In that case we had to start by creating the spec file, writing the tests and once the test fails we could start to write the solution. Then when the test passes we can write refactor the code (of course checking that these changes don’t make the test fail again!)

This method is also known as red, green, refactor. A test is red (fails) until a test is green (passes) and then it can be refactored.

My tasks until we spoke again were to complete the TDD exercise for Multiples of 3 and 5, to complete the Vimtutor and to complete Codecademy’s Ruby course. Phewf!

Cedric also showed me a great site for a free learning programme called The Odin Project (http://www.theodinproject.com/), and in my own searching I also found the curriculum with exercises for Railsbridge (http://curriculum.railsbridge.org/docs/). Railsbridge is a course based in the United States that has the occasional workshop in the United Kingdom too. It is an organisation that is interested in diversifying the tech industry, and run weekend workshops to get people involved in tech by learning Ruby on Rails. 

[uncle-bob-TDD-rules]: http://butunclebob.com/ArticleS.UncleBob.TheThreeRulesOfTdd
[pseudo-code]: http://programmers.stackexchange.com/questions/12683/should-one-use-pseudocode-before-actual-coding

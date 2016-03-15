---
layout: post
comments: true
title:  "An introduction to TDD"
date:   2016-01-15 12:29:31 +0000
---

Today Cedric and I had a session about TDD. 

<strong>What's that?</strong>

TDD, or Test Driven Development, is the very-handy practise of testing your code as it is written. A test is written (no code yet!) and should fail. Once it fails some code can be written to make the test pass. Once the test passes it can be refactored if need be. After these three steps produce a passing test, the next test can be written, and the process repeated.

This may seem like a time-consuming exercise, but it is outrageously valuable for things like:

  1. helping you to figure out what you want to the code to do, therefore creating detail in your specifications. 
  2. keeping your code [DRY][dont-repeat-yourself] and concise. This is because it forces you to write code only in response to the tests.
  3. reducing time spent reworking the code. If details must be changed it is easy to ensure they don't break other specs.
  4. also reducing time spent debugging if you can see exactly where the problem resides.
  5. being advantageous in the development of the code's intention and your changing understanding of the nature of the problem.

In the words of [Uncle Bob][uncle-bob-TDD-rules], the three rules of Test Driven Development are:

  1. You are not allowed to write any production code unless it is to make a failing unit test pass.
  2. You are not allowed to write any more of a unit test than is sufficient to fail; and compilation failures are failures.
  3. You are not allowed to write any more production code than is sufficient to pass the one failing unit test.

This method is also known as red, green, refactor. A test is red (fails) until a test is green (passes) and then it can be refactored.

<strong>Applying TDD</strong>

In Ruby the gem used for TDD is [Rspec][rspec-info]. You can install this on your terminal and get straight to writing tests and running Rspec. This [tutorial][rpsec-library-tutorial] from Tuts+ will give you an understanding of how to set up rspec and file structure, as well as how the tests run. So how might I apply TDD with Rspec to a kata?

Cedric and gave this problem: 

  `Find all the numbers under a limit of n that are divisible by 3 or 5, and then return the sum of these numbers.`

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

Not an incredibly clear structure here, but the idea was to figure out the problem in my head first, before I attempted to solve it. To know the problem is to know what tests to write and what their outcomes should be.

This is how it might start:

<p align="center">
<img src="../../../../../../../assets/beginning-tdd.jpg">
</p>

<br>

<strong>Another Resource...</strong>

There is a secret, for-spies-only, resource in the comments section of this [blog-post][air-pair-readers-coupon] (still valid?) if you want a more involved tutorial of Test Driven Development. Plus the tutor has an excellent moustache!

<div align="center">
<iframe src="//giphy.com/embed/Dzmg5QAojwb6M" width="300" height="180" frameBorder="0" allowFullScreen></iframe>
</div>

P.s. This is not the moustachioed tutor, this is you being a spy, and also owning a very good crumb-catcher.


[uncle-bob-TDD-rules]: http://butunclebob.com/ArticleS.UncleBob.TheThreeRulesOfTdd
[pseudo-code]: http://programmers.stackexchange.com/questions/12683/should-one-use-pseudocode-before-actual-coding
[dont-repeat-yourself]: http://programmer.97things.oreilly.com/wiki/index.php/Don't_Repeat_Yourself
[rspec-info]: http://rspec.info/
[rpsec-library-tutorial]: https://code.tutsplus.com/tutorials/ruby-for-newbies-testing-with-rspec--net-21297
[air-pair-readers-coupon]: https://www.airpair.com/testing/learn-ruby-test-driven-development

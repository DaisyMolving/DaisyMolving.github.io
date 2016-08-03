---
layout: post
published: false
comments: true
title: "Asymptotic Notation"
date: 2016-07-28 10:30:30 +0000
---

<strong>What is Asymptotic Notation</strong>

When writing software and applications, the time that it takes for operations to run depends on a whole lot of factors, such as: 

* The age of your computer and how much memory is used
* The software underneath that is used to run your program
* Other processes running at the same time that slow your program down

This makes it difficult to measure the efficiency of an algorithm or program, since time cannot be used truthfully, due to all the possible external factors affecting it. How slow or fast it is running therefore, might actually have nothing to do with its efficiency.

Computer Science uses something called Asymptotic Notation. It is a measure of efficiency that depends upon the number of operations (`n`) that an algorithm has to perform. It asks, as `n` increases, how much less efficient, or how much greater is the runtime, of your software. There are three categories of asymptotic notation, they are:

* Big O notation (that's a letter 'oh', not a zero)
* Big Ω notation (that's an omega)
* Big Θ notation (that's a theta)

Big O notation represents the worst case of efficiency, Big Ω the best case and Big Θ where the best and worst case are the same. Let's look at an example.

<strong>Linear Functions</strong>

In a linear search algorithm a list of sorted numbers is taken as an argument and iterated over, one by one. A friend has chosen a number from the list `[1, 2, 3, 4, 5, 6, 7, 8]`. To find it with linear search we start at number `1`, the first position. We check if that is the secret number, and if it isn't we carry on to the next position. We repeat this until we find the number, or we have gone through every element in the list. 

The best outcome for efficiency would have been that the number in the first position was the chosen number, then we would have had only to guess once and the search would end. The worst outcome would be that the chosen number was in the last position. This means that linear search can be described as `0(n)`. 

<p align="center">
<img src="../../../../../../../assets/asymptotic_linear_iterations.jpg">
</p>

That means that the worst outcome is directly proportional to the number of operations. As `n` increases by one, the runtime increases by one unit of time at the same rate.

On a graph it would look like this:

<p align="center">
<img style="width: 400px;" src="../../../../../../../assets/linear_asymptote_graph.jpg">
</p>

Because it is directly proportional, a linear function is not greatly efficient. As our system grows so too does our runtime, at the same rate, forever. For algorithms that are only ever required to perform small operations this may not be a problem, but for larger operations the difference would be very noticeable. Imagine if the unit of time that ran a single operation was a millisecond, one thousandth of a second. For 100 elements the worst case runtime would be 100 milliseconds, but for 60,000 the worst case runtime would be a whole minute. Luckily, computers don't usually run that slowly, but you can see by this comparison how inefficient a linear function might be. So what is a better option?

<strong>Logarithmic Functions</strong>

[Binary Search][binary-search] is a search algorithm that is an example of a Logarithmic Function. 


[binary-search]:http://daisymolving.github.io/2016/07/18/binary-search.html


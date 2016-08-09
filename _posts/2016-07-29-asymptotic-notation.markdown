---
layout: post
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

[Binary Search][binary-search] is a search algorithm that is an example of a Logarithmic Function. This particular logarithmic function finds an element by dividing the possible search by two every time that it "guesses". This means that the number of operations in this case is maximum `log` (with base 2) `(number_of_elements) = n`. So for a list of 8 elements there will be no more than three guesses/operations, and for a list of sixteen elements (twice the size) the number of guesses/operations only increases by one, so `n = 4`.

This means that logarithmic functions, where `O log(n)`, are very efficient. They can be seen on a graph as visually opposite to an exponential, they grow ever more slowly as the number of operations increases. On the graph it would look like: 

<p align="center">
<img style="width: 400px;" src="../../../../../../../assets/logarithmic_func_graph.png">
</p>

Thinking back to how a linear function which took a list of 100 elements might take 100 milliseconds, by the same list a logarithmic function would take 6.64 milliseconds! But what if we can me even more efficient?

<strong>Constant Functions</strong>

A constant function is a function that regardless of the number of operations, the run-time does not increase. This means that `O(n^0)`, but because any number to the power of `0` equates to `1`, a constant function is notated as `O(1)`. On a graph it looks like a flat straight line moving towards infinity, like so:

<p align="center">
<img style="width: 400px;" src="../../../../../../../assets/constant_func_graph.png">
</p>

An example of a constant function is one that recalls the size of a list that is updated in a pre-stated variable everytime something is added. Despite how many elements there are in the list, the function recalls the number instantly, at a constant.

Let's compare it to our previous functions, as well as some other types to avoid:

<div align="center" style="margin-bottom: 30px;">
<table style="border-spacing: 0px; border: #111162 solid 2px;">
<tr>
<td style="width: 200px; padding: 10px; border: #111162 solid 1px; margin: 0px; color: #111162; background-color: #eeeeff">Worst Case of Function Type</td>
<td style="padding: 10px; border: #111162 solid 1px; margin: 0px; color: #111162; background-color: #eeeeff">If <i>n</i> = 100 and runtime unit one millisecond</td>
</tr>
<tr>
<td style="padding: 10px; border: #111162 solid 1px; margin: 0px;">O(1) (constant)</td>
<td style="padding: 10px; border: #111162 solid 1px; margin: 0px;">1</td>
</tr>
<tr>
<td style="padding: 10px; border: #111162 solid 1px; margin: 0px;">O log(n) (logarithmic)</td>
<td style="padding: 10px; border: #111162 solid 1px; margin: 0px;">6.64</td>
</tr>
<tr>
<td style="padding: 10px; border: #111162 solid 1px; margin: 0px;">O(n) (linear)</td>
<td style="padding: 10px; border: #111162 solid 1px; margin: 0px;">100</td>
</tr>
<tr>
<td style="padding: 10px; border: #111162 solid 1px; margin: 0px;">O nlog(n) (log-linear)</td>
<td style="padding: 10px; border: #111162 solid 1px; margin: 0px;">664</td>
</tr>
<tr>
<td style="padding: 10px; border: #111162 solid 1px; margin: 0px;">O n^2 (quadratic)</td>
<td style="padding: 10px; border: #111162 solid 1px; margin: 0px;">10,000</td>
</tr>
<tr>
<td style="padding: 10px; border: #111162 solid 1px; margin: 0px;">O n^3 (cubic)</td>
<td style="padding: 10px; border: #111162 solid 1px; margin: 0px;">100,000</td>
</tr>
<tr>
<td style="padding: 10px; border: #111162 solid 1px; margin: 0px;">O 2^n (exponential)</td>
<td style="padding: 10px; border: #111162 solid 1px; margin: 0px;">127 * 10^27 (that's 27 zeros!)</td>
</tr>
</table>
</div>




[binary-search]:http://daisymolving.github.io/2016/07/18/binary-search.html


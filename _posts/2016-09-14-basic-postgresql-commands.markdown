---
layout: post
comments: true
title: "PostgresQL: Some Basic SQL Commands"
date: 2016-09-14 10:30:30 +0000
---

PostgresQL is an object relational database management system, using the language SQL. SQL stands for Structured Query Language, and it is used to communicate with your database, in order to add or remove data, present data, or edit data.

A database can be thought of as a series of tables, each with rows and columns. Each column relates to a category, and each row is an instance of something or someone who has/or relates to each of those categories. Each instance has an identification number. Here is an example of a database table, a contact sheet for freelance software developers that a company uses:

<div align="center" style="margin-bottom: 30px;">
<table style="border-spacing: 0px; border: #111162 solid 2px;">
<tr>
<td style="padding: 10px; border: #111162 solid 1px; margin: 0px; color: #111162; background-color: #eeeeff">id</td>
<td style="padding: 10px; border: #111162 solid 1px; margin: 0px; color: #111162; background-color: #eeeeff">firstname</td>
<td style="padding: 10px; border: #111162 solid 1px; margin: 0px; color: #111162; background-color: #eeeeff">lastname</td>
<td style="padding: 10px; border: #111162 solid 1px; margin: 0px; color: #111162; background-color: #eeeeff">contactnumber</td>
<td style="padding: 10px; border: #111162 solid 1px; margin: 0px; color: #111162; background-color: #eeeeff">languages</td>
<td style="padding: 10px; border: #111162 solid 1px; margin: 0px; color: #111162; background-color: #eeeeff">rate/hr</td>
</tr>
<tr>
<td style="padding: 10px; border: #111162 solid 1px; margin: 0px;">1</td>
<td style="padding: 10px; border: #111162 solid 1px; margin: 0px;">Fred</td>
<td style="padding: 10px; border: #111162 solid 1px; margin: 0px;">Hernandez</td>
<td style="padding: 10px; border: #111162 solid 1px; margin: 0px;">336-283-5937</td>
<td style="padding: 10px; border: #111162 solid 1px; margin: 0px;">ruby, elixir, javascript</td>
<td style="padding: 10px; border: #111162 solid 1px; margin: 0px;">22</td>
</tr>
<tr>
<td style="padding: 10px; border: #111162 solid 1px; margin: 0px;">2</td>
<td style="padding: 10px; border: #111162 solid 1px; margin: 0px;">Mahmoud</td>
<td style="padding: 10px; border: #111162 solid 1px; margin: 0px;">Bahar</td>
<td style="padding: 10px; border: #111162 solid 1px; margin: 0px;">404-310-0631</td>
<td style="padding: 10px; border: #111162 solid 1px; margin: 0px;">javascript, java, c++</td>
<td style="padding: 10px; border: #111162 solid 1px; margin: 0px;">25</td>
</tr>
<tr>
<td style="padding: 10px; border: #111162 solid 1px; margin: 0px;">3</td>
<td style="padding: 10px; border: #111162 solid 1px; margin: 0px;">Christina</td>
<td style="padding: 10px; border: #111162 solid 1px; margin: 0px;">Kjær</td>
<td style="padding: 10px; border: #111162 solid 1px; margin: 0px;">517-322-7693</td>, 
<td style="padding: 10px; border: #111162 solid 1px; margin: 0px;">java, c++, haskell</td>
<td style="padding: 10px; border: #111162 solid 1px; margin: 0px;">23</td>
</tr>
<tr>
<td style="padding: 10px; border: #111162 solid 1px; margin: 0px;">4</td>
<td style="padding: 10px; border: #111162 solid 1px; margin: 0px;">Akio</td>
<td style="padding: 10px; border: #111162 solid 1px; margin: 0px;">Abe</td>
<td style="padding: 10px; border: #111162 solid 1px; margin: 0px;">802-229-2213</td>
<td style="padding: 10px; border: #111162 solid 1px; margin: 0px;">python</td>
<td style="padding: 10px; border: #111162 solid 1px; margin: 0px;">20</td>
</tr>
<tr>
<td style="padding: 10px; border: #111162 solid 1px; margin: 0px;">5</td>
<td style="padding: 10px; border: #111162 solid 1px; margin: 0px;">Kaja</td>
<td style="padding: 10px; border: #111162 solid 1px; margin: 0px;">Walczak</td>
<td style="padding: 10px; border: #111162 solid 1px; margin: 0px;">508-587-4508</td>
<td style="padding: 10px; border: #111162 solid 1px; margin: 0px;">erlang, elixir, java, clojure</td>
<td style="padding: 10px; border: #111162 solid 1px; margin: 0px;">30</td>
</tr>
<tr>
<td style="padding: 10px; border: #111162 solid 1px; margin: 0px;">6</td>
<td style="padding: 10px; border: #111162 solid 1px; margin: 0px;">Céline</td>
<td style="padding: 10px; border: #111162 solid 1px; margin: 0px;">Proulx</td>
<td style="padding: 10px; border: #111162 solid 1px; margin: 0px;">315-413-3845</td>
<td style="padding: 10px; border: #111162 solid 1px; margin: 0px;">java, ruby, javascript</td>
<td style="padding: 10px; border: #111162 solid 1px; margin: 0px;">24</td>
</tr>
</table>
</div>

Let's say the name of this table is `freelancecontacts`. How might we access different parts of the table?

<strong>Selecting All Columns</strong>

If we want to select something from the table we use the command `select`. `*` is used to mean "all columns". We also need to specify where we are getting the columns `from`, using the table name.

Therefore our query would look like:

{% highlight sql %}

select * from cd.freelancecontacts

{% endhighlight %}

<strong>Specifying Columns</strong>

What about when we want to specify certain columns instead of all of them? The basic syntax is:

`select [some set of columns] from [some table or a group of tables]`

So if we wanted just the first and last names of each of the freelancers, we could select them like this:

{% highlight sql %}

select firstname, lastname from cd.freelancecontacts

{% endhighlight %}

<strong>Selecting Columns Based on Information</strong>

We can also select all the freelancers that charge under $25/hr. We do this by selecting the columns that match up with a particular column where this is true. We use the query:

{% highlight sql %}

select * from cd.freelancecontacts where rate/hr < 25

{% endhighlight %}

<strong>Selecting Based on Patterns</strong>

What if the company wanted to select all the JavaScript developers? They would select based on a pattern. A pattern uses the syntax of `'%pattern%'`.

{% highlight sql %}

select * from cd.freelancecontacts where languages like '%javascript%'

{% endhighlight %}

What about if the company wanted the JavaScript developers but only ones that charge under $25/hr? They can use the `and` keyword, like so:

{% highlight sql %}

select * from cd.freelancecontacts 
	where languages like '%javascript%'
	and rate/hr < 25

{% endhighlight %}

<strong>Selecting Based on Multiple Identifiers</strong>

We can select multiple freelancers by their id, using the `or` keyword like so:

{% highlight sql %}

select * from cd.freelancecontacts where id = 2 or id = 4

{% endhighlight %}

Or a more concise way of doing it, using `in`, would be:

{% highlight sql %}

select * from cd.freelancecontacts where id in (2, 4)

{% endhighlight %}

<strong>Adding a Column Based on Information</strong>

Say we want to do something (add a column for instance), based upon a current possibility, we can use a `case` statement. Maybe the company has a budget that means that all freelancers who charge less than $25/hr are "affordable" and all others are "expensive". They could make a query like this:

{% highlight sql %}

select firstname, lastname,
case when (rate/hr < 25 )
	then "affordable"
	else "expensive"
end as relationtobudget
from cd.freelancecontacts

{% endhighlight %}

This would return the table:


<div align="center" style="margin-bottom: 30px;">
<table style="border-spacing: 0px; border: #111162 solid 2px;">
<tr>
<td style="padding: 10px; border: #111162 solid 1px; margin: 0px; color: #111162; background-color: #eeeeff">firstname</td>
<td style="padding: 10px; border: #111162 solid 1px; margin: 0px; color: #111162; background-color: #eeeeff">lastname</td>
<td style="padding: 10px; border: #111162 solid 1px; margin: 0px; color: #111162; background-color: #eeeeff">relationtobudget</td>
</tr>
<tr>
<td style="padding: 10px; border: #111162 solid 1px; margin: 0px;">Fred</td>
<td style="padding: 10px; border: #111162 solid 1px; margin: 0px;">Hernandez</td>
<td style="padding: 10px; border: #111162 solid 1px; margin: 0px;">affordable</td>
</tr>
<tr>
<td style="padding: 10px; border: #111162 solid 1px; margin: 0px;">Mahmoud</td>
<td style="padding: 10px; border: #111162 solid 1px; margin: 0px;">Bahar</td>
<td style="padding: 10px; border: #111162 solid 1px; margin: 0px;">expensive</td>
</tr>
<tr>
<td style="padding: 10px; border: #111162 solid 1px; margin: 0px;">Christina</td>
<td style="padding: 10px; border: #111162 solid 1px; margin: 0px;">Kjær</td>
<td style="padding: 10px; border: #111162 solid 1px; margin: 0px;">affordable</td>
</tr>
<tr>
<td style="padding: 10px; border: #111162 solid 1px; margin: 0px;">Akio</td>
<td style="padding: 10px; border: #111162 solid 1px; margin: 0px;">Abe</td>
<td style="padding: 10px; border: #111162 solid 1px; margin: 0px;">affordable</td>
</tr>
<tr>
<td style="padding: 10px; border: #111162 solid 1px; margin: 0px;">Kaja</td>
<td style="padding: 10px; border: #111162 solid 1px; margin: 0px;">Walczak</td>
<td style="padding: 10px; border: #111162 solid 1px; margin: 0px;">expensive</td>
</tr>
<tr>
<td style="padding: 10px; border: #111162 solid 1px; margin: 0px;">Céline</td>
<td style="padding: 10px; border: #111162 solid 1px; margin: 0px;">Proulx</td>
<td style="padding: 10px; border: #111162 solid 1px; margin: 0px;">affordable</td>
</tr>
</table>
</div>

<strong>Selecting In Order, With Limits</strong>

To select in a certain order we use the term `order by` with either `asc` for ascending, or `desc` for descending. If `asc` or `desc` is not specified then the default will be ascending order. A limit can also be used, so that the top <i>n</i> amount of the category will be returned. To get the first three most expensive freelancers we can:

{% highlight sql %}

select firstname, lastname 
from cd.freelancecontacts 
order by rate/hr desc
limit 3;

{% endhighlight %}

<strong>Selecting a List from Two Tables</strong>

The company that employs the freelancers also has some in-house developers, and they would like a list of all of the languages that all possible employees know. The table below is called `inhousedevelopers`.

<div align="center" style="margin-bottom: 30px;">
<table style="border-spacing: 0px; border: #111162 solid 2px;">
<tr>
<td style="padding: 10px; border: #111162 solid 1px; margin: 0px; color: #111162; background-color: #eeeeff">id</td>
<td style="padding: 10px; border: #111162 solid 1px; margin: 0px; color: #111162; background-color: #eeeeff">firstname</td>
<td style="padding: 10px; border: #111162 solid 1px; margin: 0px; color: #111162; background-color: #eeeeff">lastname</td>
<td style="padding: 10px; border: #111162 solid 1px; margin: 0px; color: #111162; background-color: #eeeeff">languages</td>
</tr>
<tr>
<td style="padding: 10px; border: #111162 solid 1px; margin: 0px;">1</td>
<td style="padding: 10px; border: #111162 solid 1px; margin: 0px;">Ken</td>
<td style="padding: 10px; border: #111162 solid 1px; margin: 0px;">Waller</td>
<td style="padding: 10px; border: #111162 solid 1px; margin: 0px;">ruby, elixir, erlang</td>
</tr>
<tr>
<td style="padding: 10px; border: #111162 solid 1px; margin: 0px;">2</td>
<td style="padding: 10px; border: #111162 solid 1px; margin: 0px;">Sally</td>
<td style="padding: 10px; border: #111162 solid 1px; margin: 0px;">Benson</td>
<td style="padding: 10px; border: #111162 solid 1px; margin: 0px;">ruby, java, javascript</td>
</tr>
<tr>
<td style="padding: 10px; border: #111162 solid 1px; margin: 0px;">3</td>
<td style="padding: 10px; border: #111162 solid 1px; margin: 0px;">Annie</td>
<td style="padding: 10px; border: #111162 solid 1px; margin: 0px;">Singh</td>
<td style="padding: 10px; border: #111162 solid 1px; margin: 0px;">java, c++, erlang</td>
</tr>
</table>
</div>

To find the languages of each person in both tables we use `union`:

{% highlight sql %}

select languages from cd.freelancecontacts 
union
select languages from cd.inhousedevelopers

{% endhighlight %}

<strong>Using Aggregates</strong>

A quick way to find the largest or smallest price is by using the aggregates `max()` and `min()`, like so:

{% highlight sql %}

select max(rate/hr) as mostexpensive
from cd.freelancecontacts

{% endhighlight %}

or

{% highlight sql %}

select min(rate/hr) as mostaffordable
from cd.freelancecontacts

{% endhighlight %}

<strong>To Use A Subquery?</strong>

How might we return the name of the person with the lowest hourly rate? We could use a subquery like so:

{% highlight sql %}

select firstname, surname 
from cd.freelancecontacts
where rate/hr =
	(select max(rate/hr)
		from cd.freelancecontacts)

{% endhighlight %}

However there are occasionally more concise ways to access information than using subqueries, like so:

{% highlight sql %}

select firstname, surname 
from cd.freelancecontacts
order by rate/hr 
limit 1;

{% endhighlight %}

If you want to practise these SQL commands by <i>doing</i> you can try the exercises at [PostgresQL Exercises][postgresql_basic_ex].

[postgresql_basic_ex]:https://pgexercises.com/questions/basic/

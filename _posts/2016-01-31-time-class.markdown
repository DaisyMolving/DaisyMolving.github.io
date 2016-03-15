---
layout: post
comments: true
title:  "The Time Class"
date:   2016-01-31 12:29:31 +0000
---
<strong> Using Ruby's Time Class </strong>

Ruby has a class called Time, which holds a range of information regarding the date and time. To access the current date and time you can assign a new instance of the time class to a variable like so:

{% highlight ruby %}

time = Time.new

#=> 2016-01-22 10:32:50 +0000

{% endhighlight %}

Below is a screen-recording to show how the Time class can be accessed within the console, and what it is doing:

<div align="center">
<video src="../../../../../../../assets/Time_class.m4v" width="700" height="400" style="padding: 0px;" frameBorder="0" allowFullScreen controls></video>
</div>

You can access different components in the Time class with different key words:


{% highlight ruby %}

time = Time.new

time.year #=> year of the date
time.month #=> month of the date (1 to 12)
time.day #=> day of the date (1 to 31)
time.wday #=> day of the week (0 to 6, where Sunday is 0)
time.yday #=> day of the year (1 to 366)
time.hour #=> hour of the day (0 to 23)
time.min #=> min of the hour (0 to 59)
time.sec #=> second of the minute (0 to 59)
time.usec #=> microseconds (000000 to 999999)
time.zone #=> timezone name (e.g. "UTC")

{% endhighlight %}

<strong>Formatting the Date and Time</strong>

For formatting the date and time we can use our method friend `.strftime` and his directives. 

`.strftime` stands for "standard formatting time" and below you can find a list of what are called directives.
Directives specify what time information we want in a neat and concise way. For instance:

{% highlight ruby %}

time = Time.new

def print_time_long_way
  print "Today is the #{time.day}nd of #{time.month}, #{time.year}"
end

print_time_long_way
#=> Today is the 22nd of January, 2016

def print_time_short_way
  print time.strftime("Today is the %dnd of %B, %Y")
end

print_time_short_way
#=> Today is the 22nd of January, 2016


{% endhighlight %}
See how both methods return the same result, but `.strftime` makes writing the action much neater and quicker? 

<strong>A list of Directives for Standard Formatting</strong>

{% highlight ruby %}

"%a" #=> Abbreviated weekday name
"%A" #=> Full weekday name
"%b" #=> Abbreviated month name
"%B" #=> Full month name
"%c" #=> Preferred local date and time representation
"%d" #=> Day of the month (1 to 31)
"%H" #=> Hour of the day (0 to 23)
"%I" #=> Hour of the day (1 to 12)
"%j" #=> Day of the year (1 to 366)
"%m" #=> Month of the year (1 to 12)
"%M" #=> Minute of the hour (0 to 59)
"%p" #=> Meridian indicator (am or pm)
"%S" #=> Second of the minute (0 to 59)
"%U" #=> Week number of current year, where weeks start at Sunday (0 to 53)
"%W" #=> Week number of current year, where weeks start at Monday (0 to 53)
"%w" #=> Day of Week (0 to 6, where Sunday is 0)
"%x" #=> Preferred representation of the date, no time
"%X" #=> Preferred representation of the time, no date
"%y" #=> Year without a century (00 to 99)
"%Y" #=> Year with a century (e.g. 2016)
"%Z" #=> Time zone name
"%%" #=> Literal % character

{% endhighlight %}

<br>

If you would like to find some more methods that act upon the Time class, you can refer to the [Ruby Docs][ruby-docs-time-class] on this. There is also very good information at [Tutorials Point][tutorials-point-time].

<br>

<strong>Regarding that screen-recording...</strong>

In this video I wrote out the time formatting with its directives in an incredibly long winded way.
It wrote it like:
{% highlight ruby %}
time = Time.new
time.strftime("%A" + " the " + "%d" + "th" + " of " + "%B")
{% endhighlight %}

but it can just be written like:

{% highlight ruby %}
time = Time.new
time.strftime("%A the %dth of %B")
{% endhighlight %}

Well, phewf!

[ruby-docs-time-class]: http://ruby-doc.org/core-2.2.0/Time.html
[tutorials-point-time]: http://www.tutorialspoint.com/ruby/ruby_date_time.htm


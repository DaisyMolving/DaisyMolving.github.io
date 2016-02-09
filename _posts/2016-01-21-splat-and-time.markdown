---
layout: post
title:  "Ruby Splat and the Time Class"
date:   2016-01-21 12:29:31 +0000
---
<strong> Using Ruby's Time Class </strong>

Ruby has a class called Time, which holds a range of information regarding the date and time. To access the current date and time you can assign a new instance of the time class to a variable like so:

{% highlight ruby %}

time = Time.new

#=> 2016-01-21 10:32:50 +0000

{% endhighlight %}

Here is a screen-recording to show how the Time class can be accessed within the console, and what it is doing:

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


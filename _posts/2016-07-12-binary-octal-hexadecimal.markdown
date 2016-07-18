---
layout: post
comments: true
title: "Binary, Octal and Hexadecimal Numbers"
date: 2016-07-12 12:30:30 +0000
---

The most widely used system for counting and arithmetic is the decimal, or base-ten, system. For example, we use ten digits to represent all numbers (0, 1, 2, 3, 4, 5, 6, 7, 8, 9). This is likely derived from humans possessing ten fingers, a convenient physical reference for counting on.
Binary, Octal and Hexadecimal numbers are numbers which are represented differently from our decimal system, using different digits and sometimes letters. First, let's look at how the ordinary decimal system works.

<strong>The Decimal System</strong>

The decimal system uses the ten digits, from zero to nine. It then uses the same digits prefixed with `1` to represent ten to nineteen, again prefixed with `2` to represent twenty to twenty-nine, and so on to infinity. For instance when we look at the number `9,724`, we know that it has `9` thousands, `7` hundreds, `2` tens and `4` ones.

Another way of putting it is:

<p align="center">
<img src="../../../../../../../assets/decimal_base_ten_system.png">
</p>

This is because `10^0 == 1`, `10^1 == 10` and so on. Written in this way it is much clearer how the system uses a base of ten. So what about the binary system?

<strong>The Binary System</strong>

The binary system uses only the first two digits of the decimal system, the `0` and the `1`. The binary system is a base-two system. This means that it works using `2` as a base for each exponent. It looks like this:

<p align="center">
<img src="../../../../../../../assets/binary_table.png">
</p>

Look at how `2^0` is another way of notating `1`, `2^1` is `2`, `2^2` is `4` and `2^3` is `8`. Now if we want to know how the binary number for the number `1` is represented we can use the table to ask how many ones there are, and put a `1` in that column. This makes `1` represented in binary as `0001`.

For the number `2` there is one in the `2^1` column, and so `2` is represented as `0010`. What about `3`? Does `8` go into `3`? Nope, and nor does `4`. But `2` does! Once! We put a `1` in the `2^1` column. Now there is still `1` left over. This means we will put a `1` in the `2^0` column, and `3` is represented in binary as `0011`.

<strong>Octal Numbers</strong>

Octal numbers use a base of eight. This is helpful in computing, because units of digital information called <i>bytes</i> consist of eight <i>bits</i>. Octal counting systems are also used by the Yuki and Pamean Native American peoples, as they count using the spaces in between their fingers rather than the fingers themselves. 

Just like how the binary system only uses the first two digits in its notation, the octal system only uses the first eight, that is `0, 1, 2, 3, 4, 5, 6` and `7`. In order to convert a decimal number to an octal one, we used the same process as above, but we use a table that uses bases of eight instead of two. For instance, to convert the number `60` to its octal number counterpart we can check; does `512` go into `60`? Definitely not, nore does `64`. How many times does `8` go into `60`? `7` times, with `4` left over. How many times does `1`, or `8^0`, go into `4`? `4` times. This means that the decimal `60` is equal to an octal `74`. 

The table below gives a few more examples, where the orange numbers are the decimal numbers, and the numbers in the yellow table are octal:

<p align="center">
<img src="../../../../../../../assets/octal_conversion.png">
</p>


<strong>Hexadecimal Numbers</strong>

Hexadecimal numbers use a base of sixteen. This means that they use all of the ten digits from `0` to `9` plus six more letters, `A` to `F`. Therefore `A` will represent `10`, `B` is `11` and so on to `F` as `16`. 

The table below shows hexadecimal numbers in base-sixteen configuration. In order to convert `2A` to a decimal number it is `(2 * 16) + (1 * A)`. Remember, in the hexadecimal system, `A` represents `10` so the decimal number that represents the hexidecimal `2A` is `42`.

Conversely, let's convert the decimal number `2194` into a hexidecimal. Does `4096` go into `2194`? Nope, does `256`? Yes, `8` times, with a remainder of `146`. How many times does `16` go into `146`? `9` times, with a remainder of `2`. How many times does `1` go into `2`? Twice. So we have been given an `8`, a `9` and a `2`. The hexadecimal of `2194` is `892`.

<p align="center">
<img src="../../../../../../../assets/hexadecimal_table.png">
</p>

<strong>Elixir Shortcuts</strong>

Thankfully, Elixir gives us shortcuts in its interactive console to convert binary, octal and hexadecimal numbers into decimal numbers. Simply prefix your number with `0b` if it is binary, `0o` if it is octal or `0x` if it is hexidecimal, and the decimal counterpart will be produced.

{% highlight elixir %}
iex> 0b0101
#=> 5

iex> 0o3415
#=> 1805

iex> 0xE23AD
#=> 926637
{% endhighlight %}

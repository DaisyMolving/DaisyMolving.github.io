---
layout: post
title:  "Is And Isn't It True Or False"
date:   2016-01-16 12:29:31 +0000
---

<strong> Arithmetic and Comparison Operators </strong>

In Ruby, an expression or statement is made up of values and operators. 

Take a look at the equation `4 + 6 == 10`. Within this equation there is an arithmetic operator (`+`, `-`, `*`, `/` and `%`) and there is a comparison operator (`==`, `!=`, `>`, `<`, `>=`, `<=`, `<=>`, `===`). The above equation of `4 + 6 == 10` has a boolean value of `true`, because the expressions on either side of the `==` operator evaluate the same amount, as required by `==`. If we used a different comparison operator, and changed the equation to `4 + 6 < 10`, the equation now has a boolean value of `false`. 
These operators are very useful when we want a programme to perform certain actions based upon whether a condition is true or false. Lets take a look at what each of these operators mean:

<div align="center" style="margin-bottom: 30px;">
<table style="border-spacing: 0px; border: #111162 solid 2px;">
<tr>
<td style="width: 200px; padding: 10px; border: #111162 solid 1px; margin: 0px; color: #111162; background-color: #EEEEFF">Arithmetic Operator</td>
<td style="padding: 10px; border: #111162 solid 1px; margin: 0px; color: #111162; background-color: #EEEEFF">Means:</td>
</tr>
<tr>
<td style="padding: 10px; border: #111162 solid 1px; margin: 0px;">+</td>
<td style="padding: 10px; border: #111162 solid 1px; margin: 0px;">Adds</td>
</tr>
<tr>
<td style="padding: 10px; border: #111162 solid 1px; margin: 0px;">-</td>
<td style="padding: 10px; border: #111162 solid 1px; margin: 0px;">Subtracts</td>
</tr>
<tr>
<td style="padding: 10px; border: #111162 solid 1px; margin: 0px;">*</td>
<td style="padding: 10px; border: #111162 solid 1px; margin: 0px;">Multiplies</td>
</tr>
<tr>
<td style="padding: 10px; border: #111162 solid 1px; margin: 0px;">/</td>
<td style="padding: 10px; border: #111162 solid 1px; margin: 0px;">Divides</td>
</tr>
<tr>
<td style="padding: 10px; border: #111162 solid 1px; margin: 0px;">%</td>
<td style="padding: 10px; border: #111162 solid 1px; margin: 0px;">Modulus, this returns a value that is the remainder when one number is divided by another</td>
</tr>
</table>
</div>



<div align="center" style="margin-bottom: 30px;">
<table style="border-spacing: 0px; border: #111162 solid 2px;">
<tr>
<td style="width: 200px; padding: 10px; border: #111162 solid 1px; margin: 0px; color: #111162; background-color: #EEEEFF">Comparison Operator</td>
<td style="width: 500px; padding: 10px; border: #111162 solid 1px; margin: 0px; color: #111162; background-color: #EEEEFF">Means:</td>
</tr>
<tr>
<td style="padding: 10px; border: #111162 solid 1px; margin: 0px;">==</td>
<td style="padding: 10px; border: #111162 solid 1px; margin: 0px;">Is equal to</td>
</tr>
<tr>
<td style="padding: 10px; border: #111162 solid 1px; margin: 0px;">!=</td>
<td style="padding: 10px; border: #111162 solid 1px; margin: 0px;">Is not equal to</td>
</tr>
<tr>
<td style="padding: 10px; border: #111162 solid 1px; margin: 0px;">></td>
<td style="padding: 10px; border: #111162 solid 1px; margin: 0px;">Greater than</td>
</tr>
<tr>
<td style="padding: 10px; border: #111162 solid 1px; margin: 0px;"><</td>
<td style="padding: 10px; border: #111162 solid 1px; margin: 0px;">Less than</td>
</tr>
<tr>
<td style="padding: 10px; border: #111162 solid 1px; margin: 0px;">>=</td>
<td style="padding: 10px; border: #111162 solid 1px; margin: 0px;">Greater than or equal to</td>
</tr>
<tr>
<td style="padding: 10px; border: #111162 solid 1px; margin: 0px;"><=</td>
<td style="padding: 10px; border: #111162 solid 1px; margin: 0px;">Less than or equal to</td>
</tr>
</table>
</div>

Here we can see that the `!` acts as a negating character, and basically says 'is not' to the operator that it sits with. For instance `!>` would be the same as putting `<`.

<strong> Logical and Boolean Operators </strong>

Similarly `!`, or 'is not', can be used with booleans to create expressions such as `false == !true`. Other boolean operators are `and`: `&&`, as well as `or`: `||`. In an `&&` expression, <strong>both</strong> the right and left side must be `true` for the expression to be `true`. In an `||` expression, <strong>only one</strong> side must be `true` for the expression to be `true`.

<div align="center">
<div style="margin: 30px; display: inline-block;">
<table style="border-spacing: 0px; border: #111162 solid 2px;">
<tr>
<td style="border: #111162 solid 1px; border-right: none; padding: 10px; margin: 0px; color: #111162; background-color: #EEEEFF">AND</td>
<td style="width: 60px; border: #111162 solid 1px; border-left: none; padding: 10px; margin: 0px; color: #111162; background-color: #EEEEFF"></td>
</tr>
<tr>
<td style="padding: 10px; border: #111162 solid 1px; margin: 0px;">True && True</td>
<td style="padding: 10px; border: #111162 solid 1px; margin: 0px;">True</td>
</tr>
<tr>
<td style="padding: 10px; border: #111162 solid 1px; margin: 0px;">True && False</td>
<td style="padding: 10px; border: #111162 solid 1px; margin: 0px;">False</td>
</tr>
<tr>
<td style="padding: 10px; border: #111162 solid 1px; margin: 0px;">False && True</td>
<td style="padding: 10px; border: #111162 solid 1px; margin: 0px;">False</td>
</tr>
<tr>
<td style="padding: 10px; border: #111162 solid 1px; margin: 0px;">False && False</td>
<td style="padding: 10px; border: #111162 solid 1px; margin: 0px;">False</td>
</tr>
</table>
</div>


<div style="display: inline-block; margin: 30px;">
<table style="border-spacing: 0px; border: #111162 solid 2px;">
<tr>
<td style="border: #111162 solid 1px; border-right: none; padding: 10px; margin: 0px; color: #111162; background-color: #EEEEFF">OR</td>
<td style=" border: #111162 solid 1px; border-left: none; padding: 10px; margin: 0px; color: #111162; background-color: #EEEEFF"></td>
</tr>
<tr>
<td style="padding: 10px; border: #111162 solid 1px; margin: 0px;">True || True</td>
<td style="padding: 10px; border: #111162 solid 1px; margin: 0px;">True</td>
</tr>
<tr>
<td style="padding: 10px; border: #111162 solid 1px; margin: 0px;">True || False</td>
<td style="padding: 10px; border: #111162 solid 1px; margin: 0px;">True</td>
</tr>
<tr>
<td style="padding: 10px; border: #111162 solid 1px; margin: 0px;">False || True</td>
<td style="padding: 10px; border: #111162 solid 1px; margin: 0px;">True</td>
</tr>
<tr>
<td style="padding: 10px; border: #111162 solid 1px; margin: 0px;">False || False</td>
<td style="padding: 10px; border: #111162 solid 1px; margin: 0px;">False</td>
</tr>
</table>
</div>
</div>

<strong> Short Circuit Evaluation </strong>

Because Ruby operates with this logic if an `&&` equation is being evaluated and the first expression within it is `false`, then Ruby knows that the answer <strong>must</strong> be false, because an `&&` equation needs both sides to be `true` for the evaluation to be `true`. This is called short-circuit evaluation. In this case the second half of the equation is not evaluated to reach a conclusion.

The same goes for `||` statements, where if the first part of the equation is `true`, Ruby knows that the evaluation must be `true`. The second part of the equation is not evaluated, the evaluation is 'short-circuited'.

<strong> The Combined Comparison Operator </strong>

The combined comparison operator, or `<=>`, compares both sides or an equation and returns a value. If the first operand is greater than the second, the equation will evaluate to 1. If the first operand is equal to the second operand, the equation will evaluate to 0. If the first operand is lesser than the second operand, the equation is evaluate to -1. For instance:

`3 <=> 1` will evaluate to `1`
`3 <=> 3` will evaluate to `0`
`1 <=> 3` will evaluate to `-1`

---
layout: post
comments: true
published: false
title: "Exposing Duplication In TDD"
date: 2016-04-22 12:30:30 +0000
---

Ideally our code should be not only clear and functional, but also neat and concise. One element of this is avoiding duplication. Sometimes when we are building our code it is difficult to avoid writing the same thing twice or even three times, but we should be able to cut back duplicity at every milestone. If several blocks of code are doing the same, or similar, actions they can likely be consolidated into one action, and differences to a new method.

Testing our code can help us to remove duplication, by exposing it. In order to expose it completely it is very important that we are disciplined in following the T.D.D. guidelines. Uncle Bob has them as:

  1. You are not allowed to write any production code unless it is to make a failing unit test pass.
  2. You are not allowed to write any more of a unit test than is sufficient to fail; and compilation failures are failures.
  3. You are not allowed to write any more production code than is sufficient to pass the one failing unit test.

Let's look at an example of how this would work.

<strong> Coin-Changer Example </strong>

write tests first
<p align="center">
<img src="../../../../../../../assets/encouraging_dup_to_remove_it_tdd/coin_change_first_test.jpg">
</p>

just give him what he wants
<p align="center">
<img src="../../../../../../../assets/encouraging_dup_to_remove_it_tdd/just_give_him_what_he_wants.jpg">
</p>

if/else statements to encourage duplication
<p align="center">
<img src="../../../../../../../assets/encouraging_dup_to_remove_it_tdd/encouraging_duplication_if_else.jpg">
</p>

reducing dup in tests too
<p align="center">
<img src="../../../../../../../assets/encouraging_dup_to_remove_it_tdd/reducing_duplication_in_tests.jpg">
</p>

the more types of tests, the more interesting it gets
<p align="center">
<img src="../../../../../../../assets/encouraging_dup_to_remove_it_tdd/specs_for_multiple_coins.jpg">
</p>
<p align="center">
<img src="../../../../../../../assets/encouraging_dup_to_remove_it_tdd/amount_6_how_many_coins_repetition.jpg">
</p>

moving to while loops
<p align="center">
<img src="../../../../../../../assets/encouraging_dup_to_remove_it_tdd/while_loops_first_repeat.jpg">
</p>

repeat to three
<p align="center">
<img src="../../../../../../../assets/encouraging_dup_to_remove_it_tdd/repeat_to_three.jpg">
</p>

extracting values to an array, creating an each block
<p align="center">
<img src="../../../../../../../assets/encouraging_dup_to_remove_it_tdd/each_block_alongside_old_while_loops.jpg">
</p>

and finally!
<p align="center">
<img src="../../../../../../../assets/encouraging_dup_to_remove_it_tdd/coin_changer_final_state.jpg">
</p>


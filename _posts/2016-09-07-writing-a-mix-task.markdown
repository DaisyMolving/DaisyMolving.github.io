---
layout: post
comments: true
title: "Elixir: Writing a Mix Task"
date: 2016-09-07 10:30:30 +0000
---

Using a Mix Task is another way to run an Elixir application, instead of [using an escript][escript_mix_post]. A mix task belongs to the `Mix.Tasks` module and is given a name, so it can be run with the command `mix [task_name_here]`.

To create a mix task, you must first create a file with the chosen name of the task in your `lib` directory. In this case, we will be using it to run an application which finds the frequency of each word in the novel <i>Frankenstein</i>.

`touch lib/frankenstein.ex`

Within it we write the module name `Frankenstein` preceded by `Mix.Tasks`. In this way, the task belongs to the `Mix.Tasks.Frankenstein` module. Your file will look something like this:

<p align="center">
<img src="../../../../../../../assets/mix_task_setup.png">
</p>

The task imports from the module it needs to run, in this case `WordFrequencyFinder`. This means that it can use any of the functions within this module. The `run` function is specifically a `Mix.Task` function, and it runs the task with given arguments. In this case we pass it anything, with the `_` operator. The `run_frequency_search` function comes from the imported module, and takes two arguments, which are text files.

Now to run this mix task we must navigate to the parent directory and run `mix frankenstein`.


[escript_mix_post]:http://daisymolving.github.io/2016/08/08/running-an-elixir-file-with-mix.html

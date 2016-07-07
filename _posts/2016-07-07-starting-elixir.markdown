---
layout: post
comments: true
title: "Elixir: Beginning Functional Programming"
date: 2016-07-07 12:00:30 +0000
---

I have freshly started (today!) a student apprenticeship with [8th Light][8th-light-website] where I will be learning many new things, including three types of languages; one statically typed language, one dynamically typed language and one functional language. The functional language I am going to learn is called [Elixir][elixir-intro].

Functional Programming languages use expressions, and are declarative. They avoid mutability (the ability to change), which leads to fewer side-effects. Ideally your code should always return an expected output, and functional programming's reliance on mathematical functions eternally returning the same result when run allows this. I will not pretend that I understand a lot of the things that define functional programming, but that should all become clearer with time.

<strong>Getting Started</strong>

Elixir can be installed using `brew update` followed by `brew install elixir`, or by following the instructions on their [website][elixir-installation]. Elixir is build on top of Erlang, so brew should install both. You can check this by running `elixir -v` and `erl -v` to return their version numbers.

If you are using Vim, you can [configure][vim-config-post] your `~/.vimrc` file with the [Vim Elixir][vim-elixir-github] plugin.

<strong>The Elixir Console</strong>

The Elixir console can be accessed with the command `iex`. In this environment one can experiment with different types of Elixir expressions and help is only an `h` command away. In fact the documentation for every Elixir module can be accessed by using the help command with the module as an argument like so:

<p align="center">
<img src="../../../../../../../assets/iex_help_string.png">
</p>

Handy!

<strong>Learning with Koans</strong>

8th Light have written some [Elixir koans][elixir-koans-github] to help learn syntax, modules and data-types. In order to try them, `git clone` the url, `cd` into the freshly cloned directory, split your panes and run one with the instructions on the github readme, the other completing and saving each exercise within the `koans` directory in order. Each time you save the file the tests will run, and tell you whether you have aced it or not.

[8th-light-website]:https://8thlight.com/
[elixir-intro]:http://elixir-lang.org/
[elixir-installation]:http://elixir-lang.org/install.html
[vim-config-post]:http://daisymolving.github.io/2016/01/17/a-vim-config-post.html
[vim-elixir-github]:https://github.com/elixir-lang/vim-elixir
[elixir-koans-github]:https://github.com/elixirkoans/elixir-koans

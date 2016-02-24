---
layout: post
title: "Reconfiguring Tmux"
date: 2016-01-30 12:30:31 +0000
---

<strong> A Better Prefix Key </strong>

The first thing we are going to change is the prefix from `ctrl b` to `ctrl s`. If you haven't already you will need to change your `caps lock` key to become a newly minted `ctrl` key. There are instructions how to do this in this [Vim configuration post][vim-config-post]. In the tmux config file we must first tell tmux to stop using `ctrl b`. So the first thing we write is `unbind C-b`. The capital 'c' stands for `ctrl`. We then reset the prefix by inputting `set -g prefix C-s`. What that says is, "set, globally, the prefix to `ctrl` `s`".

Now save this file with the Vim command `:w`. To make tmux source this file every time it runs, and put your edits into action we must run `source-file`. This is something that we run in the tmux prompt, which we access with `prefix :` (right now your prefix will still be `ctrl b`). The prompt appears at the bottom of your shell. In it we will type `source ~/.tmux.conf` and press `enter`. Now the new prefix of `ctrl s` is active. Try it out, split a window into two panes!

<strong> Quicker Source File Loading </strong>

It is going to be a pain to have to write `source ~/.tmux.conf` every time that we change something and source it, so let's bind a key to automatically run that process. In the file write `bind-key r source-file ~/.tmux.conf \; display-message "~/.tmux conf reloaded"`. This is saying, "bind the key r to source the file that is `~/.tmux.conf` and when this is done display the message that it is reloaded". We must use `prefix :` and `source ~/.tmux.conf` once to get it started, but after that we will be able to use `prefix r` to reload the config file any time we like.

<strong> Forward Incremental Search </strong>

Before we made `ctrl s` the prefix, it was actually already a command in tmux called "Forward Incremental Search". What if we want to use this one day? We can input `bind-key -r C-s send-prefix`. This will send the prefix so that if we were to again type `ctrl s` it will now stand for forward incremental search. The `-r` means that instead of needing to type `ctrl s` twice every time that we want the forward incremental search to increment, we type the prefix once and then every single following `ctrl s` will increment.

<strong> Direction Keys </strong>

Have you noticed, when you have more than one pane in a window, that using `prefix o` to cycle around panes until you have reached your destination is a bit of a drag? We could bind keys to make new commands so that we can move up, down, left, right between panes. Super! 

Let's input `bind-key -n C-h select-pane -L`. This creates a command `ctrl h`, that selects a pane to the left. You will notice this matches the Vim direction commands. That's handy. The `-n` is allowing binding of keys without the needing the prefix first. The `-L` tag stands for "left". So knowing this we can also make `bind-key -n C-j select-pane -D` to use `ctrl j` to move down, `bind-key -n C-k select-pane -U` to use `ctrl k` to move up and `bind-key -n C-l select-pane -R` to use `ctrl l` to move right.

Now source the file, open multiple panes and try out your new commands!

<strong> Moving Within Tmux Pane </strong>

<strong> Stylin' </strong>
colours etc... status left length

<strong> Extra Features </strong>

battery and time

<p align="center">
<img src="../../../../../../../assets/config-tmux.jpg">
</p>

[vim-config-post]: http://daisymolving.github.io/2016/01/15/a-vim-config-post.html

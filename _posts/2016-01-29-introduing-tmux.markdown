---
layout: post
title: "Intro to Tmux and Some Helpful Configuration"
date: 2016-01-29 12:30:31 +0000
---

<strong> What is Tmux? </strong>

Tmux is a terminal multiplexer that allows you to run several panes, each running a different process, within one terminal window. It is really useful for running alongside Vim, so that you could feasibly spend all of your time programming solely in the terminal.

Here are a few examples where it rules:

Running `rspec` in the command line at the same time as using Vim to edit a spec and implementation file.

<p align="center">
<img src="../../../../../../../assets/tmux-example-rspec-rb-files.jpg">
</p>

Or, as I am doing writing this blog, where I am editing blog-post `.markdown` files in one pane, running `jekyll serve` on localhost:4000 (allows me to see page rendered) and using one pane to run irb in the command line, for verison control using git or listing `_post` files.

<p align="center">
<img src="../../../../../../../assets/tmux-example-post-edits-jekyll-serve.jpg">
</p>

<strong> Installing Tmux </strong>

To install tmux you must first install a package manager such as [homebrew][homebrew-install] and then run `brew install tmux`.

Run tmux by entering `tmux` into the command line. It's as easy as that! You will know that tmux is doing its thing because the title `tmux` will appear at the top of your window, and a coloured bar will appear at the bottom. 

<p align="center">
<img src="../../../../../../../assets/running-tmux.jpg">
</p>

<strong> Split a Window into Panes </strong>

Now that you have tmux running, let's have a little look at what it does. Tmux commands are prefixed by `ctrl b`. So in order to split a window horizontally into two panes type `ctrl b` and then `"`. To split that pane vertically in two, hit `ctrl b` and then `%`. How cool is that!

<strong> Understanding Tmux Objects </strong>

Now we have some split panes in tmux, it is important to know what we are looking at. The objects in tmux are called Session, Window and Pane. The Session is the session in which tmux is run. You began it when you typed `tmux` into the command line. Running only one Session per terminal shell is advisable. Each Session contains a Window. The Window is the view of all your processes. It is split into Panes. Each Pane within a Window usually runs a different process.

<p align="center">
<img src="../../../../../../../assets/tmux-objects.jpg">
</p>

<strong> Tmux Commands </strong>

Below is a list of some commands in tmux. Each command begins with the prefix, which currently is `ctrl b`.


<div align="center" style="margin-bottom: 30px;">
<table style="border-spacing: 0px; border: #111162 solid 2px;">
<tr>
<td style="width: 200px; padding: 10px; border: #111162 solid 1px; margin: 0px; color: #111162; background-color: #EEEEFF">Command</td>
<td style="padding: 10px; border: #111162 solid 1px; margin: 0px; color: #111162; background-color: #EEEEFF">Action</td>
<td style="width: 200px; padding: 10px; border: #111162 solid 1px; margin: 0px; color: #111162; background-color: #EEEEFF">Command</td>
<td style="padding: 10px; border: #111162 solid 1px; margin: 0px; color: #111162; background-color: #EEEEFF">Action</td>
</tr>
<tr>
<td style="padding: 10px; border: #111162 solid 1px; margin: 0px;">prefix c</td>
<td style="padding: 10px; border: #111162 solid 1px; margin: 0px;">new window</td>
<td style="padding: 10px; border: #111162 solid 1px; margin: 0px;">prefix ,</td>
<td style="padding: 10px; border: #111162 solid 1px; margin: 0px;">name window</td>
</tr>
<tr>
<td style="padding: 10px; border: #111162 solid 1px; margin: 0px;">prefix w</td>
<td style="padding: 10px; border: #111162 solid 1px; margin: 0px;">list windows</td>
<td style="padding: 10px; border: #111162 solid 1px; margin: 0px;">prefix f</td>
<td style="padding: 10px; border: #111162 solid 1px; margin: 0px;">find window</td>
</tr>
<tr>
<td style="padding: 10px; border: #111162 solid 1px; margin: 0px;">prefix &</td>
<td style="padding: 10px; border: #111162 solid 1px; margin: 0px;">kill window</td>
<td style="padding: 10px; border: #111162 solid 1px; margin: 0px;">prefix .</td>
<td style="padding: 10px; border: #111162 solid 1px; margin: 0px;">move window</td>
</tr>
<tr>
<td style="padding: 10px; border: #111162 solid 1px; margin: 0px;">prefix %</td>
<td style="padding: 10px; border: #111162 solid 1px; margin: 0px;">split pane horizontal</td>
<td style="padding: 10px; border: #111162 solid 1px; margin: 0px;">prefix "</td>
<td style="padding: 10px; border: #111162 solid 1px; margin: 0px;">split pane vertical</td>
</tr>
<tr>
<td style="padding: 10px; border: #111162 solid 1px; margin: 0px;">prefix o</td>
<td style="padding: 10px; border: #111162 solid 1px; margin: 0px;">swap panes</td>
<td style="padding: 10px; border: #111162 solid 1px; margin: 0px;">prefix q</td>
<td style="padding: 10px; border: #111162 solid 1px; margin: 0px;">show pane numbers</td>
</tr>
<tr>
<td style="padding: 10px; border: #111162 solid 1px; margin: 0px;">prefix x</td>
<td style="padding: 10px; border: #111162 solid 1px; margin: 0px;">kill pane</td>
<td style="padding: 10px; border: #111162 solid 1px; margin: 0px;">prefix [SPACE]</td> 
<td style="padding: 10px; border: #111162 solid 1px; margin: 0px;">toggle layouts</td>
</tr>
<tr>
<td style="padding: 10px; border: #111162 solid 1px; margin: 0px;">prefix d</td>
<td style="padding: 10px; border: #111162 solid 1px; margin: 0px;">detach</td>
<td style="padding: 10px; border: #111162 solid 1px; margin: 0px;">prefix t</td>
<td style="padding: 10px; border: #111162 solid 1px; margin: 0px;">big clock</td>
</tr>
<tr>
<td style="padding: 10px; border: #111162 solid 1px; margin: 0px;">prefix ?</td>
<td style="padding: 10px; border: #111162 solid 1px; margin: 0px;">list shortcuts</td>
<td style="padding: 10px; border: #111162 solid 1px; margin: 0px;">prefix :</td>
<td style="padding: 10px; border: #111162 solid 1px; margin: 0px;">prompt</td>
</tr>
</table>
</div>

You may have noticed that it is a little laborious using `ctrl b` as your prefix, as your hand needs to continuously move away from the home range on your keyboard. We are going to fix this problem, and to do that we must do some reconfiguration.


<strong> Reconfiguring Tmux </strong>

You can access your tmux config file with `vim ~/.tmux.conf`. This is where you will add to and edit your tmux configuration.

The first thing we are going to change is the prefix from `ctrl b` to `ctrl s`. If you haven't already you will need to change your `caps lock` key to become a newly minted `ctrl` key. There are instructions how to do this in this [Vim configuration post][vim-config-post]. In the tmux config file we must first tell tmux to stop using `ctrl b`. So the first thing we write is `unbind C-b`. The capital 'c' stands for `ctrl`. We then reset the prefix by inputting `set -g prefix C-s`. What that says is, "set, globally, the prefix to `ctrl` `s`".

Now save this file with the Vim command `:w`. To make tmux source this file every time it runs, and put your edits into action we must run `source-file`. This is something that we run in the tmux prompt, which we access with `prefix :` (right now your prefix will still be `ctrl b`). The prompt appears at the bottom of your shell. In it we will type `source ~/.tmux.conf` and press `enter`. Now the new prefix of `ctrl s` is active. Try it out, split a window into two panes!

It is going to be a pain to have to write `source ~/.tmux.conf` every time that we change something and source it, so let's bind a key to automatically run that process. In the file write `bind-key r source-file ~/.tmux.conf \; display-message "~/.tmux conf reloaded"`. This is saying, "bind the key r to source the file that is `~/.tmux.conf` and when this is done display the message that it is reloaded". We must use `prefix :` and `source ~/.tmux.conf` once to get it started, but after that we will be able to use `prefix r` to reload the config file any time we like.

<p align="center">
<img src="../../../../../../../assets/tmux-config.jpg">
</p>
[homebrew-install]: http://brew.sh/
[vim-config-post]: http://daisymolving.github.io/2016/01/15/a-vim-config-post.html

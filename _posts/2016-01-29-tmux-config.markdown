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

install [homebrew][homebrew-install] and then `brew install tmux`.

Run tmux by entering `tmux` into the command line. It's as easy as that! You will know that tmux is doing its thing because the title of your window will say `tmux` and there will be a bar at the bottom of your window too. 

<p align="center">
<img src="../../../../../../../assets/running-tmux.jpg">
</p>

<strong> Split a Window into Panes </strong>

(default prefix is ctrl b) then " for vert split and % for horizontal split

tmux objects - session, window, pane

list of some commands

reconfiguring tmux

using prefix [ and the up and down j,k keys to look at spec errors in terminal etc

battery bar and time (hey wait, it's those time literals!)

[homebrew-install]: http://brew.sh/

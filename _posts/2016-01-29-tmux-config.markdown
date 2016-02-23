---
layout: post
title: "Intro to Tmux and Some Helpful Configuration"
date: 2016-01-29 12:30:31 +0000
---

<strong> What is Tmux? </strong>

Tmux is a terminal multiplexer that allows you to run several panes, each running a different process, within one terminal window. It is really useful for running alongside Vim, so that you could feasibly spend all of your time programming solely in the terminal.

Here are a few examples where it rules:

Running `rspec` in the command line at the same time as using Vim to edit a spec and implementation file.

<p align="center"><img src=""></p>

Or, as I am doing writing this blog, where I am editing blog-post `.markdown` files in one pane, running `jekyll serve` on localhost:4000 (allows me to see page rendered) and using one pane to run irb in the command line, for verison control using git or listing `_post` files.
why tmux is great, especially alongside vim

<p align="center"><img src=""></p>

<strong> Installing Tmux </strong>

installing tmux

using tmux

tmux objects - session, window, pane

commands

reconfiguring tmux

using prefix [ and the up and down j,k keys to look at spec errors in terminal etc

battery bar and time (hey wait, it's those time literals!)



<strong> Reconfiguring Tmux </strong>

You can access your tmux config file with `vim ~/.tmux.conf`. This is where you will add to and edit your tmux configuration.

The first thing we are going to change is the prefix from `ctrl b` to `ctrl s`. If you haven't already you will need to change your `caps lock` key to become a newly minted `ctrl` key. There are instructions how to do this in this [Vim configuration post][vim-config-post]. In the tmux config file we must first tell tmux to stop using `ctrl b`. So the first thing we write is `unbind C-b`. The capital 'c' stands for `ctrl`. We then reset the prefix by inputting `set -g prefix C-s`. What that says is, "set, globally, the prefix to `ctrl` `s`".

Now save this file with the Vim command `:w`. To make tmux source this file every time it runs, and put your edits into action we must run `source-file`. This is something that we run in the tmux prompt, which we access with `prefix :` (right now your prefix will still be `ctrl b`). The prompt appears at the bottom of your shell. In it we will type `source ~/.tmux.conf` and press `enter`. Now the new prefix of `ctrl s` is active. Try it out, split a window into two panes!

It is going to be a pain to have to write `source ~/.tmux.conf` every time that we change something and source it, so let's bind a key to automatically run that process. In the file write `bind-key r source-file ~/.tmux.conf \; display-message "~/.tmux conf reloaded"`. This is saying, "bind the key r to source the file that is `~/.tmux.conf` and when this is done display the message that it is reloaded". We must use `prefix :` and `source ~/.tmux.conf` once to get it started, but after that we will be able to use `prefix r` to reload the config file any time we like.

<p align="center">
<img src="../../../../../../../assets/tmux-config.jpg">
</p>
[vim-config-post]: http://daisymolving.github.io/2016/01/15/a-vim-config-post.html

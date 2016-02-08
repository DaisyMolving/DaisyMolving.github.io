---
layout: post
title:  "Some Vim Configuration"
date:   2016-01-15 12:29:31 +0000
---

Vim is here to help speed up your process of editing files and running processes, and with a little configuration one can make it look and act exactly as desired. After installing Vim we can configure a vimrc file. When first accessed, it may be empty. Type `vim ~/.vimrc` into your terminal to open it. So far mine looks like this:

<p align="center">
<img src="../../../../../../../assets/vimrc_file.jpg">
</p>

I have used a Vim plugin manager called [Vundle][vundle-github], this is in order to install, update and manage my plugins. The first 4 lines of the file are required to set up Vundle. 

Following this are my plugins. All of these pictured, and many more useful plugins, can be found on Github. [Syntastic][scrooloose_syntastic] checks for syntax errors, [Vim-Ruby][vim-ruby-github] contains configuration files for editing and compiling Ruby within Vim, [Endwise][endwise-github] automatically adds `end` to Ruby methods, conditionals and loops where it is required, [Supertab][supertab-github] allows you to use `<tab>` key to complete words as you might for finding files and directories in the terminal, [Vim-Commentary][vim-commentary-github] is a plugin that allows you to comment out sections using `gcc` and takes a count for the amount of lines, [Vim-Rspec][vim-rspec-github] runs Rspec within Vim and [Ctrl-P][ctrl-p-github] allows you to search within Vim files.

The objective of using Vim is to save a considerable amount of time spent on moving around the keyboard and computer display. Therefore another very handy keyboard configuration is to change the `<caps lock>` key to `<ctrl>` in order to keep your hands comfortably in the home range. From now on all your capitalisation will be achieved with `<shift>` instead, and whenever you need to use a command you can just slide lil' left pinkie over to your newly minted `<ctrl>` key, no worries. On a Macintosh system this can be changed within system preferences:

<p align="center">
<img src="../../../../../../../assets/change_caps_lock_to_ctrl.jpg">
</p>

Now you are all set...

<p align="center">
<img src="https://s.yimg.com/ny/api/res/1.2/yu3L92jNn_JavuhoDZHpjA--/YXBwaWQ9aGlnaGxhbmRlcjtzbT0xO3c9NTAwO2g9MjEy/http://l.yimg.com/cd/diminuendo/1.0/original/23a7d58f5cd5ea3ab7dfc01677aee0981df94b3f.gif">
</p>


[vundle-github]: https://github.com/VundleVim/Vundle.vim
[scrooloose_syntastic]: https://github.com/scrooloose/syntastic
[vim-ruby-github]: https://github.com/vim-ruby/vim-ruby
[endwise-github]: https://github.com/tpope/vim-endwise
[supertab-github]: https://github.com/ervandew/supertab
[vim-commentary-github]: https://github.com/tpope/vim-commentary
[vim-rspec-github]: https://github.com/thoughtbot/vim-rspec
[ctrl-p-github]: https://github.com/kien/ctrlp.vim

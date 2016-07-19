---
layout: post
comments: true
title: "Ruby: Layout of Your Application"
date: 2016-04-20 12:30:30 +0000
---

Not only does the design of your application matter in terms of how all objects work together and apart, but also the directory structure and readme are very important. Hopefully someone other than yourself might want to navigate your files and look at your code, and crucially, be able to understand from your readme file how to execute your code and what your intentions were. 

<strong> Directory Structure </strong>

The layout of your directories should be just as sensible as the code itself. Group together things that should be together in appropriate directories, starting broadly and getting more specific. For instance, the main.rb, which will be the entry point for executing your application will be at the top level, as will your readme, the instructions on how to execute the code. Then your code library will be in one directory, and your test specifications in another. Within each of these directories there should be directories grouping any appropriate classes together. Running `tree` command might show it as something like this:

<p align="center">
<img src="../../../../../../../assets/file_tree_tic_tac.jpg">
</p>

<strong> Main.rb </strong>

The `main.rb` file is called your entry point. Wikipedia describes it as "where control is transferred from the operating system to a computer program, at which place the processor enters a program or code fragment and execution begins." In Ruby, we create a file in which we execute each class or module step by step using a code snippet to run these processes. We could instantiate, say, the `Game` class, and call start upon it, which in turn instantiates all other classes, running them in the order needed. It might look as simple as this:

<p align="center">
<img src="../../../../../../../assets/main_file_tic_tac.jpg">
</p>

<strong> Writing the Readme </strong>

When writing a readme file it is important to make it both concise and engaging. You want the reader to get jazzed about using your software, or interested in helping you to improve it! Not only is the content important, but remember it will likely be viewed on a browser (say on Github) so use html or markdown language to create headings, paragraphs, bold text or anything else that applies.

Here are some basic content-to-include steps:

1. Your name, the name of your software, the date last updated and a way of contacting you if applicable
2. Basic description of what the software does
3. Basic installation/running requirements/steps
4. More in depth description of the programme and what it does
5. What the programme fails to do if applicable (maybe you didn't quite achieve what you hoped, or have some bugs!) with code snippets where needed)
6. Plans for the future, features to add, bugs to fix.
7. Any copyright information if applicable.

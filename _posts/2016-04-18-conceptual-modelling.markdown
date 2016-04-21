---
layout: post
comments: true
title: "Conceptual Modelling Based on SOLID"
date: 2016-04-18 12:30:30 +0000
---

When using the SOLID principles in your Ruby software it is important to consider them before you begin, and also at each milestone, in order to ensure that your programme remains pliable. It is good to think about what your programme might look like before you dive into it, in order to know where to begin and how to test each behaviour. However, do not over-design, as functionality may change as you write, and having too strong an idea of where you <i>wanted</i> to go can sometimes stop you from going where you <i>should</i>.

<strong>Where to Start?</strong>

Think about what it is that your application will do. If you were to write a basic "story" of the main actions of your software what would it look like? Let's think about the game Tic Tac Toe, or Noughts and Crosses.

<p align="center">
<img src="../../../../../../../assets/story_of_tic_tac.jpg">
</p>

Now looking at this story we could look for any obvious repeated nouns that would seem to be classes. We can underline or highlight them to make them more obvious. Some parts of our story give us repeated actions that don't clearly belong in one of those classes, so we can highlight them too:

<p align="center">
<img src="../../../../../../../assets/story_of_tic_tac_class_nouns.jpg">
</p>

From this we have a basic idea of our different classes, `Game`, `Board`, `Player`, `Position`. What about those repeated actions? What class do they belong to? It seems that they read and write. So therefore we should also have a `Reader` and a `Writer`.

<strong>Thinking about Responsibilities</strong>

Have a quick think about what responsibility each class will have, and make sure that each has a sole purpose. If not we may need to think about splitting classes or creating new ones. 

<i> Game </i>: Runs game by displaying and soliciting.

<i> Board </i>: Updates score by updating and reading grid.

<i> Player </i>: Places marker by selecting position on grid.

<i> Position </i>: Has value that can be changed to player's marker value, once.

<i> Reader </i>: Reads inputs.

<i> Writer </i>: Writes outputs.

Be careful to ensure classes do not gain extra responsibilities that are not related to their core purpose. 

<strong>Thinking about Relationships</strong>

If it helps you to understand you might wish to draw a small diagram to illustrate the relationships between classes, like so:

<p align="center">
<img src="../../../../../../../assets/flow_of_control_tic_tac_classes.jpg">
</p>

However you should think about developing each class individually to its fullest capacity in your code before creating unnecessary dependencies between classes.

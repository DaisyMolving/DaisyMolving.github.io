---
layout: post
title: "The Importance of OCP and How Polymorphism Can Acheive It"
comments: true
date: 2017-01-20 10:30:30 +0000
---

I have recently been learning Java, and attempting to write TicTacToe in a clean and concise way. I have found this a challenge, and have made many mistakes that have led me to further appreciate the SOLID principles, particulary the [Open/Closed Principle][open-closed-post]. 

The Open/Closed Principle states that your application should be open to extension and closed to modification. This means that it ought be written in such a way that if a feature is added, or a class is extended, existing code needn't change. An indication that this principle has not be followed is when a change in one part of your application prompts changes in several other places. I created such a problem in my TicTacToe application.

Below is a class called `Session`. The purpose of `Session` is to set up a game by creating the players with which to initialise the Game class. In order to create players, the method `createPlayersOfType` takes a string response of `"a"`, `"b"`, `"c"` or `"d"` to prompt the `playerCreator` to initialise players of a certain class. 

<p align="center">
<img src="../../../../../../../assets/java_session_class_ttt.png">
</p>

The problem with this `if/else` block in `Session` for player creation is that if we wanted to add another option, such as a `RandomComputerPlayer` vs an `UnbeatablePlayer`, we would have to change something in the `Session` class, the `PlayerCreator` class, the `Messenger` class and the `Validation` class. A small change in one class would affect several others. This clearly violates the Open/Closed Principle.

<strong>So how can we fix it?</strong>

<p align="center">
<img src="../../../../../../../assets/pathsBetweenClasses.png">
</p>

Above is a rough diagram of the paths between class methods needed to instantiate a Game with certain types of players. We need to think of a way that a change to one of these methods won't trigger a change in all the other classes. `Session` should not know about the different options available for creating different player types. This responsibility should belong to our `playerCreator`.

So first of all we should remove knowledge of the game options from Session, by removing the if/else block. Session should simply make a call to playerCreator to create the correct type of players, as below:

<p align="center">
<img src="../../../../../../../assets/session-without-if-else.png">
</p>

Now we can think of a way that `playerCreator` can use different `userResponse` to create players without using an if/else block. One solution is to create a hashmap, where the keys are different options and the values contain two players of the correct type. Below is an example of a hashmap called `gamePlayerOptions`. If there are ever more game options added we need simply to add it to the hashmap shown in the constructor.

<p align="center">
<img src="../../../../../../../assets/game-options-hashmap-in-player-creator.png">
</p>

<strong>What about Validation?</strong>

We have now removed knowledge of the game options from `Session`, but that knowledge still exists in the `playerCreator`, the `Validator` and the `Messenger`. Does the `Validator` need to know about the game options in order to validate? We could instead pass the required regex to match against the game options to the `Validator` at the time we use them. This means that the `playerCreator` needs to know what the match requirements are but the `Validator` need not.

<p align="center">
<img src="../../../../../../../assets/validate-with-match-from-player-creator.png">
</p>

Above we have requested a response from the `Validator` by passing it the user input, the match requirements regex and the invalid message from the `Messenger` specific to the game options of the `PlayerCreator`. 

Now if there are any new game options added it is the `PlayerCreator` that knows about new options and a changed match requirement, but not the `Validator` at all. The amount of places that need to be changed by a new option has halved from when we started!

<strong>Removing Game Option Knowledge from Messenger Class</strong>

What if we wanted to only have knowledge of the game options in the `PlayerCreator` and nowhere else? We can use another data structure to store the possible options and just pass them to the `Messenger` when it is time to list them.

First we would create a `List<String>` to store all the strings of options, like so:

<p align="center">
<img src="../../../../../../../assets/add-list-of-game-options-as-menu.png">
</p>

However, the user is initially prompted for a response to the game options in the `Session` class. This prompt should instead be introduced in the `PlayerCreator` class. The `PlayerCreator` passes the `Messenger` method `askGameType` the list of options that it stores.

In the `PlayerCreator` class:


<p align="center">
<img src="../../../../../../../assets/PlayerCreator-menu-setup.png">
</p>

And in the `Messenger` class:

<p align="center">
<img src="../../../../../../../assets/Messenger-game-option-set-up.png">
</p>

[open-closed-post]:http://daisymolving.github.io/2016/03/15/open-closed-principle.html

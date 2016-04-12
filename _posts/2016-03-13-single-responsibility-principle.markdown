---
layout: post
comments: true
title: "SOLID: Single Responsibility Principle"
date: 2016-03-13 12:30:30 +0000
---

<strong> Why Should We Use the Single Responsibility Principle in OOP (and Other S.O.L.I.D Principles)? </strong>

Object Oriented Programming is especially useful when we start to model larger applications, where we will have multiple classes each responsible for separate objects and multiple methods within each of those classes. We should us OOP to help us acheive maximum clarity and reusability, as well as minimal fragility and sluggishness in our programme. But what does this mean? And How might we go about this? 


If code is clear it is easy for anyone else looking at it to understand what each part is doing. If code is reusable it is not so bound to the particular programme that we are writing that we may in the future be able to apply the same code to alternative problems. Code is not fragile when it is not easy to break, and often is fragile due to different classes or methods becoming very dependent on each other, for instance if a function within Class A depends very heavily on something to be at a certain state in Class B, perhaps anything you alter in Class B can break Class A. What a pain! One thing that we can do in order to be more confident in our code is to look at the responsibilities of each part of our application, and then think about their relationships. This is often referred to as applying the Single Responsibility Principle.

<strong>Single Resposibility Principle in Methods </strong>

When writing a method, it should ideally be created to have only one responsibility or purpose, one reason to exist. You can use your test suite to help you with this. For instance you may have many tests for one method, but all should be testing the same type of information, and looking for the same type of outcome. If it is not, then it would seem that this method has more than one responsibility. Another way to look at this is to describe aloud or on paper what the responsibility of each method is. If there are any descriptions that involve the word 'and', and you cannot strongly justify why, then you may be violating the Single Responsibility Principle. 

The method should be named in such a way that describes what the responsibility is very specifically. It should convey the action that the method is performing in a way that is clear and succinct.

<strong> S.R.P in Classes </strong>

Just as methods should have one reason to exist, so too should classes. A class can have multiple behaviours, but all of these behaviours should support the class responsibility. Robert "Uncle Bob" Martin says, "Gather together the things that change for the same reasons, seperate things that change for different reasons". This is a good rule to remember when creating classes. Any anomolous methods are usually better suited to their own class, or in a different pre-existing class. The aim is to find a way that all methods and classes can exist in their current model in a way that makes sense. Classes that have only one responsibility, like single-responsibility methods, are easily re-used. They are also much easier to test, they can be faster because there are fewer dependencies.

<strong>Wait, So What is This SOLID Stuff? </strong>

The Single Responsibility Principle is the first principle in Robert Martin's SOLID principles. SOLID is an acronym for 5 principles that act as useful guidelines for acheiving well-ordered and coherent applications, that are easily maintainable and scaleable. The S.O.L.I.D. letters stand for:

Single Responsibility Principle
Open/Closed Principle
Liskov's Substitution Principle
Interface Segregation Principle
Dependency Inversion Principle

Read the next few posts to find out more about the rest!

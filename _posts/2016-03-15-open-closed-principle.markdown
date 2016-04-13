---
layout: post
comments: true
title: "SOLID: Open/Closed Principle"
date: 2016-03-15 12:30:30 +0000
---

<strong> What is the Open/Closed Principle? </strong>
	
The Open/Closed Principle is the 'O' in the SOLID principles, by Robert "Uncle Bob" Martin. It states that, "an object should be open to extension, but closed to modification". That is, if new requirements arise for the programme, you would be able to write <i>new code</i> for those requirements, rather than haveing to change the existing, working code. You are changing the behaviour, without changing the code.

<strong> What does that mean? </strong>

Let's say you have built an e-commerce type site, and this need to process payments. You might decide to use the payment processor Stripe to help you with this. You set it up, and Stripe is working wonderfully. One day your manager asks you to change from using Stripe, to using a new payment processor. No problem! All you need to do is find every method in your code that relies on Stripe and change it. But wait, where you have removed your `Stripe` keyword to replace it with your new term, it has broken other parts of your code that relied on it. And then you had to set about fixing <i>them</i>. That takes quite a while... Because there are so many places that you need to remove `Stripe` and add your new term! And therefore so many methods that depend on `Stripe`! And then you found that you had to change all your tests that they now specify for `NewProcessor` rather than `Stripe`.

And all that time that it took to switch over none of our customers could process payments, when it should have been so simple!

We violated the Open/Closed Principle, and it makes us very worried now about any future parts we need to change... So let's fix it.

<strong> Using the Open/Closed Principle </strong>

This is achieved with [Abstraction][oop-principles-post]. We abstract the dependency to be taken as a parameter called `payment_processor`, upon which the `charge_customer` method can be called. We also have made a PaymentProcessor class, that Stripe class inherits from, so when we need to switch to a new payment processor, we can write it as a new class that also inherits from PaymentProcessor. In this way we are writing new code to make a change, without having to edit our existing code. Now the `charge` method does not care what the `payment_processor` object is, it knows nothing about it, only passes it through a mehtod. In the method it calls charge on that object, and the payment_processor exists/extends elsewhere.

See how you can <i>extend</i> the class, by injecting a different payment processor, without <i>modifying</i> the class.


[oop-principles-post]:http://daisymolving.github.io/2016/02/17/introduction-to-OOP.html

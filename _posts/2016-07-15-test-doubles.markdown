---
layout: post
comments: true
title: "Test Doubles"
date: 2016-07-15 12:00:30 +0000
---

Test doubles are like stunt doubles, they are types of tests that contain placeholders for the real thing. We would use test doubles when the real thing does not exist yet or we do not yet need it, but they are most useful so that we can isolate the unit we are testing. This decreases dependency and coupling in our code. There are five different types.

<strong>What is a Dummy?</strong>

A dummy is a fill-in used to satisfy the compile-time check and run-time execution. They are passed around but never actually used. An example could be when you would pass a null value into a method or function that you are testing, because you are testing the other values that the method acts upon, or testing different methods that depend on the given method and don't use its parameters.

If I am creating an echo server, a programme that <i>reads</i> inputs from the user and repeats them (<i>writes</i> them to the console), I might create a `UI` class which takes a `Reader` class and a `Writer` class as arguments. The first thing that the echo server does when run is greets the user, it writes the console without needing to read anything yet. We might write our test like this (in Ruby):

{% highlight ruby %}
require 'reader'
require 'writer'
require 'ui'

describe UI do

  it 'prints a welcome message to console' do
    writer = Writer.new
#The reader is not yet needed for this test so we pass in a dummy, as nil
    reader = nil
    echo_server = UI.new(reader, writer)
    expect(echo_server.message_printed).to eq "Welcome\n"
  end
end
{% endhighlight %}

You can see the dummy as the `nil` value being passed in where the `reader` would usually go. A dummy is used when you must pass an argument, but you know that the argument will never be used.

<strong>What is a Stub?</strong>

A stub is passed in as a proper value, for instance it returns true or false. It could be used when a method or function must return true or false in order for you to be able to test another part of your programme. Stubs do not respond to anything programmed outside the test, meaning that the real method or function in the implementation file is not used, it is the stub value that is used.

An example would be when you are testing that a `User` is logged in to your website before they can change their password. You won't want to provide your test with login details and <i>actually log in</i> every time the test runs, it is much simpler to use a stub like so:

{% highlight ruby %}
describe User do
  it 'allows user to change password' do
    user = User.new("Sally", "passWord123")
#the stub is the value given to is_logged_in
    is_logged_in(true)
    expect(user.can_change_password).to eq true
  end
end
{% endhighlight %}

<strong>What is a Spy?</strong>

A spy is a test double that checks that a method or function has been called. It "spies" on your program to see what methods are being actioned by your system but is not concerned with their output. This is helpful, because sometimes we want to ensure that functions are being called without wanting the action itself to take place every time the test suite is run.

An example of this is if you were testing that a customer will receive a confirmation email when they register to your site. You would want to check that `send_confirmation_email` has been called, but not for it to actually send an email as part of the test. You only want the email to be sent in the real circumstance, especially if you are paying for the service.

{% highlight ruby %}
describe RegistrationConfirmation do

  it 'sends a confirmation email to customer upon registration' do
    new_registration = RegistrationConfirmation.new("Barry", "PasswordSecret123")
#the spy method confirm_email_sent checks that send_confirmation_email was called:
    expect(new_registration.confirm_email_sent).to eq true
  end
end
{% endhighlight %}

<strong>What is a Fake?</strong>

A fake is a fake value passed into the test to simulate a <i>real</i> situation. It gives the test fake data in the same way that there would be real data given in the actual circumstance. It tests the methods or functions you are passing it into to act in the expected way for the particular data that you gave it.

An example of when you might use a fake could be when you are making a tic-tac-toe/nought and crosses game, where the board is usually passed an unmarked grid upon initialization, but you want to test how it would act upon a board that has been marked to make the game end (i.e. when someone wins). You would pass the board class some fake data, for instance an array where there are three noughts or crosses in a row:

{% highlight ruby %}
describe Board do

  it 'finds a winner for three x in a row' do
#look at how the fake_board below is an instance of the Board class 
#that has been passed fake data to test methods:
    fake_board = Board.new(%w(1 2 3 x x x 7 8 9))
    expect(fake_board.end_of_game?).to eq :winner
  end

end
{% endhighlight %}
[Steve Hostettler][steve-hostettler-blog] writes in his blog, "The most common reasons for using fake objects is that the real component is not available yet, is too slow or cannot be used during tests because of side effects"

<strong>What is a Mock?</strong>

A mock is a test double that knows what it is testing, it verifies itself. This means that it spies on the module or class that you are testing and knows what behaviour to expect. An example of a mock that is testing the way that a `UI` class prints the `Board` class information is below. The `Board` is passed fake data, then the mock spies on the writer to check that it behaves as expected, before calling the `print_rows` method from the `UI` class that will make the test pass.

{% highlight ruby %}
require 'ui'
require 'reader'
require 'writer'
require 'board'

describe UI do
  let (:stream) { StringIO.new }
  let (:reader) { Reader.new(stream) }
  let (:writer) { Writer.new(stream) }
  let (:ui) { UI.new(reader, writer) }

  it 'takes board and prints it correctly as three lines of three' do
    fake_board = Board.new(%w(1 2 3 4 5 6 7 8 9))
    expect(writer).to receive(:put_line).with "1 2 3"
    expect(writer).to receive(:put_line).with "4 5 6"
    expect(writer).to receive(:put_line).with "7 8 9"
    ui.print_rows(fake_board)
  end
end
{% endhighlight %}

[Martin Fowler][martin_fowler_test_doubles] writes that, "Mock objects are pre-programmed with expectations that form a specification of the calls they are expected to receive."

[steve-hostettler-blog]:http://www.hostettler.net/blog/2014/05/18/fakes-stubs-dummy-mocks-doubles-and-all-that/
[martin_fowler_test_doubles]:http://www.martinfowler.com/bliki/TestDouble.html

---
layout: post
comments: true
title: "Elixir: Testing Input and Output"
date: 2016-09-10 10:30:30 +0000
---

Inputs and outputs are collected and printed by an application at runtime. This could mean running your programme to pass an input or check the printout every time you run a test. Fortunately Elixir provides a module to test input/output which doesn't require running the application. Inputs can be provided and outputs checked with a module called CaptureIO.

CaptureIO is functionality provided by ExUnit, a testing framework for Elixir. You will notice that Elixir test files use ExUnit.Case, like so:

{% highlight elixir %}
defmodule ProjectNameTest do
  use ExUnit.Case

  test "does something" do
    assert ProjectName.do_something == "did it!"
  end

end
{% endhighlight %}

When we want to use CaptureIO we must import it at the top of our file; just as we `use ExUnit.Case`, we must `import ExUnit.CaptureIO`. Now we are ready to write tests. 

<strong>Testing Output</strong>

Testing output uses a `capture_io` function like so:

{% highlight elixir %}
defmodule ProjectNameTest do
  use ExUnit.Case
  import ExUnit.CaptureIO

  test "prints something capitalized" do
    assert capture_io(fn ->
      ProjectName.print_something_capitalized("hello")
    end) == "Hello"
  end
end
{% endhighlight %}

The function calls the `print_something_capitalized/1` function, and expects the output to be the capitalized argument. You can see here how CaptureIO captures the output of the entire function and compares it to the string outside of itself.

<strong>Testing Input</strong>

Testing input can be complex in other languages, but CaptureIO gives us two ways to test this. We would write a test the same as the one above, but simply pass it an input. We will then need to print this input and capture it in order to check that assertions pass. For instance:

{% highlight elixir %}
defmodule ProjectNameTest do
  use ExUnit.Case
  import ExUnit.CaptureIO

  test "takes an input" do
    assert capture_io("mary", fn ->
      IO.write ProjectName.get_name
    end) == "What is your name?\n mary"
  end
end
{% endhighlight %}

The test above would test a function something like this:
{% highlight elixir %}
defmodule ProjectName do

  def get_name do
    IO.gets("What is your name?\n")
  end

end
{% endhighlight %}

See how the `get_name` function does not need to take an input as an argument for effective input testing, and with CaptureIO we can test the `IO.gets` directly. Because the `IO` here includes the prompt statement, our test returns the prompt as well as the input. If we would prefer to isolate the input there is another type of CaptureIO test we could write:

{% highlight elixir %}
defmodule ProjectNameTest do
  use ExUnit.Case
  import ExUnit.CaptureIO

  test "takes a name input" do
    assert capture_io([input: "mary", capture_prompt: false], fn ->
      IO.write ProjectName.get_name
    end) == "mary"
  end
end
{% endhighlight %}

Here we have passed the CaptureIO function an input as well as telling it not to capture the prompt from the IO.gets. This is very useful when we need to only test that a input, or a series of inputs, has been returned. Sometimes however it is useful to keep track of the prompts in our testing, such as when we are testing behaviour in recursive functions, when output depends on input.

<strong>Testing Output that Depends on Input</strong>

If I have a function that verifies an input, it might include a conditional that prints a celebratory reply when the input is correct, otherwise retries/recurses. An example could be if I wanted to verify that a name input by the application user does not contain any numbers, only letters are allowed. If the input name is found to contain numbers then the user must try again. The function in question might look something like:

{% highlight elixir %}
defmodule ProjectName do

  def verify_name do
    verify_name(IO.gets("What is your name?"), ~r/([a-z A-Z]+)/, "Please input a name that has only letters: ")
  end

  def verify_name(name_input, accepted_name, failure) do
    if String.match?(name_input, accepted_name) do
      IO.puts("Thanks #{user_input}!")
    else
      verify_name(IO.gets(failure), accepted_name, failure)
    end
  end

end
{% endhighlight %}

The function `verify_name/0` calls `verify_name/3` with a request for an input, a regex expression to match that input to, and a failure message to recurse with every time the regex match fails. We would like to write a test that checks both branches of the conditional, so we would like to give the test multiple inputs. The test might look like this:

{% highlight elixir %}
defmodule ProjectNameTest do
  use ExUnit.Case
  import ExUnit.CaptureIO

  test "prints failure message until name is verified" do
    assert capture_io("!@£123\nDaisy", fn ->
      ProjectName.verify_name
		end) == "What is your name? Please input a name that has only letters: Thanks Daisy!\n"
  end
end

{% endhighlight %}

The test above is given two inputs, one failing input and one accepted input. How might we give a test two inputs? In Elixir CaptureIO tests it is as simple as seperating two inputs with a newline escape character (`\n`). The function `verify_name` is not printed inside the CaptureIO function, and so here, unlike the tests above, the input is not printed. We are more concerned here that each conditional branch has printed the correct message on the relevant input, and so we are using input to test output.

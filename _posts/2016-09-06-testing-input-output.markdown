---
layout: post
published: false
comments: true
title: "Elixir: Testing Input and Output"
date: 2016-09-06 10:30:30 +0000
---

Inputs and outputs are collected and printed by an application at runtime. This could mean running your programme to pass an input or check the printout every time you run a test. Fortunately Elixir provides a module to test input/output which doesn't require running the application. Inputs can be provided and outputs checked with a module called CaptureIO.

CaptureIO is functionality provided by ExUnit, a testing framework for Elixir. You will notice that Elixir test files use ExUnit.Case, like so:

{% highlight elixir %}
defmodule ProjectNameTest do
  use ExUnit.Case
  doctest ProjectName

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
  doctest ProjectName

  test "prints something capitalized" do
    assert capture_io(fn ->
      ProjectName.print_something_capitalized("hello")
    end) == "Hello"
  end
end
{% endhighlight %}

The function calls the `print_something_capitalized/1` function, and expects the output to be the capitalized argument. You can see here how CaptureIO captures the output of the entire function and compares it to the string outside of itself.

<strong>Testing Input</strong>

Testing input can be

<strong>Testing Output that Depends on Input</strong>

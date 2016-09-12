---
layout: post
comments: true
title: "Elixir: The Pipe Operator"
date: 2016-09-02 10:30:30 +0000
---

Elixir provides a helpful operator for piping functions together. It is particularly useful for providing clarity in an application that performs a long chain of tasks. By using the pipe operator, `|>`, we take the return of each function and pass it to the next. For example, we have written an application that takes a large text and counts how many times each word appears, printing the result from most frequent to least frequent. We split the words into a list, then pass this list to a function which removes uninteresting words (like "a", "and", "the", etc.), then pass this to a function which counts the frequency, then pass this to a function that prints the outcome. It might look like this (cue horizontal scroll bar, it's going to be long!):

{% highlight elixir %}

def run_frequency_search(text, uninteresting_words) do
  print_outcome(tally_word_frequency(remove_uninteresting_words(split_words(text), split_words(uninteresting_words))))
end

{% endhighlight %}

Sure, that works fine, but it is very difficult to read, and also unclear as to what is happening. Good code should be easy to read and require minimal explanation. That is why the pipe operator is so useful. Observe the comparison below:

{% highlight elixir %}

def run_frequency_search(text, uninteresting_words) do
  split_words(text)                             
  |> remove_uninteresting_words(split_words(uninteresting_words))
  |> tally_word_frequency
  |> print_outcome
end

{% endhighlight %}

The function above is exactly the same as the first, but it reads like a clear list of instructions. The outcome of each function is passed to the following function as though it is its first argument.

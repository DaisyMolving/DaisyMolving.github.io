---
layout: post
comments: true
title: "Elixir: Using Poison to Parse JSON Data"
date: 2016-09-22 10:30:30 +0000
---

In the [previous post][previous-post], we learnt how to use the Elixir library HTTPoison to make an HTTP request. Ours was a `GET` request, and we retrieved a file of JSON data from the Open Weather API that looked like this:

<p align="center">
<img src="../../../../../../../assets/json-data-weather-example.png">
</p>

JSON stands for JavaScript Object Notation, and is a way of storing data. Information is stored as key-value pairs in a way that is organised and easily accessible. However, it is also written in JavaScript.

{% highlight javascript %}
var example = { 
	"name" : { "first_name" : "Daisy", "last_name" : "Mølving" },
	"age" : 25,
	"hobbies" : "knitting"
};
{% endhighlight %}

In order to convert data into something that Elixir can read, we can use a JSON parsing library such as Poison.

<strong>Using Poison</strong>

Poison must be added as a dependency in your mix.exs file like so:

<p align="center">
<img src="../../../../../../../assets/adding_poison_as_dependency.png">
</p>

Now run `mix deps.get`.

Poison allows us to take the JSON data returned in the HTTP response and parse it into Elixir, where it will be treated like a series of Maps and Lists. In order to parse the data, we can write a function where we pass the HTTP `GET` request to the Poison.Parser module.

<p align="center">
<img src="../../../../../../../assets/poison_parser_function.png">
</p>

Now we can treat the information as though we are accessing it from maps and lists in regular Elixir. Knowing that the JSON data looks like this:

{% highlight javascript %}
{"city": 
	{ "id": 2643743,
		"name": "London",
		"coord": {"lon": -0.12574, "lat": 51.50853}
		"country": "GB",
		"population": 0}
	}
}
//population, 0? Really Open Weather Map?
{% endhighlight %}

We know that parsed into Elixir it will be:

{% highlight elixir %}
%{"city" => 
	%{ "id" => 2643743,
		"name" => "London",
		"coord" => %{"lon": -0.12574, "lat": 51.50853}
		"country" => "GB",
		"population" => 0}
	}
}
{% endhighlight %}

And so an Elixir function like the one below will access the city's name from the above nested maps.

<p align="center">
<img src="../../../../../../../assets/locate_information_in_map.png">
</p>

Poison makes using JSON data in Elixir simple, and greatly efficient. We can now use this data anywhere in our application, including storing it in a database, which we will do in our next post.

[previous-post]:http://daisymolving.github.io/2016/09/20/http-and-httpoison.html

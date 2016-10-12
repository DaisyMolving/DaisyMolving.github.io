---
layout: post
published: false
comments: true
title: "Elixir: Accessing Databases with Ecto"
date: 2016-09-26 10:30:30 +0000
---

The Ecto Library is used to interact with databases in an Elixir Mix project. In my Grabbing The Weather application I would like to store temperatures gathered from the external Weather API and access it to give the average temperature for each city. I realise this is not very scientific, as it only averages the temperatures that it has collected at my request since the database was created, but let's look at how to set it up for learning's sake.

First of all we need to add Ecto as a dependency in our `mix.exs` file to what we already have from [previous posts][http-poison-post], like so:

<p align="center">
<img src="../../../../../../../assets/adding_ecto_and_postgrex_to_deps.png">
</p>

You will notice that I have also added a `postgrex` dependency. This is because my database will use Postgres. Next I add Ecto and Postgres to my application function, as well as the logger. The logger will show messages, warnings or errors as to whether access to the database was successful or not. Also in the application function there is a module defined. This module is where the logic lives that will be interacting with our database.

<p align="center">
<img src="../../../../../../../assets/adding_ecto_and_postgrex_to_applications.png">
</p>

Now I can run `mix deps.get` and `mix deps.compile`.



[http-poison-post]:http://daisymolving.github.io/2016/09/20/http-and-httpoison.html

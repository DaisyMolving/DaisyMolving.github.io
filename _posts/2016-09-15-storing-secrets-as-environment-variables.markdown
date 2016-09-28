---
layout: post
comments: true
title: "Storing Secrets as Environment Variables"
date: 2016-09-15 10:30:30 +0000
---

Recently I have started a project which uses an external API to access current and future weather information. The API, [Open Weather Map][open-weather-map-site], allows one to make data requests to its server, and returns json or xml data to fulfill the request. In order to monitor their API calls, Open Weather Map supplies each registrant with an API key. This key is personal to each registrant's application. 

Depending on how many calls the registrant makes, the cost of their account will range from $0 to $2000USD a month. For this reason a registrant would be wise to keep their personal API key a secret, as if others know or can access it they can use it freely, at the key owner's cost!

We cannot store our API key anywhere in our application. As soon as we use Git or another version control system, and our application files are online, the key is there in plain view for everyone to see. There are even some types of malware that search sites such as Github for matches on key strings. However our application will still need to access the key in order to make requests to the API.

So, how can our application access an API key that is not stored anywhere within it? That is where environment variables come in.

<strong>Environment Variables</strong>

Environment Variables are locally stored dynamic values that can be used in both scripts and on the commmand line. They can be set, or unset inside your shell configuration file, such as `.bashrc` or `.zshrc`. To see the environment variables that are already set on your system, type `env` into the command line. This will print them in an ordered list.

My system shell is ZSH, so in order to edit my `.zshrc` configuration file I open it with vim like so:

`vim ~/.zshrc`

Now I need can set my api key in here like so:

`export WEATHER_API_KEY="thisisnotmyrealapikey"`

One would of course replace the string above with their real API key supplied to them upon registering to Open Weather Map. Here in the `.zshrc` file, the key is accessible to any application that needs it, but cannot be seen within them. It exists solely on the computer's local system. In order to retrieve it to make requests as part of a url, we use Elixir's System module. The System module contains functions that can interact with the host system.

We can access our key, without revealing it, like so:
{% highlight elixir %}
iex> System.get_env("WEATHER_API_KEY")
{% endhighlight %}

Within the application that uses it, it might look something like this:

<p align="center">
<img src="../../../../../../../assets/env_var_in_url.png">
</p>

The url above is what will be used to make an http request to the Open Weather API, which now can only be done through this application alone instead of through unexpected parties.

[open-weather-map-site]:http://openweathermap.org/api

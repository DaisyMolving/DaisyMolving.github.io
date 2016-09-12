---
layout: post
comments: true
title: "Elixir: Creating a Project with Mix and Running it Using Escripts"
date: 2016-08-08 10:30:30 +0000
---

Elixir comes with a build tool called Mix, which can be used to create a project. Creating a mix project is very simply done, and using it to run tests and executable files is also very easy. 

To create a new mix project simply type the command `mix new project_name`.

This will create the following directory structure:

<p align="center">
<img src="../../../../../../../assets/mix_project_tree.png">
</p>

The `lib` and `test` directories contain your implementation and test files respectively. The `mix.exs` file configures your project and can be set to create an escript file to run your project.

<strong>Running Tests</strong>

To run your tests the command `mix test` can be used. This must be run from the `project_name` folder because the command needs access to the `mix.exs` file. You can run it to check configuration before you have even written any code.

<p align="center">
<img src="../../../../../../../assets/mix_project_test.png">
</p>

You will notice that a test already passes. This is because your test file has a truthful test already built in like so:

<p align="center">
<img src="../../../../../../../assets/mix_lib_and_test_files.png">
</p>

This passing test can be deleted or replaced with your real tests as you write your application. Let's write an application that sums a list of numbers:

<p align="center">
<img src="../../../../../../../assets/mix_example_replacement_test.png">
</p>

<strong>Running A Command Line Application</strong>

To run a command line application you will need an entry point, or main module. This is the module that you select to contain a `main` function, which will be the trigger that sets off your application. It is configured that it takes an argument, so has an arity of one ( `main/1` ).

Once you are happy that your application is working as it should and are ready to run, it is time to write the `main` function, like so:

<p align="center">
<img src="../../../../../../../assets/mix_main_function.png">
</p>

Our `main` function here is not passed an argument, as it has a hard-coded number-list upon which to act. Therefore the function takes `_`. This operator allows anything to be passed here, as it is not defined.

Next we need to tell the `mix.exs` file where to look for the `main` function. We therefore define our `main_module` under our `escript` like so:

<p align="center">
<img src="../../../../../../../assets/mix_defining_the_escript_and_module.png">
</p>

This is saying, "When the escript is to be run/built, here is the module which contains the `main` function."

Now we will run the command `mix escript.build` to build the escript. It shows below in our directory in red. This is an executable file, it is the file that runs our application.

<p align="center">
<img src="../../../../../../../assets/mix_building_the_escript.png">
</p>

To run it, we simply run the command `./project_name`. If we were to pass the `main` arguments to act upon, this is where we would do it.

<p align="center">
<img src="../../../../../../../assets/mix_running_the_escript.png">
</p>

Success! The escript runs the `main` which passes the number-list `[1, 2, 3, 4]` to `print_sum`, and we see the result here on the command line.


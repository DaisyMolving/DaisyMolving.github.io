---
layout: post
comments: true
title: "Elixir: Lists (Linked-Lists) Vs Tuples and Arrays"
date: 2016-08-01 10:30:30 +0000
---

<strong>Linked Lists vs Arrays and Tuples</strong>

Your computer's memory can be thought of as a series of sections, each with a storage capacity, at a certain position. If we had a tuple `{1, 2, 3}` to store in memory it would be stored contiguously. This means all its elements would be stored in order right next to each other, like they are in the diagram below. This is useful when we need to access an element, because it can easily be found. A tuple's size is fixed upon it's creation. This means that we know how many elements there are in the collection at all times. When accessing elements we can find them with a simple equation, using the first position of the tuple and adding to it the number of elements to traverse multiplied by their size. 

<p align="center">
<img src="../../../../../../../assets/array_tuple_in_memory.png">
</p>

For instance the tuple above has 5 integers, each taking up 3 bytes of memory. To find the element at the index `3`, we would multiply that index number by the amount of bytes of memory needed to reach that position (3) and add that to the first position.

`3 * 3 + 100 = 109`

Now we can access the element at position 109 easily. Look again at the functions that the Tuple module uses. They are involved with finding elements in this way, and also replacing them. Finding the `tuple_size` is also simple, because of the fact that tuples are a fixed size upon creation. Recalling this information is instant.

There are some disadvantages to storing collections contiguously also. One of these is when we want to add an element to a tuple. Because tuples are a fixed size upon creation we cannot simply expand them to insert a new element into them. The tuple has to be copied to a new location with the new element where there is enough space to hold the entire collection contiguously again. This means that this type of operation is not instant, rather it takes as much time as moving each element, a linear function. 

<p align="center">
<img src="../../../../../../../assets/moving_resizing_array_tuple.png">
</p>

This can cause memory wasteage as well as less efficient functions. In the above diagram the dark blue space represents memory that used by other mystery data types and the new tuple to be created in a new location. As you can see we added `72` here to the 2nd index position of the tuple `{13, 4, 8, 2, 56}`.

Lists in Elixir are a data type called linked lists. They are not stored contiguously like tuples or arrays in ruby. In a linked list each element has its value as well as a pointer to the location of the next element. This means that when adding or removing elements we need only to change where the pointers are pointing, and any new elements can be stored absolutely anywhere in the computer memory. Linked lists use memory efficiently as well as allowing for instant additions and removals, however they do not allow for instant recall of elements at individual positions.

<p align="center">
<img src="../../../../../../../assets/linked_list.png">
</p>

This is because to find the element at a particular index we must follow each pointer and look at each element along our way to it. This means that finding elements is not a constant operation, rather a linear function.

Deciding whether to use a tuple or a list in your algorithm or program may be important when considering what you need to be doing. If you need to collect data that is constantly needing to be added to, then a list may be best. If you need to input data only once upon creation, but will need to access it constantly, then a tuple will be more efficient.

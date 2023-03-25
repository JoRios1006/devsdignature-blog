---
title: "OOP sucks"
date: "2023-03-25T22:28:54Z"
---

The development and spread of object-oriented programming (OOP) is a disaster for the modern world.

 Just as the Industrial Revolution brought about unprecedented change and upheaval, so too has the rise of OOP ushered in a new era of chaos and confusion in the world of software development.

Gone are the days of simple, procedural programming, where functions and data structures were kept separate and code was easy to read and understand. In its place, we have a new paradigm that seeks to bind functions and data together in a single, impenetrable unit known as an object. It's as if the software world has been turned on its head, with madness and confusion reigning supreme.

But fear not, my fellow programmers, for all is not lost. With a little common sense and a healthy dose of skepticism, we can push back against the tide of OOP and reclaim our rightful place as masters of our own code. Together, we can build a better, more sane world of software development, free from the tyranny of objects and the madness they bring. So let us rise up, my friends, and declare our independence from the chains of OOP!

##### Objection 1 - Objects Are a Fundamental Error

Object-oriented programming (OOP) is a disaster waiting to happen. Functions and data structures belong to different worlds and should never be forced together into a single entity. Functions do things, while data structures just are. How can we possibly understand functions and data structures when they are locked up in the same cage?

To make matters worse, functions in OOP are built from sequences of imperatives, making them difficult to comprehend. Data structures, on the other hand, are declarative and much easier to understand. Functions are just black boxes that transform inputs to outputs. We can understand the function if we understand the input and output, but that doesn't mean we can write it.

Functions and data structures are completely different animals, and it is fundamentally incorrect to bind them together in objects.

Objects bind functions and data structures together in indivisible units. I think this is a fundamental error since functions and data structures belong in totally different worlds. Why is this?

**Functions do things**. They have inputs and outputs. The inputs and outputs are data structures, which get changed by the functions. In most languages functions are built from sequences of imperatives: “Do this and then that …” to understand functions you have to understand the order in which things get done (In lazy FPLs and logical languages this restriction is relaxed).

Data structures just are. They don’t do anything. They are intrinsically declarative. “Understanding” a data structure is a lot easier than “understanding” a function.

Functions are understood as black boxes that transform inputs to outputs. If I understand the input and the output then I have understood the function. This does not mean to say that I could have written the function.

Functions are usually “understood” by observing that they are the things in a computational system whose job is to transfer data structures of type T1 into data structure of type T2.

**Since functions and data structures are completely different types of animal it is fundamentally incorrect to lock them up in the same cage.**

##### Objection 2 - Everything Has to Be an Object

In OOP, everything has to be an object, even time. This is a ridiculous notion. In a non-OOP language like Erlang, time is just an instance of a data type. We can specify time using clear type declarations that are not associated with any particular object. There are no methods to complicate things.

In OOP, data type definitions are spread out all over the place, making it difficult to find them. In Erlang or C, we can define all our data types in a single include file or data dictionary, but in OOP, it's impossible. To define a ubiquitous data structure, we must choose a base object in which to define it, and all other objects that want to use it must inherit from that object. It's a mess.

Consider “time”. In an OO language “time” has to be an object. But in a non OO language a “time” is a instance of a data type. For example, in Erlang there are lots of different varieties of time, these can be clearly and unambiguously specified using type declarations, as follows:

```
-deftype day() = 1..31.
-deftype month() = 1..12.
-deftype year() = int().
-deftype hour() = 1..24.
-deftype minute() = 1..60.
-deftype second() = 1..60.
-deftype abstime() = {abstime, year(), month(), day(), hour(), min(), sec()}.
-deftype hms() = {hms, hour(), min(), sec()}.
...
```

Note that these definitions do not belong to any particular object. they are ubiquitous and data structures representing times can be manipulated by any function in the system.

There are no associated methods.


##### Objection 3 - In an OOPL data type definitions are spread out all over the placeObjects Have Private State

One of the most frustrating aspects of object-oriented programming (OOP) is the way data type definitions are scattered all over the place. Unlike in non-OOP languages like C or Erlang, where all data types can be defined in a single include file or data dictionary, OOP requires that data type definitions belong to objects.

This means that to define a ubiquitous data structure, we must first choose a base object in which to define it. All other objects that want to use this data structure must then inherit from that object, adding another layer of complexity and making code harder to understand and maintain.

As a result, finding all the data type definitions in an OOP program can be a real challenge. Without a clear, centralized location for data type definitions, it is easy to lose track of which data types are defined where, leading to confusion and errors.

Furthermore, the scattering of data type definitions in OOP can hinder modularity and code reuse. With data types tied to objects, it becomes harder to reuse code across different parts of a program or between different programs.

In conclusion, the scattering of data type definitions in OOP is a major obstacle to writing maintainable, modular code. While OOP has its benefits, it is important to be aware of the limitations it imposes on code organization and to look for alternative paradigms that can help mitigate these issues.

In an OOPL data type definitions belong to objects. So I can’t find all the data type definition in one place. In Erlang or C I can define all my data types in a single include file or data dictionary. In an OOPL I can’t - the data type definitions are spread out all over the place.

Let me give an example of this. Suppose I want to define a ubiquitous data structure. ubiquitous data type is a data type that occurs “all over the place” in a system.

As lisp programmers have know for a long time it is better to have a smallish number of ubiquitous data types and a large number of small functions that work on them, than to have a large number of data types and a small number of functions that work on them.

A ubiquitous data structure is something like a linked list, or an array or a hash table or a more advanced object like a time or date or filename.

In an OOPL I have to choose some base object in which I will define the ubiquitous data structure, all other objects that want to use this data structure must inherit this object. Suppose now I want to create some “time” object, where does this belong and in which object…

##### Objection 4 - Objects Have Private State

The use of private state in object-oriented programming (OOP) has long been a point of contention among programmers. While some argue that private state is necessary for data encapsulation and abstraction, others maintain that it is a hindrance to modularity and code reuse.

On the one hand, private state allows programmers to hide the inner workings of their objects from the outside world, preventing unauthorized access and ensuring data integrity. It also allows for more flexible and modular code, as objects can be easily composed and reused without worrying about external interference.

On the other hand, private state can also lead to unnecessary complexity and coupling between objects. Objects with private state are not easily composable, as they can only be used in the context of the object in which they were defined. This can lead to code duplication, unnecessary object creation, and increased memory usage.

Furthermore, functions with side effects should be avoided in programming languages since they can lead to unexpected behavior and bugs. However, private state in OOP encourages the use of side-effecting functions, since data can only be modified through object methods. This can make it harder to reason about programs and debug them when something goes wrong.

So, what is the solution to this dilemma? Some programming paradigms, such as functional programming, eschew the use of private state altogether, instead relying on immutable data structures and pure functions that have no side effects. Others, such as aspect-oriented programming, provide mechanisms for managing state that are separate from the objects themselves.

Regardless of the approach taken, it is clear that private state in OOP is not without its drawbacks. Programmers must weigh the benefits of data encapsulation and abstraction against the complexity and coupling that private state can introduce. Only then can they create software systems that are both robust and easy to maintain.

State is the root of all evil. In particular functions with side effects should be avoided.

While state in programming languages is undesirable, in the real world state abounds. I am highly interested in the state of my bank account, and when I deposit or withdraw money from my bank I expect the state of my bank account to be correctly updated.

Given that state exists in the real world what facilities should programming language provide for dealing with state?

OOPLs say “hide the state from the programmer”. The states is hidden and visible only through access functions.
Conventional programming languages (C, Pascal) say that the visibility of state variables is controlled by the scope rules of the language.
Pure declarative languages say that there is no state.

The global state of the system is carried into all functions and comes out from all functions. Mechanisms like monads (for FPLs) and DCGs (logic languages) are used to hide state from the programmer so they can program “as if state didn’t matter” but have full access to the state of the system should this be necessary.

The “hide the state from the programmer” option chosen by OOPLs is the worse possible choice. Instead of revealing the state and trying to find ways to minimise the nuisance of state, they hide it away.

OOPs may argue that hiding state is necessary to prevent bugs and ensure data integrity, but this is a flawed argument. Hiding state only makes it harder to reason about programs and debug them when something goes wrong. Instead, we should strive to create programming languages and paradigms that make it easy to manage state while minimizing its impact.

Furthermore, the use of private state in OOPs leads to unnecessary complexity and coupling between objects. Objects with private state cannot be easily composed or reused, making it difficult to build complex systems that are modular and easy to maintain. This problem is exacerbated by the fact that data type definitions in OOPs are spread out all over the place, making it hard to find and understand them.

##### Object Oriented Programming is Inherently Harmful

> “Object-oriented programming is an exceptionally bad idea which could only have originated in California.”
– Edsger Dijkstra

>“object-oriented design is the roman numerals of computing.”
– Rob Pike

>“The phrase "object-oriented” means a lot of things. Half are obvious, and the other half are mistakes.“
– Paul Graham

>“Implementation inheritance causes the same intertwining and brittleness that have been observed when goto statements are overused. As a result, OO systems often suffer from complexity and lack of reuse.”
– John Ousterhout Scripting, IEEE Computer, March 1998

>“90% of the shit that is popular right now wants to rub its object-oriented nutsack all over my code”
– kfx

>“Sometimes, the elegant implementation is just a function. Not a method. Not a class. Not a framework. Just a function.” 
– John Carmack

>“The problem with object-oriented languages is they’ve got all this implicit environment that they carry around with them. You wanted a banana but what you got was a gorilla holding the banana and the entire jungle.”
– Joe Armstrong

>“I used to be enamored of object-oriented programming. I’m now finding myself leaning toward believing that it is a plot designed to destroy joy.”
– Eric Allman

OO is the “structured programming” snake oil of the 90' Useful at times, but hardly the “end all” programing paradigm some like to make out of it.

And, at least in it’s most popular forms, it’s can be extremely harmful and dramatically increase complexity.

Inheritance is more trouble than it’s worth. Under the doubtful disguise of the holy “code reuse” an insane amount of gratuitous complexity is added to our environment, which makes necessary industrial quantities of syntactical sugar to make the ensuing mess minimally manageable.

In conclusion, OOPs are a fundamentally flawed approach to programming that should be avoided at all costs. Instead, we should strive to create programming languages and paradigms that separate functions and data structures, make it easy to manage state, and encourage modularity and code reuse. Only then can we build robust and maintainable software systems that meet the needs of users and developers alike.
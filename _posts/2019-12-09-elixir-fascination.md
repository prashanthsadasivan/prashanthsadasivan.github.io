---
layout: post
title: Elixir - A fascinating combination of concepts
---

Programming Languages are created in order to solve problems. This might seem obvious, but I don't think it is _as_ obvious as it seems. Some languages are focused on working with statistical and numerical data. Some are focused on ease of learning and usage. Others are focused on making it easier to write performant code. There are languages that attempt to work for all usecases and problems. But languages that are crafted to focus on a set of specific problems feel more powerful. I've always had a problem really feeling comfortable in Python, for example. Python lets you work with fancy list comprehensions, build very large class hierarchies, write functional code, and write metaprogramming (maybe? I've never really understood metaclasses, though I never put in the effort to). It's got web frameworks across the spectrum of full mvc to single line scripts that I feel that the depth of language features come at the cost of the language feeling cohesion. There's value in being able to jump into a random codebase and being able to understand the codebase without having to understand the nonstandard conventions. Ruby and Rails really mastered this concept, basically to a fault. Go also falls into an interesting place in this spectrum of structured and diadactic versus free and unstructured. NodeJS too. 

But I haven't worked with a language and framework that's as tight as Elixir and the OTP, and I've been dying to use Elixir to solve a problem that it's well suited for.

I don't plan on recounting the syntax or structure of Elixir, there are plenty of blog posts on the internet about why Elixir is cool. But I want to focus on a few really valuable ideas that make Elixir very special.

## leveraging the erlang VM

Before working with elixir, I was not very familiar with erlang. I knew that RabbitMQ was written in erlang which had weird config syntax, but I didn't quite know what value erlang provides. The Erlang VM has a bunch of nifty features and properties that make writing "massively scalable, soft real-time highly available" systems easier. Thanks to erlang's focus on making it easier to write these types of systems, Elixir really doesn't have to focus that much on inventing new ways to solve these problems. Some of the tools that the erlang VM gives you to write concurrent, highly available systems are:

* Lightweight Processes - See green threads, goroutines, etc.
* Preemptive Scheduling - No singular process can dominate the VM
* OTP Framework - A framework for describing the hierarchy of concurrent processes in the system
* Distribution - Connect Nodes within a system to coordinate work across a cluster.

There's plenty more concepts, and libraries that makes it easier to design concurrent systems with erlang than designing them in python, ruby, java, or others. There are also plenty of pitfalls too.  Elixir, by leveraging the erlang VM and OTP, is essentially an additional ecosystem of tools and services built for the erlang VM, using a different programming language frontend.  This may sound like I'm minimalizing what Elixir is - I'm not. Elixir gets all this stuff, including the battle testing the erlang VM has gone through for free, and leveraging erlang frees the language design to be focused on usability of these concepts, and providing additional tools to make writing distributed systems even easier.

## developer ergonomics + enough metaprogramming to be dangerous

Having been created by a former Rails core team member, Elixir has a very familar syntax if you've ever written Ruby. If you haven't, things still feel familiar - those coming from functional languages will appreciate very famiilar concepts like pattern matching, first class functions, and many other goodies. those coming from OOP and more traditional languages will appreciate the if and for statements, structs and modules. The language design is extremely pragmatic - they don't introduce new concepts to the language very easily, and borrow heavily from which ever language makes the most sense. There's some novelty around using the pipe operator, and the `with` keyword that using the language also feels fun to newcomers. Overall though, I'd say that Elixir is more a combination of some of the better ideas from other communities rather than a bunch of brand new ideas.

And it's worth mentioning: with metaprogramming, the language can remain tiny - if you need some new syntax or DSL, you can create it without burdening the language with niche features. And the community has been very responsible with metaprogramming too, tending to only use it if it really adds value.

All this adds up to a language that feels like it has been designed with intention, focused on getting new users up to speed quickly by leveraging familiar concepts, and providing the tools needed to solve problems and extend the language.

## a productive web framework that puts it all together.

Phoneix is great for many reasons, but the one I want to focus on is how it's a great learning tool for all the concepts in Elixir and Erlang. If someone is looking to learn Plain ol' Ruby, Rails is NOT the codebase to look at. But Phoenix is an awesome demonstration of how to build a scalable, concurrent (and extensible) system, using the tools and concepts Elixir, Erlang, and OTP provide.

I kind of skipped over it before, but OTP is massively important. OTP provides an application framework - an easy way to start your application with a description of how everything needs to start up. Rather than starting at `int main` or `__main__`, and having to worry about manual startup, OTP gives you the tools to start your application in the correct order (and shutdown too! ), as a framework. OTP provides configured conventions that make it easy to reason about where to put your long running services.

Phoenix is a great introduction to the OTP concepts. When you start to peel back what feels like the magic layers of Phoenix, you don't end up in a quagmire of metaprogramming concepts (ignore Ecto). Phoenix is simply an OTP application. You'll find just a few simple erlang/elixir libraries (cowboy, plug), some interesting imports (`:controller` and `:view` imports), and the EEx template library _built into the language, rather than as library_. When you look at how the framework bootstraps your codebase, they give you the tools you need to add more complexity to your application, without having to fully design the coordination between all the parts of your application.

## wrapping up

All these different concepts, I've not seen in a language and framework. I don't think there are very many languages and frameworks that come with an application framework, a VM optimized for building concurrent applications, a lean syntax, and a productive web framework all in one. Go has a lean syntax, and some tools for building concurrent applications, but since you wire up everything manually, each application ends up looking different. Rails applications look very similar, but it is not a lean syntax, and I wouldn't say it's very optimized for writing concurrent applications (which more and more applications are becoming daily, with the rise of websockets and realtime expectations). Python I'm sure you can do it all, but again it's not a consistent set of tools, it's just whatever you decide to wire it up as. Maybe Java has some tools to do all this stuff? I doubt it would feel as slick and cohesive though. If you have the right problem, Elixir can be the edge that makes your solution better than the competition. There are not a lot of technologies I'd say that's true. There are even fewer programming languages I'd say that's true. But I feel confident saying that it's true for Elixir.

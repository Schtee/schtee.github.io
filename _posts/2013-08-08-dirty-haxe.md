---
title: Dirty Haxe
layout: post
date: 2013-08-08
---
I'm working on my first ever [Haxe](http://www.haxe.org) project and I am loving it. Haxe is a free, open source, object-oriented, cross platform, multi-target, ActionScript-like language and compiler. From one project you can generate:

* a compiled SWF, with support for a bunch of Flash versions
* JavaScript
* PHP
* C#, for targeting Windows,Windows Phone, Xbox or anything Mono supports
* Java, for targeting Android or anything that runs the JVM
* C++, for targeting basically anything else

Apart from SWF these will all provide source code which can then be built in an environment of your choosing.

What about making games?
-
For me, the real magic comes with the OpenFL library - an open source, cross platform implementation of the Flash standard library. This gives you access to a complete, well documented node based view hierarchy that can target basically anything. From the same project, using a different build argument, OpenFL can build to run in browser using HTML5 or Flash; natively on Windows, Mac and Linux desktop; on mobile, with support for iOS, Android and BlackBerry. This means you can hedge your bets when targeting browser: don't want to worry about flakey HTML5 support? Provide it as an option, but also build a SWF for everybody else. There's always going to be discrepancy between hardware and screen resolutions available on different mobile devices, but that doesn't mean you need different code. Build support for different resolutions into your game and target standard hardware features and your game can run on anything.

The language
-
So it can build a game to run on your toaster, but how is it to actually use? Well, for a start it has a compiler, so you know ahead of execution that your local variable is being used without being assigned. It's strictly typed, so that same compiler can catch you assigning a String to an Int. It also makes good use of type inference so you still don't have to be too verbose with assignment. It supports generics for some sweet strictly-typed containers. It supports anonymous functions and function objects for super-convenient callbacks. It's got a thorough standard library with support for sockets, web requests, XML parsing, functional-style set manipulation and a bunch more. The standard library support varies depending on what's actually available on different platforms, but that's all covered in the [API docs](http://api.haxe.org/). I haven't had to touch too much of it for the project I've been working on, but the hash map implementation has served me well. Compile times are an oft-quoted boon of Haxe, and from my limited experience it seems great. My MacBook Air generates the JS target for my simple puzzle games in 2-3 seconds.

I've struggled a little bit with debugging but that's mainly a result of targeting HTML5. The JavaScript debugger in Firefox is great but you're debugging a single monolithic JS file which is a different representation of your Haxe code, and then figuring out what  that actually translates to. I'll have to explore further if there's a way to debug something closer to the actual game code I wrote, ideally the Haxe code itself. Declarations are ECMAScript style, ``name:Type`` (e.g. ``var x:Int``), which I find a little off-putting as I spend most of my time in C-like languages, but I can cope!

Conclusion
-
I use [Unity](http://www.unity3d.com) extensively, both at work and at home, and it's perfect for making cross-platform 3D games, making heavy use of the concept of scenes. I've made a few 2D games in Unity and it always feels like I'm fighting against it, shoehorning 2D elements into a 3D workflow. Haxe with OpenFL seems like a great code-centric alternative to Unity - you get all the benefits of write-once, deploy anywhere, plus the whole Flash standard library to drive your game's sprites. I'll definitely be using it for any small 2D games I make in the near future. Also having the option of targeting Flash is a nice bonus few other cross platform solutions still support!

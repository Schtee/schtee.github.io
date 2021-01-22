---
title: "How and Why Is This Object Being Destroyed, Unity?!"
layout: post
date: 2017-07-17
---
I recently ran up against a problem in a Unity project I'm working on: a `GameObject` was being `Destroy`ed, but I didn't know why or from where. The codebase, naturally, has many calls to `Destroy()` and contains its own methods with that name, which made both *Find References* and text-based searches impractical. I just wanted a breakpoint in `UnityEngine.Object.Destroy()`.

## Round 1: `OnDestroy()`
*Spoilers: you may well know this method is a dead-end.*

Unity will automatically call `OnDestroy()` on all components on a destroyed `GameObject`. I thought this might allow me to set a breakpoint, but `OnDestroy()` is deferred to the end of the frame, so the callstack doesn't go back to the original `Destroy()` call. Next!

## Round 2: Hacking Unity's IL
A discussion with a friend led to the idea of modifying the [.NET IL](https://en.m.wikipedia.org/wiki/Common_Intermediate_Language) in Unity's DLLs to modify the contents of `UnityEngine.Object.Destroy()`. I Googled upon [Simple Assembly Explorer](https://sites.google.com/site/simpledotnet/simple-assembly-explorer), which allows you to view and modify the IL of compiled .NET binaries. Without any prior knowledge of .NET IL I was quickly able to insert a `ldarg.0`, to push `this` onto the stack as the argument for the next function call, and a `call` instruction, to call out to `UnityEngine.Debug.LogWarning`, which would give me a stack trace.
I booted up my project in Unity and sure enough, every call to `Destroy` produced the log I hacked in there. Amazing!
While this worked, it felt very fragile: any future update to Unity would stamp over this, and I didn't fancy learning IL to build this out further.

## Round 3: Harmony
I was aware of the concept of [hooking/detours](https://www.codeproject.com/Articles/30140/API-Hooking-with-MS-Detours) from lower level, C++/assembly code, and was interested whether something similar existed for .NET/C#/Mono/Unity. Google led me to [Harmony on GitHub](https://github.com/pardeike/Harmony):

> A library for patching, replacing and decorating .NET and Mono methods during runtime.

Not only does it support Unity, it's built with Unity in mind- the example code is a mod for a Unity game. I was able to copy and paste the example code into a fresh project referencing the Harmony DLL, change the target class to `UnityEngine.Object`, the target method to `Destroy` and the target parameter to a `UnityEngine.Object`, then change the hooked method implementation to a log call. After a build, all I needed to do was drop my new DLL, along with the provided Harmony DLL, into the Unity project call the setup function to initialise the hooks and boom: the log was again produced on every `Destroy`. This has a bunch of benefits over the previous method, such as writing the patch in the language I was already using, not having to screw with binary file (so the patch's code could happily live in source control), and being forwards compatible (unless Unity make any breaking API changes). In theory any C# Unity could be hooked in this fashion, which could be great for mocking functions or gaining a bit more control over what's going on under the hood!

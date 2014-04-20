---
layout: post
title: "Hello, The Internets"
date: 2013-02-11
---
I'm currently developing a personal-project mobile game using [Cocos2d-x][], a cross platform port of the Cocos2d-iOS framework. I got as far as having a few graphical layers moving sprites on the screen when I got tired of 2d-x's weird Objective-C–shoehorned–into–C++ style, which encourages the use of static factory functions to create objects, when C++ already has constructors. I had also been reading a lot about Entity/Component (EC) systems for game development – a methodology that allows for game objects to be built up from collections of reusable components, and, relevantly, forces logic to be separated from display code. I thought this would be a great opportunity to implement my own EC system, as it would keep the nasty Object-C style code very localised and wouldn't spread to any parts of the game logic.

This went really well – after writing and refining the EC framework, then coding some fundamental components and subsystems (such as SpriteRenderable and Position components and SpriteRenderer subsystem), I had a character I could set the world position of, and the SpriteRenderer subsystem would set the Cocos sprite's position accordingly. I went on to write the relevant components and subsystems to get the character moving around a tile base map, using the Cocos touch interface and all was good.

Then I hit a problem. The game I'm developing needs a trigger system. An entity (e.g. a button) needs to trigger an action (e.g. a door opening). This requires the subsystem to track entities with Button components (the trigger) and entities with Position components (the entity that will cause the button to trigger) and consider them independently:

    for each Entity with Button and Position: b
        for each Entity with Position: p
            if b.pos == p.pos
                b.button.triggerAction()

..which my current system doesn't support, so I'll have to add the concept of *or* and *and* operators to the class that defines the types a subsystem is interested in. I'll check back in when that's implemented and hopefully I'll have a nice, flexible event triggering system.

[Cocos2d-x]: http://www.cocos2d-x.org

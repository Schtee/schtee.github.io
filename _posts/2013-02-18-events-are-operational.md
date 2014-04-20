---
layout: post
title: "Events Are Operational"
date: 2013-02-18
---
I have implemented my proposal outlined in the previous post and all it's working great. There's a base TriggerComponent class which holds a pointer to its action. PositionTriggerComponent extends TriggerComponent, and PositionTriggerSubSystem checks for objects occupying PositionTriggerComponent-Entities' tiles and sets the triggered flag on their Actions. Finally, classes inheriting from ActionSubsystem decide how to handle their actions being triggered. This is working for a simple DebugActionComponent/SubSystem but the idea should apply to anything else. Getting closer to being able to make a game.
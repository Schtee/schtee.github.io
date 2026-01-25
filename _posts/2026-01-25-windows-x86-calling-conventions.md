---
title: Windows x86 C++ Calling Conventions
---
Noodling with reverse engineering Windows applications needs me to know these things but they refuse to stick in my brain, so I have put them in one place.

All stack parameters are passed in right-to-left order.

Name | Stack cleaned by | Parameters
-|-|-
`thiscall` | Callee | `this` in `ECX`, params on stack
`fastcall` | Callee | First in `ECX`, second in `EDX`, rest on stack
`cdecl` | Caller | Stack
`stdcall` | Callee | Stack
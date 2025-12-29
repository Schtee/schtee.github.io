---
title: UltraHLE Technical Information
---
I recently stumbled on [this comment on a Reddit post](https://www.reddit.com/r/emulation/comments/dhr47f/comment/f3qy9je/) about MVG's [UltraHLE](https://en.wikipedia.org/wiki/UltraHLE) retrospective. They didn't link to the source they were quoting and no amount of Googling gave me what I was looking for. Many clicks around archive.org eventually gave me [the goods](https://web.archive.org/web/19990508162905/http://www.emuunlim.com/UltraHLE/techinfo.htm). Turns out the comment containted all the text from the page, but always good to have the source. While very much not exhaustive, the page provides an interesting peek at the thinking behind an amazing technical achievement, emulating _at least some games_ from a 3D-focused console during its lifespan, at a time when consumer 3D cards were relatively novel (the Voodoo2 was released the year before UltraHLE).

Some quotes:

> There has been no attempt to translate the RSP code, since it works so closely with the hardware and uses integer arithmetic. Instead the C-code can use floating point, which is easier and faster on the PC. This means the results are not 100% same as those on the real console, but on the plus side things are a lot faster, and often results look better (for example increasing game resolution is trivial).

> What helps us, is that the games don't use the CPU to its full extent. Practically no 64-bit code is used, and virtual memory usage is limited.

> On a Pentium II the R4300 emulation speed is now close enough to allow real time operation on many games and demos. Of course the PC has to do the work of the Reality Co-Processor too, so that will slow things down. But PCs are getting faster, and a 450Mhz Pentium II should run at excellent speed. 
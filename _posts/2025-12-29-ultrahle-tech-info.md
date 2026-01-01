---
title: UltraHLE Technical Information
---
I recently stumbled on [this comment on a Reddit post](https://www.reddit.com/r/emulation/comments/dhr47f/comment/f3qy9je/) about MVG's [UltraHLE](https://en.wikipedia.org/wiki/UltraHLE) retrospective. They didn't link to the source they were quoting and no amount of Googling gave me what I was looking for. Many clicks around archive.org eventually gave me [the goods](https://web.archive.org/web/19990508162905/http://www.emuunlim.com/UltraHLE/techinfo.htm). Turns out the comment containted all the text from the page, but always good to have the source. While very much not exhaustive, the page provides an interesting peek at the thinking behind an amazing technical achievement, emulating _at least some games_ from a 3D-focused console during its lifespan, at a time when consumer 3D cards were relatively novel (the Voodoo2 was released the year before UltraHLE).

Some quotes:

> There has been no attempt to translate the RSP code, since it works so closely with the hardware and uses integer arithmetic. Instead the C-code can use floating point, which is easier and faster on the PC. This means the results are not 100% same as those on the real console, but on the plus side things are a lot faster, and often results look better (for example increasing game resolution is trivial).

> What helps us, is that the games don't use the CPU to its full extent. Practically no 64-bit code is used, and virtual memory usage is limited.

> On a Pentium II the R4300 emulation speed is now close enough to allow real time operation on many games and demos. Of course the PC has to do the work of the Reality Co-Processor too, so that will slow things down. But PCs are getting faster, and a 450Mhz Pentium II should run at excellent speed. 

<details markdown="1">
<summary>Expand for the full text!</summary>

### UltraHLE Architecture

If you are interested in programming or emulators in general, this text is for you. The purpose is the explain the basic architecture behind UltraHLE and tell how it differs from many other emulators.

The HLE in the name pretty much sums it up. It stands for High Level Emulation. Instead of trying to emulate the hardware as closely as possible and supporting low level operations, the approach is just the opposite: Emulate as little as possible and try to detect operatios as early as possible, and emulate them using optimized C-code.

For example there is no boot rom and even boot code in rom images is ignored. Common operating system routines like interrupt adjustments are intercepted and ignored. When dealing with graphics and sound, the abstraction level is high (display lists and sound lists). CPU and DMA emulation is at a lower level, but still uses some tricks to detect common operations and perform them more efficiently.

This probably wouldn't work on an older console, where low level programming and hand tuned assembly were the rule. But the Nintendo64 is quite different. Most of the code is written in high level C eliminating need for 100% exact CPU emulation (so things like exceptions or virtual memory can be emulated only approximately). Graphics and sound both use command lists, that are reasonably standard between different games.

### Graphics and Sound
On the real console display and sound lists are executed using the Reality Signal Processor (RSP) which executes code from the rom image. It is a vector processor with operations specifically designed for fast geometry and audio, and as such is difficult to emulate efficiently. In UltraHLE the lists are interpreted with C-code, which has been created by studying the lists games generate. There has been no attempt to translate the RSP code, since it works so closely with the hardware and uses integer arithmetic. Instead the C-code can use floating point, which is easier and faster on the PC. This means the results are not 100% same as those on the real console, but on the plus side things are a lot faster, and often results look better (for example increasing game resolution is trivial).

It is also possible to do things the original code doesn't do. For example, on the N64 loading new textures is a rather fast process, and all textures are loaded each frame. On the PC 3D-architectures, texture loading is generally a slower operation. The solution is to cache textures on the PC side and eliminate all unnecessary loads. This give a big performance boost and practically all textures can be cached, since PC has so much more texture memory.

Other display optimizations include removal of hidden triangles, extra matrix loads, unused mode changes and the like. Since texture and mode changes are more expensive on the PC, it makes sense to do extra geometry processing to eliminate as many changes as possible. Triangles are also collected into larger groups (sorted by mode) to allow faster rendering.

Finally, the graphics emulation has to cope with all the different rendering modes of the N64. The RCP contains a very configurable 3D-rendering unit which supports many modes that are impossible to emulate directly on 3DFX, even when using glide. UltraHLE performs pretty complex mode conversion to find the best PC-modes for each N64-mode. Things that the N64 does in a single pass are converted to 1-3 passes on the PC, depeneding on mode complexity. The modes are cached like textures, so the relatively slow mode decoding process does not slow things in practice.

Since there is so little information on Nintendo64 hardware, emulating sound and graphics on hardware level would probably have been extremely difficult (unless one had access to all N64 documentation, which we didn't). So in a way this high level approach was pretty much the only way to proceed. But it was a good way nevertheless, as the results show.

### CPU Emulation
The high level approach doesn't extend that well to CPU emulation, but luckily the CPU is a standard MIPS R4300 with excellent documentation available. So it's just a matter of following instructions, and then making it fast (which is the hard part). What helps us, is that the games don't use the CPU to its full extent. Practically no 64-bit code is used, and virtual memory usage is limited.

Initially the CPU was emulated in C like in most emulators to get things started, but that was way too slow. The next logical step also was to compile MIPS code into Intel code. All instruction decoding overhead is eliminated, but it still takes multiple Intel instructions to emulate a MIPS instruction (since MIPS has more registers and because the Intel FPU implementation just plain sucks). Also things like branches are not that easy to handle. The speedup was about 5-10x compared to C-emulation.

The next step was to add optimizations to the compiler. By allocating MIPS registers temporarily into the few Intel registers, many memory accesses can be eliminated. This allows compiling small connected instruction groups into about 2 Intel ops for each MIPS ops ratio. Nearby memory accesses with similar addresses can be simplified by caching the base addresses in registers. It is also possible to replace some RISC instruction pairs with single CISC instructions. Since our target (Pentium II) does out of order execution, it was not necessary to reorder instructions, which made optimizations a lot easier. These optimizations increased speed 2x.

On a Pentium II the R4300 emulation speed is now close enough to allow real time operation on many games and demos. Of course the PC has to do the work of the Reality Co-Processor too, so that will slow things down. But PCs are getting faster, and a 450Mhz Pentium II should run at excellent speed. And there are probably more possible optimizations, just waiting to be done.

### Compatibility
UltraHLE is a very unusual emulator. It doesn't run many titles (yet), but what it runs, it runs well. This is because the high level emulation routines either work (if what they assume of the game is corrent) or they fail (if the game uses a totally different display list format, for example).

The goal of UltraHLE is not to run as many titles as possible. It is to run the best titles as well as possible. And looking at the current compatibility list, this is exactly what UltraHLE does. Compatibility will no doubt improve in the future, but the emphasis will still be on quality instead of quantity. 
</details>
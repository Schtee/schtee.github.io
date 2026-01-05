---
title: "Ultima IX: Ascension Archaeology Resources"
layout: post
---
While [digging through Ultima IX files]({% post_url 2026-01-02-u9-archaeology %}), I found there were at least 2 pre-release demos of the game and figured it'd be handy for History to have somewhere to record them and some other resources for U9 archaeology.

### Demos

Link | EXE Build Date | Notes
-|-|-
[Computer Gaming World Dec '99 demo](https://ultima9.ultimacodex.com/the-ultima-9-demo/) (now-obscure MDX format) / [ISO conversion](https://archive.org/details/ultima-ixcgwdemo) | 1999-09-10 | [Notes](#cgw-demo-notes)
[PC Gamer UK Issue 78 demo](https://archive.org/details/ultimaixascensiondemo) | 1999-09-16 | [Notes](#pc-gamer-demo-notes)
[US retail release for reference] | 1999-11-02 | 
[EU retail release for reference] | 2000-01-24 | 

#### General demo notes

- Neither of these demos contain `bitmapC.flx`, suggesting the DXT1 compression came very late in the day

#### CGW Demo notes

- Features an intro video explainer from ya boi Richie G not found in the other demo (`demo_introf.mpg`)
- Only contains 16 bit graphics (i.e. `bitmapsh.flx` is empty)
- I compared the contents of `bitmap16.flx` with the retail version and there are differences but I didn't find anything _juicy_
- `music.flx` and `speech.flx` are in a `Sound` folder on the disk, not part of the install
  - `music.flx` is the same as the other demo but `speech.flx` is huge - 4,962 KB vs 138,773 KB. It's bigger even than the retail release's 138,194 KB
    - There's actually quite a lot of speech here that isn't in the retail install
	- Including a `Demon_` character (6 clips) that doesn't appear at all
	- A lot of lines appear here without post-processing applied:
		- A bunch of Avatar lines have been sped up a little in retail
		- `DupreGhost` clips don't have their spoooooky echo etc applied in the demo
		- `GenericGargoyle` haven't been pitched down/had reverb applied
		- `Oracle` has different type of spooky effect applied vs retail
		- In the demo, `Peiter_02498.umt` begins "Say what a bout that pirate girl, Raven?". In retail "Raven" is scrambled out for some reason.
	- `Avatar_10332`: "Why is Britain so lacking in Compassion?". Yup.
	- There are some lines of Guardian admonishing the avatar for attacking children, which I'm guessing was cut for obvious reasons

#### PC Gamer Demo notes

- Only contains 8-bit palette indexed graphics (i.e. `bitmap16.flx` is empty)
- I compared the contents of `bitmapsh.flx` with the retail version and there are differences but I didn't find anything _juicy_

### Resources

#### Tools

Link | Description
-|-
[Ultima 9 model importer](https://github.com/Chevluh/Ultima-9-Blender-Importer) | Python script to convert models and terrain to Blender format
[u9ed](https://github.com/Schtee/u9ed) | My C# project to view and export bitmaps
[vgmstream](https://vgmstream.org/) | Can play/export U9 sfx/music/speech

#### Docs

Link | Description
-|-
[Ultima IX internal formats @ Ultima Codex](https://wiki.ultimacodex.com/wiki/Ultima_IX_internal_formats) | Details on a bunch of game files
[Ultima 9 File Formats @ Burton Radons](https://web.archive.org/web/20201011190817/https://sites.google.com/site/burtonradons/eee/platforms/single-games/ultima-ix/file-formats) | An archive of a page with some details
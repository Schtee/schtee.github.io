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
- `music.flx` and `speech.flx` are in a `Sound` folder on the disk, not part of the install
  - `music.flx` is the same as the other demo but `speech.flx` is huge - 4,962 KB vs 138,773 KB. It's bigger even than the retail release's 138,194 KB
    - There's actually quite a lot of speech here that isn't in the retail install
	- Including a `Demon_` character (6 clips) that doesn't appear at all

#### PC Gamer Demo notes

- Only contains 8-bit palette indexed graphics (i.e. `bitmap16.flx` is empty)

### Resources

#### Tools

Link | Description
-|-
[Ultima 9 model importer](https://github.com/Chevluh/Ultima-9-Blender-Importer) | Python script to convert models and terrain to Blender format
[u9ed](https://github.com/Schtee/u9ed) | My C# project to view and export bitmaps

#### Docs

Link | Description
-|-
[Ultima IX internal formats @ Ultima Codex](https://wiki.ultimacodex.com/wiki/Ultima_IX_internal_formats) | Details on a bunch of game files
[Ultima 9 File Formats @ Burton Radons](https://web.archive.org/web/20201011190817/https://sites.google.com/site/burtonradons/eee/platforms/single-games/ultima-ix/file-formats) | An archive of a page with some details

### TODO List

- [ ] Investigate extra `speech.flx` clips
- [ ] Investigate differences in `sfx.flx`
- [ ] Investigate differences in the sprites
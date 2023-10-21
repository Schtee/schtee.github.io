---
title: Copy and paste from Obsidian with formatting
---

**tl;dr: [Copy as HTML plugin](https://github.com/jenningsb2/copy-as-html)**

Copy/pasting from [Obsidian](https://obsidian.md/) has some issues. The first problem I hit was that pasting into Slack was coming through as unformatted text - the raw Markdown. After a bit of fiddling, switching from **_Edit_ to _Reading_ mode resolved this**. Pasting from Reading mode properly formats the text.

Pasting into Google Docs created some more interesting problems though. While Reading mode carried the formatting through, it also brought elements of my Obsidian theme, like background colour which, naturally, wasn't what I was looking for. Then I found the [Copy as HTML plugin](https://github.com/jenningsb2/copy-as-html), which handles its own Markdown to HTML conversion and copies the output from that, avoiding bringing along any unintended elements from the editor. This leads to a nice workflow where you can draft and edit documents in Obsidian, keeping them close to other notes to allow for future remixing/cross-referencing etc, while making it easy to transfer it to Google docs to share or collaborate on.
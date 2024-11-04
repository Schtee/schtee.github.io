> [As I’m not currently self-hosting there is every chance the hosted service may go away or my data get lost]({% post_url 2023-10-12-omnivore %})

It is with great prescience that I sadly relay news that Omnivore is [going away](https://blog.omnivore.app/p/details-on-omnivore-shutting-down):

> We’re excited to share that Omnivore is joining forces with [some AI thing] [...] All Omnivore users will be able to export their information from the service through November 15 2024, after which all information will be deleted.

So I've gone back to comparing self-hostable alternatives to avoid this happening again. My main criteria are:
- easily self-hostable
- a read-it-later service for articles, not just a bookmark manager
- Nice to have:
	- highlights/annotations
	- a mobile app for offline viewing and OS-level sharing of links

Here are the options I've found:

Name | Highlights/annotations | Mobile app | Notes
-|-|-|-
[Linkwarden](https://linkwarden.app/) | ❌ | ❌ | [Demo instance](https://demo.linkwarden.app/). General UX is actually pretty nice. Seems to be _primarily_ a bookmark management service. Does save archived snapshots of pages in various formats, but these are a little fiddly to navigate to - the default interaction is to just open the live link
[wallabag](https://github.com/wallabag/wallabag) | ✅ | ✅ | I was using wallabag for a while before moving to Omnivore. The feature set is perfect, but both the web interface and mobile app feel a little clunky and the Android context menu to annotate/highlight doesn't behave consistently
[Readeck](https://readeck.org/en/) | ✅ | ❌ | Despite not having a native mobile app, there's a lot of great stuff here. The UX is clean and simple (quite similar to Omnivore's), it'll grab video transcripts where available, it can export to epub and there's a browser extension (which works on Firefox Android) to send the contents of weird JavaScript festivals that it can't scrape directly from the HTML alone. As a bonus, the dev [knocked together an importer from Omnivore right after they announced they were shutting down](https://codeberg.org/readeck/readeck/pulls/270)

Wallabag ticks all the boxes, but Readeck feels so much nicer to work with...it's just not going to be with me on the tube. Between the browser plugin and some [HTTP Shortcuts](https://http-shortcuts.rmy.ch/) workflow, sharing to the service is covered. It's really just the offline syncing I'm missing. I'll be sticking with Readeck for a while, and ultimately if the  lack of apps becomes a deal breaker, I'm sure I'll be able to move everything to wallabag easily enough.

I'd really love someone to fork the open source Omnivore [mobile apps](https://github.com/omnivore-app/omnivore) and make them talk Readeck instead. Maybe if I can find some time...
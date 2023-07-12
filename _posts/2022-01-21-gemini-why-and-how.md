I thought I'd start off by explaining why and how I setup a Gemini server.

### Why
We were chatting at work about the issues with the modern web - speed, cruft and general usability. Someone dropped a link to the Gemini project page.

[Gemini project page](https://gemini.circumlunar.space/)

It resonated with me, particularly because it doesn't expect to be, and isn't trying to be, a replacement to the web, but an alternative with a focus on signal-to-noise ratio. The markup for formatting text, gemtext, is Markdown-like and minimal, both in terms of characters/bytes used and range of functionality. There are 3 levels of (sub-)headings, links, blockquotes and pre-formatted text. And that's it. It's all making room for that textual content.
I thought it'd be a fun project to setup my own Gemini server, ideally for as close to free as possible.

### How
After a little research I settled on gmnisrv as the server program- I found a bunch of people using it and it doesn't have a ton of dependencies.

[gmnisrv](https://sr.ht/~sircmpwn/gmnisrv/)

I've wanted to learn Docker for a while, so I spent enough time researching it to cobble together something that would build gmnisrv and host a placeholder page locally

[My (probably bad) Dockerfile](https://gist.github.com/Schtee/846b12a6c2c3dce21429c33af33393b6)

Then I had to figure out where to host it. There are many, many free-or-almost-free options for hosting something running over http/https but a lot fewer with the flexibility to serve stuff on not-port-80-or-443. However, I found that Google Cloud Compute's free tier offers a low-end VM that should be more than capable to serve any throughput I'll get on this page. Specifically they offer:
- 1 e2-micro VM in a handful of US regions
- 30GB standard persistent disk

[GCP compute free tier details](https://cloud.google.com/free/docs/gcp-free-tier/#compute)

I spun up an instance, setup SSH keys, SCPd over my Dockerfile, setup port forwarding and got gmnisrv running. I opened Gemini client Lagrange and pointed it at the VM's IP address and was served my page!

I then wrote a (very) small Python script to run over all the gemtext files in a folder (e.g. blog posts) and build an index page. All the metadata is encoded into the filename- this is 2022-01-21-why-and-how.gmi, which will go on to generate the date and title/heading for the post. As the markup is so similar to Markdown, I thought I'd also generate a Markdown representation to mirror the posts over in my Github pages page, which is, let's be honest, where you're probably reading this.

I'm hoping to use this as a place to form a habit of writing posts to synthesise and clarify my thoughts on topics I'm reading and thinking about. Let's see!
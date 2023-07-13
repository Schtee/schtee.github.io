---
title: Weaving The Web, by Tim Berners-Lee
---
![An image of "Weaving The Web, by Tim Berners-Lee"](/images/2023-07-13-weaving-the-web/book.jpg)

*Weaving The Web - The Past, Present and Future of the World Wide Web by its Inventor* by *Tim Berners-Lee*, 1990

A couple of years ago I went on a quest to find the perfect note-taking software for me. I dabbled with [Roam](https://roamresearch.com/), but was looking for something less siloed. I tried [TiddlyWiki](https://tiddlywiki.com/), but found the tech stack quite clunky, as straight out the box it's just an HTML file that has no way to write your changes anywhere. Eventually I stumbled on [Obsidian](https://obsidian.md/), which was exactly what I needed: local notes, Wiki-style interconnected-ness with simple and (relatively) standardised Markdown for formatting. It got me thinking about the structure of the web and how fundamental links and connections _should_ be. I was inspired to read Tim Berners-Lee's book on the origins of the web. I took a bunch of notes, but these are the ones that resonated most strongly.

I'll refer to [Tim Berners-Lee](https://en.wikipedia.org/wiki/Tim_Berners-Lee) as TBL to save us all some characters.

---

From the foreword by [Michael L. Dertouzos](https://en.wikipedia.org/wiki/Michael_Dertouzos), then-director of MIT Laboratory for Computer Science.

> When I first met Tim, I was surprised by another unique trait of his. As technologists and entrepreneurs were launching or merging companies to exploit the Web, they seemed fixated on one question: 'How can I make the Web mine?' Meanwhile, Tim was asking, 'How can I make the Web yours?'

### Origins
- The seed of the idea that computers could become a _web_ of connected information was planted while TBL was in high school, after a chance conversation with his dad about the potential for computers to be more intuitive if they were able to model connections as the brain does.
- TBL envisaged a generic addressing scheme which would allow arbitrary connections, where previous hierarchical/folder/directory structures led to very rigid, restrictive, mutually exclusive relationships. 
- **1965** - The concept of _hypertext_ was established long before Tim's first forays with it, with [Ted Nelson](https://en.wikipedia.org/wiki/Ted_Nelson) writing about it in [Literary Machines](https://en.wikipedia.org/wiki/Literary_Machines)
	- Nelson also coined the term [intertwingularity](https://en.wikipedia.org/wiki/Intertwingularity) to represent the idea that concepts don't fit cleanly into boxes and ultimately everything is interconnected, which sums up a lot of what TBL was thinking about. His original work can be found in a sample chapter of [_The New Media Reader book_](http://www.newmediareader.com/book_contents.html#:~:text=21.%20From%20Computer,Nelson%2C%201970%E2%80%931974).
 
### Early iterations
#### Enquire
- **1980** - TBL's first attempt at software to represent an information web, [*Enquire*](https://en.wikipedia.org/wiki/ENQUIRE), was developed purely for his own use a full decade before his first client/server Web. He was already thinking about a platform that supported arbitrary conceptual linkage, as well as connections between computers.
- It **required** a description of the connection between linked documents. This imposes database-style relationships between concepts, where semantics can then be reasoned with and queried but would feel artificial in longer-form prose.
- Links were bi-directional - a concept that can only really work in a closed system, where one owner controls all the documents.
- I've just discovered that the [original Enquire manual from 1980 is hosted by W3C](https://www.w3.org/People/Berners-Lee/EnquireManual.htm).

#### Tangle
- **Late 1984** - TBL took another shot at developing software for connecting ideas called *Tangle*.
- As with Enquire's well-defined connections, Tangle was another example of TBL's fascination with the [semantic web](https://en.wikipedia.org/wiki/Semantic_Web), where meaning can be derived systematically. His intention was that you could build layered definitions/compositions of, and connections between, concepts to the point that the computer could break a question down into concepts it knew about to pull out strands of associated information.

### R&D and beyond
- **March 1989** - TBH developed a pitch for his idea for an interconnected documentation solution, to keep track of connections between people, their work and work artifacts
> Now imagine picking up the structure and shaking it, until you make some sense of the tangle: perhaps you see tightly knit - groups in some places, and in some places weak areas of communication spanned by only a few people. Perhaps a linked information system will allow us to see the real structure of the organisation in which we work. 
* **September 1990** - Hypertext was already a big enough deal that he was able to track down the _European Conference on Hypertext Technology_, held at Versailles, to pitch his idea
	* [Looks like there were only 3 held, each 4 years apart](http://www.hcirn.com/res/event/echt.php), with 1990 being the first.
* He tried to convince Electronic Book Technologies, developers of [Dynatext](https://en.wikipedia.org/wiki/DynaText), to convert their "electronic book" software into a web browser/editor as the changes required seemed minimal. He was met with a lot of resistance as traditional media companies were stuck in their traditional media-ways, needing central databases and never allowing broken links; where a publication stands complete by itself.

### The WorldWideWeb in production
* **Christmas 1990** - The end-to-end proof of concept, with a server handling connections from at least two clients over the internet using TBL's _WorldWideWeb_ browser (/editor hybrid).
* **August 1991** - TBL went public on newsgroups, posting his NeXT-compatible browser, a line-mode browser and a basic web server.
* He also made the smart move of allowing telnet connections to a server running the line mode browser, to allow the internet at large to dabble with the web using only their existing software/setup.
* **December 1991** - The first web server outside of CERN was launched at the [_Stanford Linear Accelerator_](http://www.slac.stanford.edu/history/earlyweb/history.shtml) in Palo Alto.
* **May 1992**  - Over-the-air code a la scripts/applets was demonstrated in in Pei-Yuan Wei's [ViolaWWW](https://en.wikipedia.org/wiki/ViolaWWW).
* TBL wanted the document reference address to be called a _URI_, as _identifier_ suggested immutability. The IETF work group pushed for _URL_, as _Locator_ suggested the same document could move. Tim eventually went on to channel his philosophy in [Cool URIs don't change](https://www.w3.org/Provider/Style/URI) in **1998**.
* **1993** - Mosaic was released for free to remove any barrier to entry and proliferate instantly.
> They also seemed to follow the unprecedented financial policy of not having a business plan at first: they decided not to bother to figure out what the plan would be until the product was world-famous
- **1994** - Microsoft bought in the browser code of a small NCSA spin-off named Spyglass to kickstart the project that would become Internet Explorer for $2 million (around [$4 million 2023 dollars](https://www.usinflationcalculator.com/))
- TBL notes that by Netscape being early to market and giving their browser away for free, bringing millions of people to their home page and giving ad impressions, and then charging for commercial licences and web services, they were _"acknowledging that on the Web, it was more profitable to be a service company than a software company"_. This seems like a profound observation for 1999 (or earlier).
- **May 1995** - Sun announced the [HotJava](https://en.wikipedia.org/wiki/HotJava) browser with integrated Java VM, as well Netscape announcing Java support. TBL notes that Java was a _"repackaging of James Gosling’s Oak language, originally designed for applications such as phones, toasters and wristwatches."_. 
	- I can't find a citation for those devices specifically but plenty around set-top boxes and PDAs. Regardless, [A Brief History of the Green Project](https://www.tech-insider.org/java/research/1998/05-a.html) states that they _"quickly came to the conclusion that at least one of the waves was going to be the convergence of digitally controlled consumer devices and computers"_. This would all, of course, come full circle when phones, wristwatches, and probably toasters run Android.

### The Future
- TBL sets out his vision
	1. The web becomes more of a platform for collaboration.
		- I think we're broadly here with a lot of large web sites having some element of user generated content. However, the majority of content users are generating isn't adding to the "web" so much as adding content to a given platform. This distinction is basically what the [indieweb](https://indieweb.org/why) is all about.
	2. _"Machines become capable of analysing all the data on the Web"_, followed by an explicit reference to _semantic web_. 
		- It's arguable we've achieved this after going around all the houses. [Large language model](https://en.wikipedia.org/wiki/Large_language_model) neural networks give us a similar, if fuzzier, end result while still allowing for content to be written in plain written language, without additional markup or metadata overhead.
- To achieve his vision, TBL says we'll need:
	- a computer (screen) always available
		- Think we can tick this off with the ubiquity of mobile devices/laptops/personal computers.
	- permanent/instant internet access
		- This too, through broadband and mobile internet.

### Some observations

- TBL was really hooked on the idea of hybrid web editors and browsers; of making the web "intercreative". I can see the power in this, but I guess the technical logistics get a little weird. Serving HTML is very different from building a form to receive and store data to then inject into that HTML.
- He was also really taken by Semantic Web. The concept pops up in a lot of forms throughout the book and it seems that it's only been realised on a very superficial level. It feels that with the rise of LLM / "AI" we've reduced the need for the web to be machine-parsable at a structural level, and we can, broadly speaking, reason with raw text. We've ended up solving it from the other end, accepting that the web is just context-free noise-soup, and relying on algorithms to derive patterns from it.
- There's no mention of JavaScript, which seems surprising for a book published in 1999. It was definitely an accepted and used language, but maybe not used in any capacity significant enough to warrant mention?

I was reading the book out of an interest in the origins of the web and the tech that drives it. I didn't take notes around the formation and operation of the [_W3C_](https://www.w3.org/), or some of the loftier crystal ball-gazing as it wasn't relevant to my specific context. This was a nice quote though (emphasis mine)

> Bias on the Web can be insidious and far-reaching. It can break the independence that exists among our suppliers of hardware, software, opinion and information, **corrupting our society**.
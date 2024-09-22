---
title: Jekyll Short URL Generator
---
I was reading [this post by J about setting up a simple URL shortener with no server-side logic](https://heavydeck.net/project/jsredir/) and it got me wondering if there was a Jekyll/GitHub Pages "native" way to implement something similar. It turned out to be very simple to put together!

### `redirect.html` layout

Basically my regular layout with a couple of changes:

```
<script>
	const url = new URL(window.location.href);
	const stay = url.searchParams.get("stay") != null;
	if (!stay) {
		window.location = "{{ page.redirect }}"
	}
</script>

<noscript>
	<meta http-equiv="refresh" content="0; url={{ page.redirect }}" />
</noscript>
```

Some simple JavaScript to redirect to the target page, unless a `stay` query parameter exists. If JS isn't available it'll use the `meta` tag to redirect.

### `_config.yml`

#### Add a new `scope`

```
  - scope:
      path: ""
      type: "redirects"
    values:
      layout: "redirect"
```

...so that `redirect` entries use the new layout

#### Add a new `collection` type

```
collections:
  redirects:
    output: true
    permalink: /s/:name/index.html
```

...which will cause redirect pages to be generated at {{site.url}}/[redirectname]/index.html. This allows them to be accessible at {{site.url}}/[redirectname] with no special serverside logic or web server config to handle these paths.

### Add the redirect entries

Now I'm able to add a [redirectname.md] to my a `_redirects` folder, and all they need to contain is:

```
---
redirect: [url]
---
```

So you can now hit [{{site.url}}/s/mastodon]({{site.url}}/s/mastodon) to get to my Mastodon page, or [{{site.url}}/s/mastodon?stay]({{site.url}}/s/mastodon?stay) to hold on the redirect page! I didn't have any particular usecase for this and it was more idle noodling, but [J's application of theirs for QR codes to stick on luggage pointing to a Lost & Found page](https://heavydeck.net/blog/lost-and-found-stickers/) is very smart!
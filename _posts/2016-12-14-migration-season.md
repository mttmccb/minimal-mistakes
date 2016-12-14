---
title: "Migration Season"
excerpt: "Some thoughts on migrating from Squarespace"
tags: [squarespace]
---

{% include base_path %}

I've been putting it off too long, I need to migrate the content from my [Squarespace blog](http://mttmccb.net) and eventually I'll point the domain here. However, it's not very easy to do.

The only export option is as a Wordpress file, which is basically just an XML file of all the posts and annoyingly the attachments which are a separate type of post. It doesn't include any images at all, they need to be done some other way.

So [this fork](https://gist.github.com/spiffytech/e73777e167dc5a8b6a87) by spiffytech of [evan walsh's original](https://gist.github.com/evanwalsh/6131008) was my starting point for converting the wordpress xml to jekyll markdown posts.

I only know enough ruby to be able to run scripts, everything else is a painful search and stab in the dark. The first hurdle was using hpricot (an XML parser) seem to fail so I switched to nokogiri. Then I wasn't able to read from nodes with a `:` in them, it would just fail miserably. So I had to do a quick find an replace to remove them from the source file and update the script. Lastly I updated the export so it matched my post format more closely. If you want to see what I use you have a look at [my fork](https://gist.github.com/mttmccb/d15fec44eeca3c93195f6a5d6b331f06) and improve on it.

## Not quite
That's not quite everything because it appears some of the posts weren't parsed correctly and attachments don't appear to have been handled at all. Some of this might be solvable by modifying the script but I think there will be a bit of manual work because some of the post images won't be usable anyway.

It's been a while since I attempted to migrate a blog but I remember why I usually just left my old posts to die. It's tedious, however I hope this will be the last time for a while and the markdown format will be more portable.

I'll be drip feeding in the old posts, for now they'll be in the drafts until I tidy them up.

Right now I wouldn't recommend you use Squarespace, it's a little too hard to leave.
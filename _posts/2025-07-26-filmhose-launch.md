---
layout: post
title:  "Filmhose - Listings for London's independent and arts cinemas"
date:   2025-07-26 19:30:17 +0100
categories: blog
tags: movies, films, london, listings, repertory
---

## The problem

London is very well served for independent cinemas, often showing classics, obscura and independent films that mainstream cinemas don't have.

But, it's not trivial to find or keep track of the films you're interested in. There's no way to search for a film across all the cinemas, or even to see what's on today, without painstakingly checking all the individual cinema sites. It's very easy to miss a rare theatrical showing of a beloved film.

## filmhose.uk

So, I made [filmhose.uk](https://filmhose.uk).

[FilmHose](https://filmhose.uk) lets you browse each day's listings for the next couple of months. You can choose between the [full listings](https://filmhose.uk/hosepipe) or the ["distilled"](https://filmhose.uk/distilled) listings, which have less noise from the big current releases that you can see "anywhere". You can also select only the cinemas you're interested in, if you don't think you'll ever make it to Romford or whatever (although the [Lumiere Romford](https://www.lumiereromford.com/) is cool, you should make the effort). You can also [search by title](https://filmhose.uk/titles) if you want to know where and when a specific film will be showing.

## A few wrinkles

A more commercially focused post would probably skip this section, but I'm not that so I'll share some caveats:

* Some cinemas' websites are not easy to scrape. In fact broadly speaking I'd say, the cooler the cinema, the more likely it is they do their website in some ad-hoc way that's difficult to scrape automatically. At the moment I don't have these, which is a pity:
  * [The Nickel](https://thenickel.co.uk)
  * [David Lean Cinema](https://www.davidleancinema.org.uk)
  * [Cinema Museum, Kennington](http://www.cinemamuseum.org.uk)
  * [Theatreship, Canary Wharf](https://www.theatreship.co.uk)
  * [Sands Films](https://www.sandsfilms.co.uk)

  At some point maybe I'll just ask them if I can have their listings, like it's the twentieth century or something. Or some of them have few enough that I could enter them manually. But for now I'm just doing the lazy thing and omitting them.
* There's a quite narrow focus on independent / arts cinemas. I'm not necessarily against adding the big chains (Odeon, Vue etc), but for nerds like me the indies' listings will be more interesting. Maybe one day.
* I'm relying on the scraped titles, which aren't necessarily very consistent. Eg. some cinemas will have "Lilo and Stitch", others will have "Lilo & Stitch". There's a lot of titles like "Amadeus [40th Anniversary]". I've tried to [normalize these a bit](https://github.com/Joeboy/cinescrapers/blob/main/src/cinescrapers/title_normalization.py) for sorting and matching purposes, but it's far from perfect. This means 1) the stats above are a bit unreliable, because they're based on the scraped titles 2) It's not easy to do things like automatically get interesting data like directors, release years etc. Although I might still see if I can figure out a way that mostly works well enough.
* I'm automatically generating the film thumbnails from images found on the cinemas' websites. Because these could have any dimensions, I'm cropping them to be square. I'm trying to be [slightly clever](https://github.com/Joeboy/cinescrapers/blob/581a66cd654055b4150e6244e42d2ee616221253/src/cinescrapers/utils.py#L77) when doing the cropping, but sometimes it makes suboptimal choices. I think it's mostly good enough. Originally I was quite hesitant to have the thumbnails at all, but people told me the site looked too boring.

## But overall

So far it seems to be working out pretty well. I'm able to get data for [27 cinemas](https://filmhose.uk/cinemas), currently covering [about 700 separate films](https://filmhose.uk/titles), [2500 showtimes](https://filmhose.uk/hosepipe), with an average of 36 film options and 67 showtimes per day. Film lovers in London are pretty blessed, especially when you consider that's not including the big chains.

The site loads very quickly and has very little extraneous nonsense, for me it's easily the best way to see what's on that's interesting. I hope other people will find that too.

## Where do I sign up?

You can't, it's a free website with no login. Just go to [filmhose.uk](https://filmhose.uk).

But if you really want to sign up for something you can follow on [X / Twitter](https://x.com/FilmHose) or [Bluesky](https://bsky.app/profile/filmhose.bsky.social).

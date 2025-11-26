---
title: 'Internet Speed Meter, but open source'
summary: "The making of Traffic Light or how I learned to hate Google"
date: 2025-11-18
draft: false
ShowToc: true
cover:
   image: "/programming/traffic-light/cover.svg"
   alt: "Traffic Light cover"
   relative: false
---

If you don't want to read my rant, you can download the app on [Github](https://github.com/leekleak/traffic-light) or [F-Droid](https://f-droid.org/en/packages/com.leekleak.trafficlight/).

## Maybe the single most useful tool on Android

I've been using Internet Speed Meter Lite for a long long time and it's one of the **most useful tools** on Android I can think of.

If you've never heard of it here's just a couple of example use cases:
- A website is taking a while to load? Just check the status bar and see whether it's just a really large site or if it's gotten stuck and you should refresh.
- Unsure if the stuttery video stream is the server's fault, or your network's? Just look at the status bar and compare.
- Monitor your privacy by detecting apps that use a whole lot of bandwidth for no reason in the background.
- Feel good about your newly set up Wi-Fi router and marvel at your gigabit speeds.

In fact, it's so useful that I think some Chinese vendors like OnePlus and Xiaomi have even made versions of the feature for their own Android skins! That makes me wonder why **neither** Google nor Samsung has anything similar. I *guess* I have a hunch ;)

## What happened?

So why would I make my own version if there's already an amazing app that does what I need? Well unfortunately it **no longer does.**

Of course, it's still on the Play Store and nor has it *really* succumbed to enshittification. In fact, from the looks of it, the app really hasn't changed at all since its release, still rocking the Holo design like it's 2014. The problem is, to *no one's* surprise - Google.

As a *certified* Google hater, I've been trying to live my life while using their services as little as possible. That means no Play Store, no Google account tied to my phone and as few of their other services as possible.

Unfortunately Google **really** doesn't like that.

You know [Focus Friend by Hank Green](https://play.google.com/store/apps/details?id=com.underthing.focus.friend)? Well I can't use it! That's because the app freaks out when it doesn't find the Play Store installed and crashes to the home screen with an error such as this:

![Something went wrong](/programming/traffic-light/noplay.jpg)

This wasn't that big of a problem, because the app is just a glorified timeout button with *pretty* questionable monetization (from what I've heard, obviously).

But then it happened to Internet Speed Meter Lite.

It would open, work for a couple of seconds, presumably try to load some ads, throw that same exact error and then crash to desktop. Truly heartbreaking.

The notification would sometimes stick if I exited the app before the error, but usually it would not and I was in no mood to fiddle with it every time I rebooted or it closed.

## In search of alternatives

Obviously, the first course of action I took was looking for an open source alternative. OSS developers, especially beginners, are famous for making the same app *over and over* again. I mean I just looked for a to-do app on F-Droid and I was met by like 30 different apps that are all also the exact same thing. 

So surely someone must have made an app with a status bar network speed indicator, right? **RIGHT????**

Yep. And it's called [Data Monitor](https://github.com/itsdrnoob/DataMonitor).

Unfortunately (and no offense to the dev), I *really* don't like it. For one, the UI and *especially* the readability of some parts is horrible. While I could live with that, there's a *far* bigger issue in that the status bar indicator barely works. Sometimes it runs for an hour, sometimes just a couple of minutes, but it always breaks and gets stuck perpetually showing the "0KB/s". 

> I haven't looked at their code, but from my own experience I'd guess that that bug is ironically caused by a buggy workaround to try and wrap a bandaid around the horrible API called TrafficStats.

That, combined with the fact that the app was last updated *2 whole years ago* led me to seriously consider just making one myself.

I mean I'd never made a GUI Android app before, **but how hard can it be?**

## How hard can it be?

Not very. 

To be entirely honest I was quite surprised!

Sure, there was *a lot* of frustration spent dealing with Android APIs and cursing in the general direction of Google. Remember the API I mentioned in the last section, TrafficStats? Well I struggled with it too!

![An incredibly angry comment I left about a bug I experienced](/programming/traffic-light/trafficstats1.jpg "Fuck TrafficStats in particular")

Also, the Network Usage API is sooo slow I had to make a custom Room database to save its outputs!

But find me a developer who *doesn't* get the displeasure of working with decrepit APIs once in a while!

I really liked making the UI, which surprised me a lot because I had correlated my experience of fiddling with CSS for hours with UI design as a whole. However apparently that's not the case. I was able to make it and make it look nice surprisingly quickly with headaches arising only due to my inexperience of working with declarative UIs like Compose.

![Animation showing interactive elements](/programming/traffic-light/overview.gif)

I really liked the Material 3 Expressive videos Google published around this summer, so I tried to make something **similar**. You'll notice some interesting fonts and weird shapes, which I think make the app look pretty pleasing. It's really a shame only a *few* apps I use have adopted the more playful design...

Also, have you tried touching anything? Almost all the UI components react to touch and at times it feels a bit like a digital fidget toy. Admittedly, I'd not be surprised if someone deemed that *overdone*, but I think it's pretty fun.

![Animation showing an incredibly playful bar graph](/programming/traffic-light/graph.gif)


## The End

Hopefully the app will be useful not only to me (but even that would be fine). Even if not very long, this was a fun journey for me.

I doubt I'll make many other apps *unless* some other tool dies on me and I'm forced to make an alternative, but I do quite enjoy fixing bugs and issues in other peoples' projects, so I doubt I'll spend too much time without touching Kotlin.

Of course, as any up-and-coming dev I'm looking forward to hearing feedback, but I expect to become disillusioned with it quite quickly. I've seen the kind of shit OSS and especially Android OSS developers have to deal with and it ain't pretty. 

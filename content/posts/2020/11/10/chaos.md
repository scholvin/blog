---
title: "chaos"
date: 2020-11-10T17:53:21-06:00
draft: false
author: "jks"
authorlink: "mailto:john@scholvin.com"
tags: [ "engineering",  "democracy at sunset" ]
---

If there's one thing I've learned in over thirty years as an engineer, it's something like a nerd's refactoring of the Maya Angelou [quote](https://www.goodreads.com/quotes/335-when-someone-shows-you-who-they-are-believe-them-the): _when you see a problem in a system, believe it_. A strange message in a log file, a squeak or rattle where there didn't used to be one, a dropped connection, maybe it all just seems slow, a fever. It means something, every time. If it goes away? It's coming back. If you can't figure out why? Doesn't mean there is no why. If you didn't dispositively find and affirmatively fix it, it's happening again. Them's the rules.

And often, though not always, it's going to get _worse_. Systems in error states often find their way into positive feedback loops. Whatever wiggled loose will move in the room it has, wearing away the surrounding material to make more wiggle room, and therefore bigger motion, and so on. A software program writing an error message too often can fill up a disk, creating bigger problems than what it was complaining about in the first place. An untreated wound can fester, and become susceptible to new, more dangerous infections. The wind blows a shingle off, which allows more rain in, weakening the structure that supports the rest of the shingles. Things go superlinear---and, by definition, quickly.

Build a safeguard? Yes. But what happens when the safeguard fails? Well, build several layers of them, then. Yes, you can. And while the probability of all of them failing at once drops with each new one, sometimes they interact with each other in complicated ways that induce new risks. And safeguards are expensive to build and maintain in their own right. At some point, you have to make the engineering / financial / social / political decision that you've done a reasonable job and get back to the work at hand.

Monitoring helps, too. Build that. But like safeguards, monitors sometimes fail, and always have non-zero implementation costs. Sometimes, too, monitoring systems can be so intrusive on the underlying process that they affect its performance. You can actually monitor something to death. The [observer effect](https://en.wikipedia.org/wiki/Observer_effect_(physics)) isn't just for the quantum realm. Another cost/benefit analysis ensues.

So, what to do? How can we make anything complicated work reliably and for the long haul? 

Good news. Outside the system stands the observer. Someone designed, built, safeguarded, and monitored. All flawed, of course, as any human process must necessarily be. The observer, who doesn't have to be the architect (and probably shouldn't be) must take in what they can, and _act_. If it feels wrong, assume it is, and investigate until you can prove it's not, or until you have a fix. The key word there is "feels." Knowing when something's out of order is a judgement call, subject to all the flaws and foibles. 

The second most important word is "until." The part that overrules the human subjective is the follow through. You chase the symptom until you can explain it or until you can remedy it. Black and white. Every time. No exceptions. Forever. That's what you do.

It's hard. It doesn't end. You can't quit.

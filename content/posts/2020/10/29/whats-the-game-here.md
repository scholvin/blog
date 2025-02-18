---
title: "what's the game here?"
date: 2020-10-29T17:21:53-05:00
draft: false
author: "jks"
authorlink: "mailto:john@scholvin.com"
tags: [ "meta", "hive mind" ]
---
{{<figure src="/2020/img/spoofers.jpg" link="https://batchgeo.com/map/b42f6c3263b32926510452054c539286" width="100%" caption="_charlatans_">}}

Another post about the blog infrastructure itself. I know. But the events of the larger world are a little too overwhelming to get my arms around at the moment, and my beloved White Sox hiring a [walking, talking Blue Lives Matter flag](https://www.radio.com/670thescore/sports/chicago-white-sox/bernstein-white-sox-kill-the-fun-in-hiring-tony-la-russa) for their next manager has wedged my CPU.

The email subscription feature here officially launched a week ago. I announced it on Facebook, and was heartened and excited by how many of my friends signed up right away. (Hi!) As you might expect, there was a wave of them over the first couple of days that tapered down to a trickle, until I mentioned it again. Then there was another, smaller spike, and it faded quickly after that.[^1]

But then a funny thing started happening this week. A bot is signing up. Every few hours, from IP addresses that are [conspicuously all over the world](https://batchgeo.com/map/b42f6c3263b32926510452054c539286) (and, therefore, almost certainly spoofed), I see the following sequence of events:

1. Someone visits the home page from a Windows box running Chrome, or more likely, a script pretending to be.
2. They click on on the Subscribe link (or pretend to, as above).
3. They sign up for a weekly subscription using a valid address.
4. The system sends them a confirmation email.
5. A very short time later, definitely too soon for them to get the email, they sign up for an "every post" subscription with the same email address.
6. The system (correctly) returns them a "you're already subscribed with that address" message.
7. They go away. I never see that IP address again.

I've received about 70 of these since Monday. The email addresses are mostly from gmail and yahoo, and generally look reasonable. They're English names, sometimes with a leading initial or trailing digits, and they're real addresses, mostly, as step 4 confirms above. Maybe 10% of them bounce because AWS has recently detected them as invalid. One or two got bounced by the recipient's system. Most go through. Nobody has ever replied to one of these confirmation emails asking me to go away, or clicked on the manage link in them to unsubscribe. It seems this thing, whatever it is, is subscribing repeatedly with once valid but now untended addresses.

I only hesitate a little to spell this "attack" out in this much detail. Normally you wouldn't want to tell an adversary you're on to them, but it seems almost impossible that they are coming back here on the regular. I don't think it matters.

So I'm trying to work up a theory about what's going on here, and I'm coming up blank. Why would someone fill up my subscription database, albeit extremely slowly, with abandoned email addresses? Seems the worst that will happen is that my system will send email that will never get read. I don't think they're trying to harm me; a DDoS would be coming at me way faster. If this looks like a familiar scam to any of you sharp nerds out there, or even (maybe especially) if you're not a nerd but have a fanciful explanation for what's going on here, I'd love to hear it. I guess I'll learn more when I send out my first weekly email this weekend, but I'd love a working theory.

And, even if you don't have a thought on that, keep those replies coming. I'm right here for ya.

[^1]: I thought about flogging it on Facebook a couple more times to make sure it got more views, but I grossed myself out even thinking about it.

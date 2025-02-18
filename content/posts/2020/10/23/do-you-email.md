---
title: "so, uh, do you email?"
date: 2020-10-23T07:15:13-05:00
draft: false
author: "jks"
authorlink: "mailto:john@scholvin.com"
tags: [ "meta", "debugging", "updated" ]
---

**UPDATE** 2020-10-23 20:15 CDT

I simplified the whole thing. Now there's just a single opt-in step. You still get a confirmation email, but you don't
have to click anything to make it work. I also went into the database and just updated everyone to be confirmed. As
a good friend said, there's no reason to overthink this.

Over 150 subscribers now. Feeling good, Louis!

---

Since launching about 14 hours ago, I already have over 110 people signed up, which is overwhelming and amazing! Thank you!

But there's something funny I'm seeing in the data: about 30% of you never completed the second phase of the signup, which is clicking the confirmation link in the email you should have received. Now, as far as I can tell, all the emails got sent (except a couple which bounced, and I handled those separately). So that means 30% of the signups must be in one of the following states:

1. Got the email, but didn't read it
2. Got the email, read it, will click the link later
3. Got the email, read it, clicked the link, something went wrong
4. The email's in a spam folder 
5. The email just never got delivered for some reason.

Of those, I'm especially worried about 3-5. Those would imply a bug or a misconfiguration---something I need to deal with. So I'm going to break my own rule and reach out to a couple of you in that "pending confirm" state with an email about something other than a new post. Not to shame you if you fall in categories 1 or 2, but to make sure you're not in categories 3-5, which would mean I have to get busy. And if it turns out most of you are in categories 1-2, then I need to adjust how long I will keep emails around in that pending state before I clean them out.

BTW, if you're not sure what I'm talking about, the subscription feature is up and (I think) working. [Here's a post about it](https://scholvin.com/posts/2020/10/22/signup-time/). Or you could just hit the [Subscribe](https://scholvin.com/email/subscribe/) link up top.

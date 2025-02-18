---
title: "subscriber update"
date: 2020-02-20T12:44:50-06:00
draft: false
tags: ["meta", "subscription system"]
author: "jks"
authorlink: "mailto:john@scholvin.com"
---

<img src="/2020/img/email-database.png">

I'm hard at work on an email subcription thingy for this blog. I can reliably be counted
on to spend a ton of time on the _infrastructure_ of a thing before I actually _use_ the
thing. Examples include pedalboards I've built, offices I've occupied, runs I've painstakingly
mapped out, etc. And it's also invariably
true that during these infrastructure building phases, I'll work very little on the overlying things themselves.
I think often of my uncle Mike, building his own house almost entirely by himself. He and
his young family lived in a cramped trailer on-site for about a year while this happened. The good news is
they're still in that kick-ass, one-of-a-kind house 30 years later. There's
something to be said for doing things right or not doing them at all.

Anyway.

Everyone is familiar with the workflow for signing up for emails: you enter your email address
into a form. Soon you get an email from the provider asking if you really did this, to make
sure no shady prankster is subscribing to stuff on your behalf. You click the link in that email,
and now you're signed up. You can also expect that in every subsequent email you get from that
provider, there's a link at the bottom where you can unsubscribe. This is what I'm trying to
build here.[^1]

I'm using a series of AWS services for this project:
* [API Gateway](https://aws.amazon.com/api-gateway/), which provides API endpoints for web-based services;
* [Lambda](https://aws.amazon.com/lambda/), which allows for arbitrary code to run in AWS's cloud without having to deploy servers;
* [Relational Database Services (RDS)](https://aws.amazon.com/rds/), a relational database (in this case PostgresSQL) that runs
in their cloud, also without having to deploy servers; and
* [Simple Email Services (SES)](https://aws.amazon.com/ses/), their service for sending email.

I'm already using [EC2](https://aws.amazon.com/ec2/) for the one server that I do provision and manage,
a small linux instance that
I use for general-purpose hackery, and which is also serving this page as you are looking at it.[^2]

<img src="/2020/img/email-flow.png">

It flows like this:

1. The user enters his email and cilcks "subscribe" on a page here on the blog. That is sent
via HTTP POST to the API Gateway.
2. The API Gateway forwards that message to Lambda. A python script there parses the message
from the API Gateway.
3. The python script sends a request to the RDS database to add that email address in a "pending" state, and 
to generate a [UUID](https://en.wikipedia.org/wiki/Universally_unique_identifier) for this user.
4. The database sends that UUID back to Lambda.
5. Lambda sends the email address and the UUID to SES.
6. SES generates an email to the user with the UUID encoded. The email says something like "someone
signed you up for this awesome blog! click here if that was you, or just ignore this."
7. The user clicks on that link, and the UUID and some other stuff are sent back to a different
endpoint on the API Gateway. 
8. A (different) python script checks the database to see if the UUID and the email match.
9. If so, the python script updates the users status from "pending" to "active" in the database.
10. The database lets the python script know it worked.
11. The python script triggers a "congratulations, you subscribed!" email to the user.
12. User gets email, is happy.

Lots of details are left out here because I'm still working it out, as are the various error cases.
Theoretically, at the end of this process,
when I have a new post to share to the subscribers, I can ask the database for a list of emails in the "active" state,
and use SES to send emails to those users.
Those emails would also contain a link to unsubscribe, along with the encoded UUID, should the user choose
to unburden themself from this garden of delights.

These AWS services are all new to me, and the learning curve is pretty steep. I've made good progress, 
completing steps 1-4 above to a proof-of-concept level. I've used SES a little bit before, so that
part should go a little faster. The later steps are just variations on what I've recently learned, so
those should go pretty quickly. The thing that worries me just a little is that I've configured all of these
services via the AWS web console, and not at all from the command line. If I had to reproduce this,
or describe to someone else how to do it, I'd have no shot. A scripted deployment from scratch is something
I'd like to eventually get to, because then this could potentially be open-sourced and used by
others who are trying to opt out of the part of the web that sees you as something to monetize.

I still have to do the math on what all these services will cost me, but it seems minimal. The database
runs all the time at a cost of about 43 cents per day. The API gateway doesn't start charging until there
are millions of hits, which seem unlikely for email signups. Lambda and SES are similar. So no backbreakers
here. The EC2 server and the storage behind it, which I've been using since long before this project,
will continue to dominate the bill at $21/month.

[^1]: I'm building it from scratch because I can't find an open source version I like, and all the free
or for-pay services who do this for you do _way_ too much tracking on the people using it. A 
bedrock of the philosophy here at scholvin.com is to get away from that kind of Internet experience.

[^2]: What's with all the AWS love? Love's got nothing to do with it. I've used it and I'm comfortable
with it. Google Cloud is weird, and I'd rather eat a box of frozen babies than try Azure. And for those
who would wonder how the previous footnote squares with this, I am _reasonably_ sure Amazon isn't
harvesting the data of their AWS users' users. I wouldn't be totally shocked to find out they
are, but a lot of the customers here who are way bigger than me wouldn't accept that. At some point
at the root of the fractal, the DIY model breaks down. It's not like I could forge my own semiconductors.


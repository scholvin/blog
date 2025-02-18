---
title: "cattle not pets"
date: 2024-11-02T14:41:18-05:00
draft: false
author: "jks"
authorlink: "mailto:john@scholvin.com"
tags: [ "meta", "arlee", "technology", "cloud"]
---
{{< jksfig src="/2024/img/ansible.png" caption="some ansible code" alt="a snippet of ansible code for configuring this VM" >}}

This post is primarily to prove out the new server I built for this blog this week. I need to make sure the content management system I use, [Hugo](https://gohugo.io), is configured properly, as well as the various other subsystems that make the machine go brrr. But while I have you here, allow me to update on the (technical) state of the blog and some nerdy tools I've been playing with.

From the beginning, my intention has always been for this to be a 100% independent enterprise. It's not like I post anything so controversial that any moderating team (or, increasingly, some moderating LLM bot) would take it down, but I felt the need to reduce that probability to zero. Obviously, the one thing I don't have is a data center, so I did have to pick [someone who does](https://aws.amazon.com), but everything on top of that layer is under my full control. I administer the server, I maintain the installations of the various open-source packages that put the pixels on the screen. I patch the holes when the water gets in. This isn't a thing that most normies can do, and I would not advocate this life to anyone who doesn't already have the skills and time to make it work. There are a zillion platforms out there for folks who want to just write and let someone else handle the bits. But it does turn out there is a [growing community of folks doing it this way](https://indieweb.org/).

The challenge this past week was to stand up a new server (virtual machine) and move the content over to it in the most seamless and automated way possible. The operating system on the old server had reached end-of-life and the providers were no longer providing updates, security patches, etc. I made the decision to create the new one using scripting tools that basically bring the whole thing up from nothing, so when the operating system I'm using now eventually goes EOL, the next migration should just require running these scripts again. This should also, theoretically, give me a better chance at moving this thing away from AWS and to another cloud provider.[^1]

Managing compute resources in this automated way requires a bit of a change in thinking. "Cattle, not Pets" is the mantra. The metaphor kind of speaks for itself: your compute resources should be something more-or-less interchangeable. You should be able to bring them up or down at will without any data loss or a whole lot of work. I've never actually farmed cattle, and I'm sure that they require a lot of care in their own way, but there's a reason the big ranches just give them numbers, not names. Unlike the little fur babies we bring into our homes, who are doted upon and whose individual personalities are cherished.

{{< jksfig src="/2024/img/arlee-chair.jpg" caption="pet not cattle" alt="Arlee in a chair" >}}

And so it shall be with compute resources. In the old ("pet") way, when it was time to make a change, you'd log into the server and install the software, edit the configuration files, stop and start processes, and do whatever else was needed to make it run. In the new ("cattle") way, you instead write a script in some central, more permanent location (in this case, on my Mac) containing all of those configuration changes, step-by-step, and then you run the script to make the changes remotely. If you have hundreds or thousands of servers, it's pretty much a requirement. Or if you only have one but you may want to recreate it exactly somewhere else, this is The Way. So that's what I did, using two different tools: [Terraform](https://developer.hashicorp.com/terraform) to provision the cloud services I needed from AWS, and [Ansible](https://www.ansible.com/)[^2] to actually configure the server from bare metal. The scripts take about 30 minutes to run, and then there was an additional 10 minutes of manual stuff for me to do after that. In future iterations, I'll try to get that closer to zero, but this was good enough for now.

Anyway, this was a test of the emergency broadcast system. If anything looks weird or isn't working right, please let me know!

{{< jksfig src="/2024/img/terraform.png" caption="some terraform code" alt="a snippet of terraform code for configuring this VM" >}}

[^1]: I've been meaning to move away from AWS for a long time now, because Jeff Bezos is a truly repugnant human, and every dollar I give him nauseates me. The other big hyperscalers (Google Cloud, Microsoft Azure) aren't really any better, but there are some smaller cloud providers out there I intend to explore soon. The Terraform script I wrote to provision the AWS resources will need a full redo at some other provider, but the Ansible scripts for configuring the server should work without modification.
[^2]: I have no idea why so many of these open-source projects have such deeply stupid names.



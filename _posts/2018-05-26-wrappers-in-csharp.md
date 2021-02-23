---
layout: post
title: Wrappers in C#, and when not to use them.
tags:
  - nodejs
description: >
  A rant about wrapper dependency hell.
hero: /assets/img/bitsetbg.jpg
overlay: green
published: true
---

I no longer agree with this article, but am keeping it here as a reminder. As you can tell, I was a bit frustrated. What I do still agree with, though, is the NodeJS dependency stack is absolute hell.
{: .notice-alert}

When working on a project recently, I was required to do some networking to communicate between the C#.NET application I was creating, and a remote online server. Sounds pretty easy, right? Well, I’d been thinking about a couple of solutions, when I remembered an easy networking solution called Socket.IO (which you can check out here). Unfortunately, this program was native to NodeJS, and wasn’t available for a C# application, which sucked.

After a little searching, however, I found a C#.NET wrapper for the program, which could be installed by Nuget in VS2015 natively! It’s a great compatibility fixer, and you can find it on Quobject’s Github page [^1]. So, I set to work creating the client in C#, and the server in NodeJS. The syntax for both of them is remarkably similar, and after some tweaking from the Github example scripts, I managed to get this:

![pic](/uploads/wrapperArticleSS.png)

Obviously the server address is censored, but the logic of the script should still be pretty clear.
It connects to the server, and then sends an “`isLatestVersion`” request to the server, along with the current version number of the program, and waits for a response. When it gets one back, it checks whether the value is false, and if it is, starts the update program.

However, there was a caveat with this system. The windows form that handled the updating used a third party Node package designed for use with Socket.IO, called “delivery”. It was made by primarily the same developers, and based on the newest version, and was labelled as “fully compatible” with C#. This is where the lesson comes in:

Don’t use wrappers if you are going to use third party packages.

It’s one or the other, is the point. Because, as soon as that happened, everything completely exploded [^2]. Blunt, but true. When using the package, I first noticed that it used an automatically executing asynchronous function, which immediately raised red flags, as C#’s wrapper doesn’t like that at all, from previous testing. When running it, sure enough, it spat out that the variable “window” wasn’t assigned in the async function call, as it was coming from a C# source, which doesn’t have a window property. This kind of left me in a bad place, so I removed the asynchronous function and window variable from the package entirely, and used C#’s native systems instead.

This only created more problems, as the incompatibilities that I couldn’t see before were now unearthed, grisly and disgusting, for all the world to see. First, an error involving the “Delivery()” constructor used in my actual native NodeJS script broke, which was likely due to my meddling with the window function, however was fixed by a thorough crawl through the documentation and package source files, and a quick change in the script from using “var delivery = new Delivery()” to “var delivery = delivery.connect(ip, apic, {reconnect:true/false})”. Much uglier, but still functional. Then, an error surfaced to do with MIME, one of the package’s dependencies, and entirely unrelated to my project. At this point, I was getting a little tired, but soldiered on to try and fix the error.

After some research into the error code I received, it appeared that **another package entirely, Knox,** was causing this error, one of MIME’s dependencies! This is when I learned my lesson. When a third party package is ported over to another language, all it’s dependencies have to be as well. This creates an inconceivable number of errors if they aren’t all properly ported with identical syntax, and digs a very deep rabbit hole from which it’s nearly impossible to crawl out of.

I eventually did fix the cross compatibility issue, but only by contacting the developer via. a pull request and actually changing the code of the package itself to support a lower MIME version with the command! In my opinion, that was more stress than using a more complicated networking solution, but having little errors due to native compatibility.

I’m never using a wrapper and third party tools together ever again.
Thanks, and adieu.

[^1]: Do not use this software, it is long outdated now and very deprecated.
[^2]: Maybe this wasn't the wording in the original article...
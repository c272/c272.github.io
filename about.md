---
layout: page
title: About
permalink: /about/
published: true
---

<div class="page" markdown="1">

{% capture page_subtitle %}
<img
    class="me"
    alt="{{ author.name }}"
    src="{{ site.author.photo | relative_url }}"
    srcset="{{ site.author.photo2x | relative_url }} 2x"
/>
{% endcapture %}

{% include page/title.html title=page.title subtitle=page_subtitle %}

# Welcome.
Here, I post all of my programming projects in C#, C, and C++, as well as posts about how they were put together, and things I found interesting while making them. I am currently working @ Arm on their new architecture.
Here are some of my projects, if you want to browse:

**Major Projects:**

- [algo](https://github.com/c272/algo): A flexible programming language which aims to have a more mathematical syntax, and a simple standard library.
- [easyCase Casemaker](http://www.forums.court-records.net/viewtopic.php?f=10&t=32837): A simple and efficient way to make Phoenix Wright fan cases, all written in C#.NET.
- [quest](https://github.com/c272/quest) (currently private): An SFML game engine written entirely in C#, with no other dependencies.

**C#:**
- [iro4cli](https://github.com/c272/iro4cli): An open source reimplementation of Iro, a generic lexer file generator for text editors, which is closed source.
- [kahootify](https://github.com/c272/kahootify): A Kahoot OCR question detection program which allows the user to automatically search for questions. Utilizes heuristics and open source OCR.
- [gridsolver](https://github.com/c272/gridsolver) (currently private): A number grid solving program which utilizes heuristics and multithreading to reach an answer quickly, even at high complexities.
- [nbt.net](https://github.com/c272/nbt.net): A Minecraft NBT format serialization library written in pure C#, which uses attributes for serializable class tagging.
- [sauron](https://github.com/c272/sauron) (currently private): A Minecraft block finding project, which can locate any type of block in a world. Utilizes multithreading.
- [mCTF](https://github.com/c272/mCTF): An emulator for the mCTF specification, written for RACTF 2020.
- [spinda](https://github.com/c272/spinda) (currently private): An ASP.NET forum framework, built from the ground up using Nancy.
- [burrito](https://github.com/c272/burrito): A C# API wrapper generator, which can automatically update serialization classes based on received API data.
- [SharpRSA](https://github.com/c272/SharpRSA): A simple C# implementation of the RSA encryption algorithm.
- [rhythm](https://github.com/c272/rhythm): A responsive text editor with intelligent suggestions, built for the Algo programming language.
- [sharpie](https://github.com/c272/sharpie): A remote source based C# package manager, which has become a part of the Algo language.

**Java:**
- [gadzooks](https://github.com/c272/gadzooks): A simple raycasting engine utilizing Swing for graphics.

**Node:**
- [chatot](https://github.com/c272/chatot): A minimal and compact forum framework written in NodeJS, using Rokkit as a flat file database.
- [jLMC](https://github.com/c272/jLMC): A Javascript emulator of the “Little Man Computer” by Peter Higginson.
- [Rokkit](http://npmjs.org/rokkit): A JSON database package for Node, hosted on NPM.
- [steamguardgen](https://github.com/c272/steamguardgen): A program that automatically generates Steam Guard codes.
- [steamconfirmer](https://github.com/c272/steamconfirmer): Automatically accepts outgoing trades for a Steam account.
- [steamacc-rand](https://github.com/c272/steamacc-rand): A steam account generator running off dynamic Node. Now deprecated.
- [helloworld.js](https://github.com/c272/helloworld.js): Plays Louie Zong`s “Hello World”, in code.

**Python:**

- [graphroot](https://github.com/c272/graphroot): A program that finds the roots of graphs, taking in a simultaneous equation.
- [primecrawler](https://github.com/c272/primecrawler): Searches for primes, starting from a user-set number.

If you want to use or fork any of these projects, they are (mostly) freely available to download and use for whatever purpose you want.

Also, if you're here to read the blog about these projects, you can click [here](/).

Finally, here's all my accounts linked to this blog, just in case you wanted to contact me.
* **Github:** @c272
* **Business Email:** larry@c272.org

</div>

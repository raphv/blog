---
layout: post
title:  "About the tech used in this blog"
tags: technology
excerpt: "...and what it says about tech in general (a rant on the state of the web)"
toc: true
---
In this post, I talk through some of the steps I’ve used to set up this blog, and I explain why this tells a lot about the current state of technology.

In a nutshell, this is a perfect tool for me and it lives up to its promises of being quick to set up and very flexible.
But it’s far from perfect for many many people.
It only works for me because of the huge time and effort I’ve already invested on other tools.

Like everything in technology, using Jekyll for a few days made me love it and hate it at the same time.
The web ecosystem is broken and Jekyll isn’t fixing it at all.
It’s still broken, but in a way that is easier for me to use than other tools.

If you want to go straight to the part where I rant about how technology is broken, [just click here now](#-what-does-it-say-about-technology)

## 🛒 Why I chose Jekyll

I had long thought about starting a new blog, and I had previous experience using Wordpress, both self-hosted and via Wordpress.com, as well as a few other Content Management Systems (CMS).
I’ve also taught students how to use Wordpress, and I’ve managed a hosting platform where we had 180 instances of it running.
And I hate Wordpress.
I’m not going to give all my reasons here, I could write a whole blog post about that.
Let’s just say that its long history has made it a very inconsistent and bloated tool, both from the User Interface (UI) perspective, and behind the scenes in technical terms.

Having created pure HTML static pages in the late nineties, the idea of static website generators, combining the benefits of CMSes and of static sites, has appealed to me for a while, and I was just waiting for an opportunity to try it.
I chose Jekyll because of GitHub Pages’ support for it, and because its description made it seem very straightforward.

## ⚙️ The setup process

To have Jekyll running on **Windows**, publish my first blog post on **GitHub** theme, and make all the small changes I wanted to make, I’ve had to use a surprisingly broad array of technologies.
For many of these, I was already familiar with the technology.
For others, I had to transfer knowledge I gained from other technologies (e.g. I’ve used package managers before, but never gem).

Here’s a non exhaustive list of what I've had to use:
- I used a **command-line interface (CLI)**, and the one I've chosen is the bash shell in **Windows Linux Subsystem (WSL)**.
- This means that I'm relying on **Linux** in general and Ubuntu in particular. That's 2 operating systems on one computer, just to get a blog running.
- I've downloaded packages using two package managers (because I've used **aptitude** to download **gem**).
- I needed some familiarity with networks to understand what "serving on **localhost**" means.
- I've edited a **YAML** file for the blog’s configuration (It has its own idiosyncrasies and doesn’t work very well in Norway)
- **Markdown** is the language in which the content of block posts is written.
- I’ve had to understand the way themes can be **"subclassed"** to be modified.
- When I needed to change colours in the theme, I’ve had to use **CSS** and **SCSS**.
- When I’ve decided to modify the footer, I’ve had to use both **HTML** and a templating language named **Liquid**
- I had a nice open source font I wanted to use, [Kurier by Małgorzata Budita and Janusz Nowacki](https://jmn.pl/typografia/kurier-i-iwona/), and I didn’t want to use Google Fonts for privacy reasons, so I had some preparation to do there too.
- For publication, I first considered **GitHub Pages** - you need to know **version control** in general and **git** in particular.
- Finally I decided to host it on my own server, I have used the File Transfer Protocol (**FTP**).

## The pros and cons of Jekyll

### 👍 The pros

It perfectly fulfils its promises.
It’s fast, it’s flexible, it can be hosted anywhere.
The default theme can be easily extended – I’ve only needed a few lines of extra code, and these lines were very easy to identify.

The use of a version control system and text files rather than databases makes it incredibly easy to backup, duplicate and transfer.
It also enables me to write offline in a text editor – including on mobile phone with [Markor](https://github.com/gsantner/markor), an open-source Android app which has Jekyll-compatible templates.

In terms of how long it took to set up, it surely is slightly longer than Wordpress, but this is my first time with Jekyll, and in the long run there won't be much difference.
Just writing this blog post took nearly as long.

The choice of technological bricks suits me, since they are either technologies that I already know (HTML, CSS, Markdown) or close enough to technologies I already know (Liquid is very close to Jinja and Django templates), and the generally philosophy of Jekyll is to use bricks for just one thing, but to choose good bricks.

### 👎 The cons

Jekyll’s biggest downside is that these bricks are just too many.

These are all pre-requisites that one needs to know about, or has to learn on the go, just to set up a blog post, change the colours and fonts and add some text in the footer.
I am fortunate that these are things that I’ve learned over more than two decades of being online and trying to make websites work.

I’ve had errors at every single stage, because in many cases I prefer to use a *trial and error* approach than follow instructions step by step in detail, but also because there are always some subtleties that are not fully covered by instructions. Like working with WSL.

Throughout the process, I’ve had to use many sources of information, including official websites (for Jekyll and GitHub) as well as StackOverflow, the famous community-moderated Q&A forum.
Another source was reading the actual code from Jekyll themes, to understand how other have written code for it.

I haven’t used YouTube, but it’s also a great source of information, because to be honest, **official documentations are often terrible, because they are written for people like me**.
They are great when you know a lot and want to go straight to the point, but they are totally inaccessible to beginners.

### ⚖️ My verdict: Jekyll might be the lesser of (some) evils

You might think at this stage that I’m hating what I’ve just described, but for me the pros more than compensate the cons.

Despite the simpler learning curve, Wordpress is going to be at least as painful if I want to reach a similar result.

Another reason I prefer Jekyll over Wordpress is the way overcoming technical issues fits my rewards system better.
Each of the challenges I’ve faced these past few days was self-contained and had a rather elegant and satisfying solution.

An example: Changing a colour? Let’s identify where the CSS code for background is located...
There aren’t that many files, and the development tools in my browser even tells me in which file it’s defined.
It took just a few minutes, and it had a happy ending.

On the other hand, anything non-trivial with Wordpress feels like trying to remove a splinter from a dragon’s wing, while the dragon is flying.
I’ve often ended up modifying some PHP function hidden deep in a Wordpress theme or plugin just to display things the way I want.
Sometimes it crashed immediately, most often these quick fixes wouldn’t survive an update.
Rather than rewarding me, tweaking Wordpress has been an endless source of frustration.

But still, I’m left wondering why we can’t have something that combines the pros of Wordpress and those of Jekyll.
The answer I’m afraid is no, because in 2021, _**technology is worse than ever**_.

## 👨🏻‍💻 What does it say about technology?

As much as I love making stuff for the web, the current landscape of web technologies is a series of tools that only serve technologists and technology companies,
that are inaccessible for those who do not want or cannot invest the time to keep up to date with the latest evolutions of technology, and are barely any better for self-publishing amateurs than what we had 25 years ago.

### 💔 Technology is fragmented

There are more bricks than the ones I've interacted with, they're just the tip of the iceberg.

Everytime I update my website, I run a script written in **shell script**, which first calls the Jekyll builder, written in **Ruby**, and this Ruby is compiled into a bytecode which runs on a "virtual machine" written in **C**.
Ruby integrates with various libraries on my computer, most of which also written in C, but possibly a few other languages as well.
Based on options described in **YAML**, Jekyll converts **Markdown** content and **Liquid** templates into **HTML**, converts **SCSS** into **CSS**, and collects images and font files to build the site.

> Simple, isn't it?

Despite having very few images for now, I have three different formats already: **SVG**, **JPEG** and **PNG**, which all use different techniques to describe and/or compress visual information.

Some of these technologies are standard, for example the image formats above work on every browser (although only since 2011, which was 15 years after the invention of PNG),
and they're standard only because browsers act as a bottleneck that forces technologies to generate some form of HTML, CSS and/or JavaScript at some point.

But generating HTML can be done in many different ways, and [a popular website lists no less than 322 equivalents of Jekyll](https://jamstack.org/generators/),
some of which are extensions of Jekyll, and others are "ports" - in other words, they do the exact same thing as Jekyll but they're written in JavaScript instead of Ruby.

Some of these projects will never achieve any success and will die, and one large part of my selection process was choosing one that was less likely to die.

On a side note, HTML and CSS themselves are not really good at being stable standards themselves, [despite being maintained by an official consortium that shows its commitment to stability by using relatively old-fashioned web design](https://www.w3.org/).
These "almost-standards" evolved in a context of "browser wars" in which browsers from a different vendor, or browsers from the same vendor but different years would accept different versions of HTML.

### 🗜️ It's all ad-hoc solutions

One of the early promises of the Web was to create a media that everyone could use to publish, with a very low barrier of entry.
Personal web sites from the late nineties, with social dynamics embedded in their "webrings", were no worse as publishing outlets or less social than modern blogs or Twitter.
But they didn’t look good and had limited interactivity, so the technology community started building "solutions" to this problem, and built the modern web as a fragile tower made of disparate bricks.

To be honest, that was the case from the very beginning: When sir Tim needed to share documents at the CERN, he built a solution that worked with existing NeXT workstations, 
the network infrastructure in place at the time, and built a document description language based on the existing "Standard Generalized Markup Language" (SGML).

Then the solution to the problem of styles was a language called CSS.
And the solution to HTML, CSS and JavaScript changing all the time was libraries (jQuery, Modernizr, etc.) that create code that works everywhere.

The problem that Jekyll is trying to solve is the fact that, if I want pages in a blog to look the same, then I need to copy everything that surrounds a blog post (footers, headers, menus) on every post, and also keep the list of posts updated.
I’ve tried maintaining the archive of a mailing list manually in pure HTML in the late nineties, it’s boring as hell.
It’s not the only software tool to do so, Wordpress does it too, but it relies on things like databases that makes it slow and harder to distribute (With static site generators, I can easily give you my website on a USB stick).

So the result is that every time a new problem appears, a new technology appears, but this won't solve every aspect of the original problem, or this will generate new problems, so the cycle goes on.

### 🚷 Technology isn’t designed in a human-centred way

If you can’t relate to any of the "problems" that I’ve discussed about and that modern web technologies are supposed to solve, then you’re not alone!

This issue had already been diagnosed by Alan Cooper in his 1999 book *"The inmates are running the asylum"*: people like me who only see the benefit of these complex technologies
are **apologists** but most people who have to deal with technologies are **survivors** that suffer from this complexity.

At the core of this issue is the fact that all the problems being solved by technology are technologists’ problems.

And to be even more precise, it's about solving the problems of *technologists who work in technology full time and have time to keep up to date with the latest trends and work on side projects.*

As an example, CSS was created not because web sites couldn’t be styled – the "tables with blank pixels" techniques described in the 1996 best-selling book *"Creating Killer Websites"* did a decent job –
but that this was done in a clunky way, and software developers always try to gain efficiency and to find solutions that they deem to be "elegant" *(a very subjective notion that allows senior developers to act as gatekeepers)*.

Markdown solves the problem of being too lazy to add `<p>` at the beginning of each line (the creators of the HTML standards have already catered to our laziness by making `</p>` optional.
Also, it converts the ugly straight quotation marks inherited from typewriters into nice asymmetrical curly ones, and therefore caters to the psychological needs of typography nerds like me.

None of these are really the original problem that I had, which is **writing content**.
I could use Wordpress, I could make Twitter threads, or I could upload unformatted text documents onto a cloud provider and call it a blog.
What I'm doing right now is just solving it in a way that I am marginally more satisfied about, and that people won't frown upon if you tell them "it's my blog".

### 💰 It’s also about Big Tech

Some of these technologies are not just solutions for the problems that workers in the tech industry have, they’re also solutions for their bosses.
We’ve already mentioned the browser wars, and the fast and disparate evolution of JavaScript, HTML and CSS in the late nineties was a direct consequence of this battle between Netscape Navigator and Microsoft Internet Explorer.
In a typical corporate move, both the name and the syntax of JavaScript are an attempt by Netscape executives to capture the popularity of Java.
This language was invented in 10 days, but nowadays it powers most of the web.

Yes, most of the toolset I’ve described above is **open source**, but the biggest beneficiaries from open source technologies are big software corporations:
- They can pool their efforts on some very complex pieces of software.
- They benefit from the volunteer work because software developers love to step in to improve these products.
- They increase their visibility and attract a larger technology-minded user base, thereby reinforcing their position as market leaders.

An example: Google Chrome and Microsoft Edge, the successor to Internet Explorer, share a large part of their code, called Chromium.
For many reasons, the browser war has become pointless, but it's still worth keeping control on a valuable asset.
Chromium is Google and Microsoft's [treaty of Tordesillas](https://en.wikipedia.org/wiki/Treaty_of_Tordesillas),
an arrangement that leaves them free to pursue world domination on other grounds.

This logic in technologies like React.js, a popular front-end framework invented by Facebook that is way too often used in places where simple static HTML would be more than enough.
Thanks to the popularity of that framework, Mark Zuckerberg's company can hire software developers who are not only trained with common web technologies, but also with the in-house tools.

So, in other words, this is a technology that solves a training and staffing issue, not an issue for technology users.

Big Tech has also shown its power to strangle publication technologies.
Google, by launching its "Reader" product in 2005, has supported the popularity of RSS feeds, but then alienated millions of readers and bloggers by stopping the product 8 years later.

I long hesitated between self-hosting, and using GitHub Pages.
GitHub Pages would have allowed me to update my blog more easily, as it has first-rate support for Jekyll (well, they've invented it!).
But even though I removed many common tracking technologies from my website (no Analytics, no ads, no scripts, fonts or images hosted elsewhere), publishing it via GitHub would have meant that GitHub's servers would keep a trace of my visitors.
GitHub is a company whose products I love. They've made version control and collaboration super easy. They have the cutest logo ever, the Octocat.
But GitHub is a company that has been criticized for offering services to the United States' Immigration and Customs Enforcement, and GitHub is owned by Microsoft, the biggest US company by market capitalization as of 2020.

And even with self-hosting, I am strengthening them by talking about them and using them to back up my files.

### 🏴 It's also about patriarchy and privilege

Yes, you've read correctly. And I know what I'm talking about, I'm western European, highly educated, cisgender, heterosexual, white, male and in a good financial situation.

**Who can afford to learn about all this technology on their free time?**
Certainly not people who have to work a second job or take care of young children until everyone falls asleep.
Probably people who were offered computers at a very young age, a factor that is playing a role in the gender imbalance in technology.

Who can afford to contribute to open source projects for which they aren't being paid?

Who can afford to get in an argument with technology gatekeepers and tell them that they don't need to know everything about all of that just to publish a blog?

So why am I doing this? I'm bored and I need something fun to do.

I might someday find a job where I'm paid to do it, but I wouldn't really be helping people.

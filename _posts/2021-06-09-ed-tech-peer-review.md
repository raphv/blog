---
layout: post
title:  "EdTech for peer review: my experience"
tags: education technology
excerpt: "What I learned from testing a novel peer assessment app"
toc: true
---
## The context

At the start of this academic year, my employer started working with an EdTech company who provides (amongst other tools) a peer-reviewing platform.
This was the time when the second wave of the Covid-19 pandemic struck, and we were more than happy to have a solution that could complement our online courses.

### The Web Development course

One of the courses we used it for had been redesigned just a year before.
It is a second year course in our **bachelor's programme** where students get an **introduction to web development**.

The learning curve is quite steep, since this is the most technical course in the curriculum, but this curve is addressed by giving exercises of increasing complexity to complete over a number of weeks.
In a pre-pandemic situation, this would happen in a classroom, and students would get multiple opportunities to try and fix their work while lecturers walk around the class.

Last year, the pandemic hit halfway through that course, and proper feeback became suddenly infeasable.
We now had to provide 5-minute video slots for feedback once per week, and we had no opportunity to "walk around the class" and come back to the same students before the following week.
It also became much harder for students to help each other than when they were sitting next to each other.

When the second wave hit, we knew we wouldn't teach the same way through a second lockdown.
We were also affected by the decision to let all first year students go through, and we had bigger classes than the year before (about 50 students for each of the three lecturers on the course).

The peer review platform from our EdTech partner seemed to offer a great solution:
for each of the web development exercises, our students would deliver their work on the platform, they would then review each other, and we would give a final layer of feedback to double-check.

We created 5 small peer-review assignments for each of our classes.
Each of these assignments was graded on a list of "pass-fail" criteria, e.g. the absence of technical errors, or the use of specific techniques taught through recorded video tutorials.
Each student would be randomly assigned two peers from the same class.
If a student passes the peer assessment, they then get assessed by a lecturer.
If they fail, they get another chance.

### The Design Thinking course

We experimented with peer feedback on another course, this time for our **master's programme**.
The course follows roughly the 5-step "Design Thinking" model created by (or at least proselytized by) the Stanford Hasso Plattner Design School.

The final deliverable is a "portfolio" report which describes how students have implemented this design process to create an innovative product.
Each chapter of the report corresponds to one or two steps in the model.

At three points throughout the process, students deliver a draft of a chapter of the report and receive feedback on it.

The experience that students and lecturers had with the peer review tool was radically different in each course.

## The outcome

The implementation of peer review had much better results in the Design Thinking course.
I describe why that course was a success and the other one wasn't, I reflect on why setting up this technology turned out to be more tedious than expected.

### The good: the successful course

In the Design Thinking course, we received praise from students for our innovative use of technology.

On the lecturer side, we were also happy with the quality of comments that we saw: each group received valuable insight on the content, the writing and the structure of their document.

The content of comments revealed interesting questions about the course, about design and technology, and about writing reports in general, and we could continue the discussion when we met in class.

Students were happy to see what each other were doing, and this also helped with keeping them motivated and on track to hand in the final report without too many sleepless nights at the end.

### The bad: the less successful course

On the other hand, in Web Development, students were very critical of the same product, and feedback was also of a lower quality.

#### So, what was different?

The first major difference was that in the Design Thinking course, we focused on gathering and offering feedback, while in Web Development, we wanted to check how far students were within the course progression.

It's the difference between asking students for an opinion, and asking them to do "the lecturers' job" of providing assessment which felt more summative than formative.
Although this sounds like it could be little more than a matter of framing things correctly (which can make a considerable difference), several factors played into that or made it worse:
- The result of the process was a pass/fail decision, that led to retaking the assignment the next week - leading to a feeling of uncertainty (on the workload that was involved) and arbitrariness (since students didn't fully understand the criteria the first time).
- The process was less direct in terms of User Experience: the content to be graded couldn't be displayed in the same browser window as the criteria, and some criteria required multiple steps to be checked. On the other end of feedback, this also meant that students didn't have a direct way of seeing *where* their mistakes were located within their source code.
- There was more work involved in understanding the criteria and applying them, e.g. checking specific files for specific code elements - although the whole point of making it a peer assessment was to get students through that process, and the result was that students felt less secure about their decisions.
- This insecurity was compounded by fear about making the "wrong decision" and being responsible for it - we tried to address that by having lecturers manually check all works fulfilling 60% or more of the required criteria at the peer review level, but this wasn't enough.
- The subject of the course itself was a major difference, since it was unfamiliar to most students, and because it's somehow harder, even for us, to provide quality feedback on this kind of subject - I am struggling to find a good balance between "computer says no, try again" and re-explaining core code concepts from zero.

The very structure of the Web Development course caused an additional problem:
students really needed to keep track of their progress, and the only way they could do this was either to open each of the assignments individually (there were up to 10 hand-in boxes, given that the platform required us to publish "2nd attempts" as separate activities), or to search for past emails in their inbox. 

This generated tremendous friction for our students, reinforced by the fact that there was no easy way of structuring and hierarchizing the list of peer review activities.

### The ugly: the burden of self-service software

New technologies don't always simplify our jobs, but often generate more work for ourselves, and this tool was no exception.

We had to:
- Set up each assignment, which includes:
  - Writing instructions
  - Writing grading criteria
  - Setting up deadlines
- Distribute the assignment through our Information Systems
- Collect assignments and reviews
- Make our own review of the assignments
- Keep track of the results (for the web development course, this meant maintaining a big spreadsheet with a dozen tabs and many formulas)
- Communicating the results to students (which can be automated using mailings, but this also requires technical skills)

Not all these steps are necessary depending on how peer review is configured and embedded in the course, but in our case, it was hard to skip and it became an additional burden.
We did receive some guidance from the platform's developer in a kickoff session, and through their extremely helpful and reactive support team, but we had to learn and try out several different options throughout the process.

The platform we used did provide options for data export, but that could only be done separately by downloading one spreadsheet for each assessment, and a large amount of work was necessary to reconstitute and keep track of the course progression, as well as to map these spreadsheets to our own student lists.

Similarly, keeping students updated about their progress was a lot of labour.
I used Microsoft Word's mailing feature and it turned out to be a bit more difficult than planned
(a quick example: the way "floating point" numbers are handled meant that a grade of `6.7` in Excel would show as `6.999999997` in Word).

I would like to emphasize a point here, in case our supplier is reading this blog post:
**This product is not worse than others. Very few technological solutions can be set up without generating extra work.**

## How to improve peer review?

Now, I draw lessons on improving peer reviewing in general, whether or not we use a technological platform for it.

### Feedback is a conversation with its object

One of the evaluation criteria for students in the Design Thinking course was their application of design theory.
Theory is something I've struggled with as a student (especially at a PhD level), but I've come to consider that the only way of properly teaching theory is by getting students to connect the dots between theory and practical applications.

And this works the same for feedback - if you want feedback to be an opportunity to reflect on one's work, you need to strengthen the link between the object and the content of feedback.
The platform we've used supports this process very well - when the object is a text document that can easily be annotated.

This is also how we use features such as Microsoft Word's comments (or Adobe Acrobat's comment, but they're less user-friendly), but there's no reason to limiting oneself to PDFs and DOCs outside of technical constraints.
There are many ways we can engage students with annotating things: taking photos with mobile phones to annotate objects and spaces, making scrapbooks, using interactive boards, etc.

This is possible for code, with tools such as GitHub's review system, but this is another technical skill that we would have had to teach students.

### Reviewing is a skill

Doing something and providing feedback on that thing is not the same thing.

This asymetry builds on our existing skills.
When I read my students' works and find their words unclear, this builds on years and years of reading texts in English.
But writing clearly and concisely is still hard for me, and writing a PhD thesis didn't encourage me to do so.

Somehow, the gap between writing and reviewing code tends to run the other way round, and it's generally harder to read someone else's code (even when it's your past self) than write code.

Writing code is the result of a trial-and-error process, whereby we adjust until we find something that works, but understanding whether and why a line of code is right or wrong requires way more experience.

Design critique, a form of review that is common in design schools, is also a skill that needs to be learned through practice.
Our students - depending on their previous studies - may not be used to this process of constructive critique,
and may lack the vocabulary to say "this is good work, because...".

Good peer reviewing requires us to provide students with scaffolding.
They need to learn the language and theory of design and how to articulate and apply them to design products.
As a consequence, giving a review is not just about offering something to a peer, it's also reflecting on your own practice as a designer.

But asking students to review their peers without building up the skills puts them in a situation of anxiety.
Worse than that, bad habits of years of competitive, grade-driven education creates a situation where students might feel like helping a peer and providing a "right" answer are at odds with each other.

### Courses need to adjust to peer-reviewing

Not only do we need to teach reviewing skills to adjust to peer reviewing, we also need to teach differently as a whole, and adapt the rest of our assessment strategy.

My naïve vision of the process of building peer assessment activities was that I would copy the "transparent" grading indicators from our syllabus, paste them in the back-office interface of our platform, et voilà!

But re-reading my own indicators shows an uncomfortable truth: they are vague, subjective, and I'm way too often relying on my intuition, rather than on detailed indicators, to decide what I consider good or not.

Writing indicators that are usable by students isn't easy, and there's always the risk of transforming them into a "grocery list" that constrains the content of student assignment.
But it's also an opportunity to reflect on the learning process and to embed these indicators on that reflection.

It is not necessarily a matter of making indicators entirely objective and unambiguous - in many courses, there is more than one way of achieving a good result -
but also shifting indicators from assessing the result to assessing the rigour of the process - because in the end, we are not interested in knowing if students made a good design product purely by chance.

Just to give example, if you want students to judge the number of participants in a research study you can:
- Give them a specific number (*you must interview 5 participants*), but this encourages a "grocery list" approach and provides no reflection.
- Tell them to refer to the course material, which leads them on a skim-reading treasure hunt through your Learning Content Management System but adds little value.
- Write something along the lines of *"participant numbers align with studies found in academic literature"* or *"participant numbers are derived through a power analysis"*, and then students get to reflect on where the numbers we require come from.

Good peer-reviewing allows students to understand why we do things the way we do, and helps them see our standards as more than arbitrary numbers.

## Improving EdTech products

Many of the issues and benefits of the technology we've used are transposable to other technologies.

### The local and global views

The first thing is that when we teach, it's always challenging - for us and for students - to go back and forth between the "local", micro view of the course of the day or learning activity of the moment, and the global, macro view of the whole course and its learning objectives.

Technology has a potential to bridge that gap, to help students connect the dots, and to provide the context that is needed to make sense of the content.

However, what I've seen is that technology also fragments the students' experience.
Interestingly, this fragmentation happens at multiple levels, and I don't see any perfect solution to it.
Both fully integrated platforms and modular approaches somehow manage to create pain for both students and lectures.

### Who should take on the labour that technology creates?

Even in courses where students have reported high satisfaction with our use of technology, setting it up required a lot of work from lecturers, from finding the right technology, to setting it up, to ensuring students can access it, and finally to showcase and backup the outcome of a given learning activity.

This technology burden is distributed across the board and falls partly on students, partly on lecturers, and partly on support staff, from IT to planning.

There are limited ways of shifting this labour around.
For example, in our communication platform, many (but not all, that would be too simple) channels, files, posts, events, can be accessed directly using a URL.
When we give these URLs to our students, we can cut down on the time they spend search for resources, but this gives us extra work, and not everyone knows how to do this.

There are other workarounds that we use everyday - for example emojis help me work around the fact that menus and tabs don't allow for any form of graphic design, and therefore are hard to distinguish for students.

We have structures for circulating these good practices, for learning how to use these tools, but very often our priority is not there, we are too busy with actually teaching, grading, and filling in paperwork.
Learning technologies and applying them is just too much work for many of us.

The situations are also far from ideal for institutional IT services.
At my previous employer, the newly appointed Chief Digital Officer audited the institution to discover huge amounts of "shadow IT", i.e. tools that staff had been procuring, configuring and using without going through the central IT channels.
This was seen as a risk (from a cybersecurity point of view, but also in terms of identifying systems that fall under privacy laws), as a source of costs (bypassing central procurement) and, in that particular case, as an obstacle to outsourcing (which may be a good or a bad thing depending on who you are).
But it can only happen this way because one-size-fits-all solutions don't exist, and because IT departments are rarely big enough to support the full range of solutions that all staff need.

### Novel tools help showcase educational innovation

There are easy ways to implement peer reviewing without all the bells and whistles of new technological platforms (e.g. you can ask students to circulate their Word documents), but a platform like the one we used has an additional benefit: it's a great ways of making the concept of peer reviewing visible within the organization.
My employer has set up pilot courses, organized a webinar, created a conversation space around the technological platform.
Such tools are great at structuring conversations and at showcasing lecturers' work.

In a world where most people associate "innovation" with technology, new tools are a great way to promote educational innovation - it can be hard to showcase and to visualize, but the technology artefacts that support it make easy press releases.

## Conclusion

In a few words, peer review is a fantastic tools that helps students to learn in a meaningful and reflective way.
But this requires rethinking our courses, and understanding how reviewing skills can be built up.

Peer review is not a simple solution that can be put into practice overnight, and it requires substantial reflection, collaboration within the lecturer team, and support on an institution level.
Having technology that supports it is great, but it won't solve any underlying issues, and might add bureaucratic burden.

---
layout: post
title: Why You Can’t Make the Single Responsibility Principle Work
---

Saying a class should "only have one reason to change" is a pretty terrible explanation for what the single responsibility principle is trying to achieve. I've encountered one-line single-variable classes that could be caused to change for a dozen different reasons. What counts as a reason? How granular do you go? I don't have good answers to these questions.

What I do know is that despite having a definition that I've never really been comfortable with, the way I was writing software before the SRP sucked. Huge monolithic classes that went on for hundreds of lines and required savant-like intelligence to understand were a regular part of my work day. Now I get to glide across the surface of a project, diving deep only when I need to. It's great, and frees up a lot of cognitive space.

There are still times where I can’t make it work though, and I think I’ve managed to distill these failures down to three big reasons.

### 1. Your process doesn't support it. ###

It's Friday afternoon. You're working your way through building something that's taken up the bulk of your week. It has to be finished by the close of business. You've produced a finely-polished piece of code. No rough edges, solves the problem elegantly, something that'll impress your peer reviewer and give you a feeling of smug satisfaction as the first beer of Friday night begins to take effect.

...and then you spot it.

There's an edge case that you've missed. Dumbass. Haven't you ever heard of an off-by-one error? Didn't you figure this stuff out in first year comp sci? Obviously not, because your hoity-toity "finely-polished" holier-than-thou solution doesn't work, you talentless hack.

Pause. Breathe. Repress the voice in the back of your head.

OK. We can fix this.

There are two options:

1. Change the architecture. Instead of using one class use two, both implementing the same interface.

2. Change the implementation. Slap another method on the bottom of the original class, and call it a day.

Ostensibly, yes, the first solution is the correct one. You'd be separating out responsibilities properly there, and had you anticipated this you'd have used this design in your original plans.

But there's a problem. Introducing new classes and changing your design like this will require sign off from the architecture team, and that will require a two-day turnaround. You don't have that kind of time. So now we're talking about missing a deadline (i.e. being bad at your job in a way that others will notice), or delivering a sloppy solution (i.e. also being bad at your job, but in a way that you'll probably get away with).

What happens next is left as an exercise for the reader.

### 2. Your tools don't support it. ###

Back in the dim dark ages before the enlightenment, [Joel Spolsky told us all to use the best tools money can buy][1], which for most of us meant comically enormous displays attached to the early 21<sup>st</sup> century version of a supercomputer. This was an awful lot of fun to do on the company credit card.

The thing is though, the software we use hasn't really caught up. Take a look at this:

<img src="/images/2015-06-27-visual-studio-screenshot.png" alt="Screenshot of Visual Studio displaying Hello World in C#." title="Screenshot of Visual Studio displaying Hello World in C#." />

That's Hello World in C#, on a (tiny by today's standards) 1280×1024 display. Notice the insane amount of white space? We should be doing something better with that. 

A byproduct of the SRP is that you end up creating considerably more files, each with significantly less in them. Working with multiple files displayed full screen ends up *increasing* your cognitive load, forcing you to store more in your short term memory every time you switch between them, which defeats the purpose of having a big display in the first place. Yes, you could split panes and shuffle things around manually, but that approach is slow and assumes you're prepared to pay a high setup cost to view a class that you might only spend a few seconds reading through.

What we really need is an IDE that capitalises on all that white space automatically. I'm picturing classes printed on a deck of cards here, where drilling into a class causes the previous one to slide down into any available white space, instead of vanishing into the background the way they do now. You'd be able to see more of your work at once, it would be harder to lose context, and you could travel back through the call stack just by glancing your eyes downward.

While we’re on the subject, when did we all decide that one class = one file? Are files even a sensible way of segregating classes any more? Many languages do support writing code with more than one class to a file, but few developers actually embrace that idea. When comparing versions of code where responsibilities have been moved around, it’s often difficult to understand how a change works when a piece of functionality has crossed the barrier from one file to another. Traditional deltas don’t really work well in these situations. I’m not really sure what the fix is here, but I've got this feeling stuck in the back of my head that we need tools which don’t force you to bind your architecture quite so closely to the filesystem.

### 3. You've taken it way too far. ###

It should not take an interface, three classes, two DLL's, and (so help me) *reflection* to load a record from a database.

Yes, I have encountered this. I had to sit quietly and think about my career choices after doing so.

It’s natural when falling in love with a new tool to embrace it in all its ways. My high school computer studies teacher called this the “Microsoft Publisher Effect”, where a friend of yours figures out how to work their desktop publishing software and you start receiving party invitations that use seven different borders and twelve different typefaces. People have a tendency to go a little nutty when they come across a tool that’s new and empowering, and I’ve definitely seen that happen with the SRP.

Interestingly, this seems to affect the experienced coders more that the newbies. Almost as if after years of monolithic classes the pendulum swings back too far, or maybe it’s just that the whippersnappers haven’t had the opportunity to build bad habits yet.

Whichever camp you find yourself in, it’s important to remember that the SRP is all about managing and minimising complexity. If your work becomes harder to understand, then you’re doing a disservice to the next person who has to work with it.

[1]: http://www.joelonsoftware.com/articles/fog0000000043.html

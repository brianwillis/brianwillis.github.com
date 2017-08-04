---
layout: post
title: CSS Grid Changes Everything
---

Here's a great talk by Morten Rand-Hendriksen from this year's WordCamp in Paris, entitled [CSS Grid Changes Everything][1]. The jokes are bit much, but stick with it because what he has to say is worth listening to.

I've lived through a few “generations” of CSS tech, from gif-spacers to tables to divs to flexbox. Every time we make one of these leaps forward, I feel like we’re rearranging our prejudices, enforcing new tradeoffs in an attempt to reinvent the wheel. I’ve been concerned about this lately, especially since [last week’s announcement by Adobe that Flash will be end-of-lifed][2]. I know Flash is a dumpster fire, but it enabled so much creativity back in the early days of the web, and a small part of me is sorry to see it go. More so than any other tool, Flash made me feel like I could turn my ideas into pixels. CSS has never felt like that, especially during the days of divs and floats. Instead CSS feels like one part rigid authoritarian and one part abusive spouse. I’m always one misstep away from having my defenceless HTML get scrambled for reasons that seem downright arbitrary.

My first impression of CSS grid is that it makes layout approximately as intuitive as flexbox, but in a more elegant way. There’s nothing inherently wrong with that, but I can tell you without even using it that there are some things it does badly. Want to stack one div atop another on the z-axis, creating a three dimensional effect with a sense of depth? Not going to happen. Want to have divs that change dimensions in response to mouse over events? Not without breaking your layout.

There’s definitely a particular set of use cases being optimised for here. Namely, static pages with little interactivity, little depth, and a rigid structure[^7]. This, more than anything, is what makes CSS grid feel like the anti-Flash.

It might just be time to concede that there’s no way to create a general purpose layout model that covers the whole scope of what we do on the web. I’m disappointed that’s where we’ve ended up, but I guess it’s better than gif-spacers.

[^7]: You know, like this one.

[1]: https://www.youtube.com/watch?v=txZq7Laz7_4
[2]: https://blogs.adobe.com/conversations/2017/07/adobe-flash-update.html

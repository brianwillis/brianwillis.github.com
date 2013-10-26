---
layout: post
title: One Man's Quest to Have His Dates Print Properly in Jekyll
---

I'm loving [Jekyll][1] as a blogging engine. I do not however, love how it formats dates. Outside of a databse table, a date should not look like this:

    2013-10-04T06:15:00Z
	
That's an ISO 8601 date in full Zulu form, in case you were interested.

While we're at it, dates had better not look like this:

    04/10/2013
	
&hellip;because that's simultaneously ugly and hard to use (quick! tell me which number is the day and which is the month).

This is almost right:

    04 October 2013
	
&hellip;because it has an unambiguous month, but that leading zero on the day reminds me of ledgers printed with dot matrix printers, and most irritating of all it's missing the suffix. Today isn't "the zero four" of October, it's "the 4th" and our dates should be written that way.

So we've established that we want this:

    4th October 2013

The more hasty readers amongst you will have leapt to the conclusion that you can pick the appropriate filters and have all that perfectly formatted goodness just spill out. But no! It's not that simple! Because Jekyll uses Liquid for filters, which uses strftime for formatting dates, and strftime doesn't have support for suffixes on dates. I know all this because I raised an issue with the nice people on the Liquid team asking them to add support for suffixes on dates, and they (very politely) said no.

So I was torn. I wasn't about to go spelunking through the code to strftime to figure out a way to do this. For one thing, it's written in C and languages without garbage collection are for braver men than me. Also after this many decades of active development I'm sure it's an incredibly complex and sophisticated beast. I've written a small amount of code to handle time zones and it made my brain hurt. I can't imagine working full time on a project where all you do is wrangle dates.

So I thought about it some more and came up with this:

    {% raw %}
    {% assign day = page.date | date: '%d' %}
    {% case day %}
      {% when '01', '21', '31' %}
        {% assign suffix = 'st' %}
      {% when '02', '22' %}
        {% assign suffix = 'nd' %}
      {% when '03', '23' %}
        {% assign suffix = 'rd' %}
      {% else %}
        {% assign suffix = 'th' %}
    {% endcase %}
    {{ page.date | date: '%e' }}{{ suffix }}{{ page.date | date: ' %B %Y' }}
    {% endraw %}

Update 26th October 2013: [Anatol Broder][2] was kind enough to send me a pull request with a much simpler solution, which you can see above.

Yes, I know. This solution is not elegant. It's a monstrous piece of code which aims to achieve something very simple. It works at the wrong level of abstraction, using Liquid filters when it should be using C. It's probably hopelessly inefficient. 

It does however, have the benefit of actually working. 

So if you want pretty dates in your Jekyll blog, copy and paste that into the appropriate place in your templates and you'll be good to go.

[1]: http://jekyllrb.com
[2]: http://penibelst.de/

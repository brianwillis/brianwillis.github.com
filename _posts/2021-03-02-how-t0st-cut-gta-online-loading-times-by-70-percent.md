---
layout: link
title: How t0st Cut GTA Online Loading Times by 70%
link: https://nee.lv/2021/02/28/How-I-cut-GTA-Online-loading-times-by-70/
---

The pseudonymous hacker t0st took it upon themselves to investigate what was taking so damn long during GTA's famously lengthy loading times, and the results are not good:

> It’s parsing something. Parsing what? Untangling the disassembly would take forever so I decided to dump some samples from the running process using x64dbg. Some debug-stepping later it turns out it’s… JSON! They’re parsing JSON. A whopping 10 megabytes worth of JSON with some 63k item entries.

It's fascinating to see the whole investigation laid out like this so plainly. I've never been involved in a disassembly project like this, so it's a lot of fun to look behind the curtain and see how the professionals do it. It's also remarkable that this whole thing was pulled off with no access to the original source code, but instead by using the obfusticated assembly that's shipped to customers.

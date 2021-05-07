---
layout: post
title: The University of Minnesota Got Themselves Banned From Contributing to the
  Linux Kernel

---
The short version of this story is that two researchers at the University of Minnesota thought it would be a fun idea to contribute "hypocrite commits" (i.e. bug fixes that deliberately include security holes) to the Linux kernel to see if the kernel maintainers would spot what they had done and reject the commits. They did this without the consent of the university's Institutional Review Board (which they have since gone on to obtain retroatively), and without permission from anyone on the kernel team.

Needless to say, the kernel maintaners didn't appreciate being treated like lab rats, and responded by banning the entire university from making contributions to the kernel, and – because why just burn the crops when you can salt the earth too – they then began the process of reverting all previous commits made by anyone with an @umn.edu email address.

It's worth noting that the researchers in question did prevent these hypocrite commits from making it into the production kernel, and at the core of their research is a concerning idea about the nature of security in Free and Open Source software projects. They have also appologised, though the sincerity seems questionable given the University of Minnesota's general unwillingness to take preventative actions to stop this happening again.

I've written before about the ambivalence toward ethics that exists in the software industry. It’s frustrating to see this sort of thing keep happening. Progress is not being made here, and it desperately needs to be. Needless to say, I’m with the kernel maintainers team on this one. There’s a time and a place for deception in scientific research, and this wasn’t one of those times.

For a more complete overview of the whole mess, this [article at The Verge by Monica Chin](https://www.theverge.com/2021/4/30/22410164/linux-kernel-university-of-minnesota-banned-open-source "How a university got itself banned from the Linux kernel") provides a good run-down.
---
title: "Week 1: Memory-based attacks"
date: 2015-01-01
author: "Mike Hicks"
draft: false
weight: 1
layout: single
build:
  list: never
---

We will begin our discussion of software security by understanding one of the oldest and pernicious attacks against software: the buffer overflow. We will see how buffer overflows are one kind of memory-based attack that low-level software (written in C and/or C++, primarily) is susceptible to, and we will consider other memory-based attacks as well. Your project for this week will be to construct a simple exploit of a buffer overflow, to see how it works.

If you have not done so, please watch the [preparatory material from Week 0](/course/software-security/).

## Learning Objectives

After the completion of this week's material (including the project, due at the end of next week), you will be able to:

- Understand the standard memory layout of running processes on the Intel x86 architecture
- Identify buffer overflows and related memory-based vulnerabilities in C programs, such as those based on format strings
- Construct a simple exploit of a buffer overflow
- Understand how exploits can inject remote code, and perform other security compromises

## Video Lectures

- [Low-Level Security: Introduction](https://youtu.be/3BqiTEwz1I0) (7:35)
- [Memory Layout](https://youtu.be/msUPyCtJPSw) (11:16)
- [Buffer Overflow](https://youtu.be/x8thu1AOsX8) (6:23)
- [Code Injection](https://youtu.be/nNBKed5C3AM) (6:15)
- [Other Memory Exploits](https://youtu.be/AaCySH-jD3g) (11:52)
- [Format String Vulnerabilities](https://youtu.be/ykMdLCURWFk) (6:43)

## Readings

### Required reading

The required reading this week is the following:

- [Common vulnerabilities guide for C programmers](https://security.web.cern.ch/security/recommendations/en/codetools/c.shtml). Take note of the unsafe C library functions listed here, and how they are the source of buffer overflow vulnerabilities. This list will be relevant for the project and this week's quiz.
- (Reference) [Memory layout](http://www.geeksforgeeks.org/memory-layout-of-c-program/). Explains a C program's memory layout, replicating the discussion in the second lecture.

### Supplemental readings

The following readings are optional: They are meant to supplement the material you are getting in the videos. Check them out if you are interested in learning more, or if you just want to see it all explained in a different way.

- [How buffer overflows work](http://arstechnica.com/security/2015/08/how-security-flaws-work-the-buffer-overflow/). This article does a great job of walking you through how stack smashing works, and also talks about some defenses against it, which are covered in more depth in next week's materials.
- (Reference/refresher) [PC Assembly Language](https://pacman128.github.io/pcasm/), by Paul Carter. This free book introduces x86 assembly, and should complement ideas seen in the lectures.
- [Smashing the Stack for Fun and Profit](http://insecure.org/stf/smashstack.html) - original article on the topic by Aleph One, in 1996
- [Exploiting Format String Vulnerabilities](https://cs155.stanford.edu/papers/formatstring-1.2.pdf) - report describing these format string attacks when they were first recognized; [more recent articles](https://medium.com/swlh/binary-exploitation-format-string-vulnerabilities-70edd501c5be) present alternative descriptions
- [Basic Integer Overflows](http://phrack.org/issues/60/10.html) - discussion of how overflowing integers can be a vector of attack

## Project

The [first project](../project1) is on exploiting buffer overflows; it is due in three weeks, just prior to the start of week 4. You will complete the work for the project on your own computer, and then take the [on-line assessment](/courses/software-security/assets/week1_BOF_quiz.docx) to show that you've done so.

## Quiz

The [quiz for this week](/course/software-security/assets/week1_quiz.docx) covers all of the material for this week, and the introductory material from last week, so do not forget to view that too.

## Notes (made in 2020) on Course Content

### Buffer Overflows and Other Violations of Memory Safety

Unfortunately, despite it now being 5 years since these lectures were recorded, **buffer overflow-style vulnerabilities are still a real problem**. In the slides we showed a graph from the national vulnerability database (NVD) that ended in 2014; the NVD site allows you to [graph the prevalence of CWE 119 (the one for buffer overflows)](https://nvd.nist.gov/vuln/search/statistics?form_type=Advanced&results_type=statistics&search_type=all&cwe_id=CWE-119) to the present day. We can see that the percentage and total of these vulnerabilities declined in 2019 and 2020, but they are still relatively frequent. And, they are quite dangerous, due to the potential for an attacker to remotely inject code. They can still appear in commonly-used applications, too; e.g., [CVE-2020-1594](https://nvd.nist.gov/vuln/detail/CVE-2020-1594) considers a dangerous buffer overflow vulnerability in Microsoft Excel.

The lectures and the project consider a 32-bit Intel architecture. Today, **64-bit architectures** are essentially universal, but the principles and problems still apply. For example, [**stack smashing is still possible**](https://thesquareplanet.com/blog/smashing-the-stack-21st-century/). That said, some defenses should be more effective on 64-bit machines than they were on 32-bit ones (see next week's lecture).

Format string attacks are about as common now as they were in 2015, while **use-after-free (UAF) vulnerabilities are ticking up**, which we can see from the [NVD graph of CWE 416](https://nvd.nist.gov/vuln/search/statistics?form_type=Advanced&results_type=statistics&search_type=all&cwe_id=CWE-416), which is just one CWE type of temporal safety-violating exploit. We mentioned UAF vulnerabilities briefly, but did not discuss how they are exploited. Using a type-safe (or memory-safe) language prevents them.

Why are these vulnerabilities still common? Because the **C and C++ programming languages are still popular**. The [IEEE Spectrum ranking places them at #3 and #4](https://spectrum.ieee.org/at-work/tech-careers/top-programming-language-2020) on its top-50 languages list. As cyber-physical systems have become more prevalent (as have "Internet of Things" or IOT apps), more legacy C/C++ code is being network connected, creating more memory-unsafe attack surface.

### Big news: Spectre and Meltdown!

In January 2018, the world was shocked by the revelation of the [Spectre and Meltdown bugs](https://spectreattack.com/), which are hardware vulnerabilities that were (or still are) present in many popular modern processors. Exploitation of these vulnerabilities would allow a program to steal data which that program should not be allowed to access (e.g., from the OS or another program running on the same machine).

Both attacks involve the use of [**side channels**](https://en.wikipedia.org/wiki/Side-channel_attack). Spectre observes side effects of [speculative execution](https://en.wikipedia.org/wiki/Speculative_execution), a common means of hiding memory latency and so speeding up execution in modern microprocessors. Meltdown specifically targets memory isolation hardware. The challenge is that many features that aim to optimize performance in the common case can be exploited to reveal information by systematically tilting the scales to the rare case. While mitigations to both processors and operating systems have now been deployed, this [vector of attack (side channels in hardware) is, unfortunately, not likely to go away soon](https://dl.acm.org/doi/abs/10.1145/3373376.3378453).

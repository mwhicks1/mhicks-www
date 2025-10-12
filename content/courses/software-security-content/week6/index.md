---
title: "Week 6: Penetration Testing and Fuzz Testing"
date: 2015-01-01
author: "Mike Hicks"
draft: false
weight: 6
layout: single
build:
  list: never
---

Last week we looked at how automated tools could be used to assist developers and testers in finding important security bugs. We focused in particular on *static analysis* and *symbolic execution* as technologies.

This week, we look at the broader practice of *penetration testing* of which tools using these technologies form some part, but other practices and techniques are of interest too. We will focus in particular on *fuzz testing*, a technique that attempts to find potentially security-relevant software failures.

## Learning Objectives

After the completion of this week's material, you will:

- Understand what penetration testing is and what it achieves
- Know the basics of several state-of-the-art penetration testing tools
- Understand fuzz testing techniques and how they compare
- Be aware of several state-of-the-art fuzz testing tools

## Video Lectures

- [Penetration Testing: Introduction](https://youtu.be/fQyaZ4SYxGk) (10:11)
- [Penetration Testing: Techniques and Tools](https://youtu.be/62PHZg-dgbg) (14:28)
- [Fuzz Testing: Techniques and Tools](https://youtu.be/eMYSDJRe3t0) (15:13)

### Break out: Interview with Eric Eames

In September 2014, Mike interviewed [Eric Eames](http://www.linkedin.com/pub/eric-eames/68/7b/590), at the time a Principal Security Consultant at FusionX. In this interview we discussed principles and practice of penetration testing. **The interview is *required*** from an assessment perspective -- some quiz material will be drawn from this interview's content.

[Mike Hicks interviews Eric Eames](https://youtu.be/AfPNqgRCowQ) (31:46). Highlights, indexed by time:

- start - Introduction and background
- 1:33 - Penetration testing: what is it?
- 5:04 - Tools and techniques used in penetration testing
- 9:43 - Common technical and human mistakes in engagements
- 15:05 - Defining an engagement; pen testers as outsiders or insiders
- 17:50 - Surprising discoveries
- 19:33 - What else, in addition to penetration testing can help ensure security
- 23:05 - Undergrad education -- what should we do?
- 26:39 - Prognosis for security, looking ahead

### Break out: Interview with Patrice Godefroid

In September 2014, Mike had the pleasure of interviewing [Patrice Godefroid](http://research.microsoft.com/en-us/um/people/pg/), who is a Partner Researcher at Microsoft Research. In this interview we discussed principles and practice of fuzz testing in general, and whitebox fuzz testing in particular, especially as it has come to be used within Microsoft. The interview is *optional* from an assessment perspective, but recommended -- there will no quiz questions on it per se, but it might help provide context about material from last week and this week.

[Mike Hicks interviews Patrice Godefroid](https://youtu.be/KPsFkClfNTA) (35:06). Highlights, indexed by time:

- start - Introduction and background
- 1:08 - The state of the art in automated vulnerability detection
- 5:50 - What drove your interest in working on model checking/analysis?
- 10:13 - Comparing different fuzz testing techniques
- 19:21 - The story of deployment of fuzzing at Microsoft for whitebox fuzzing
- 24:57 - Trends in the use of automated analysis tools
- 31:06 - Open problems in automated testing tool development

In 2020, [Patrice wrote a nice review article about fuzzing](https://www.microsoft.com/en-us/research/blog/a-brief-introduction-to-fuzzing-and-why-its-an-important-tool-for-developers/).

## Supplemental Links

Here we present links to supplemental material, in case you are interested to read it (none is required for assessment).

- [Ware report](http://www.rand.org/pubs/reports/R609-1/index2.html) - introduced the idea of penetration testing, as well as many other foundational ideas in systems security
- [CPT (pen testing) certification](http://www.iacertification.org/cpt_certified_penetration_tester.html) - establish your credentials as a pen tester
- [Defcon CTF contest](https://www.defcon.org/html/links/dc-ctf.html) - be the first to find vulnerabilities in other competitors' systems and patch them in your own

### Penetration testing tools

These tools are all free, or have free versions.

- [NMAP](http://nmap.org/) - "network mapper" scans network to find what's connected to it
- [Zap](https://github.com/zaproxy/zaproxy) - web proxy and automatic vulnerability scanner
- [Burp suite](http://portswigger.net/burp) - Several pen testing tools (some versions are free)
- [Metasploit](http://www.offensive-security.com/metasploit-unleashed/Main_Page) - customizable platform for developing, testing, and using exploit code.
- [Kali](http://www.kali.org/) - Linux distribution with pre-installed pen testing tools.

### Fuzz testing tools

Again, these tools are all free, or have free versions.

- [American Fuzzy Lop (AFL)](http://lcamtuf.coredump.cx/afl/) - popular, mutation-based, gray-box fuzzer
- [Libfuzzer](https://llvm.org/docs/LibFuzzer.html) - a fuzzer that is similar in spirit to AFL, developed at Google
- [OSSFuzz](https://google.github.io/oss-fuzz/) - a Google service for fuzzing open-source software projects; uses AFL, Libfuzzer, and Honggfuzz
- [Radamsa](https://gitlab.com/akihe/radamsa) - mutation-based black-box fuzzer
- [SPIKE](http://resources.infosecinstitute.com/intro-to-fuzzing/) - network fuzzing framework

## Quiz

The [quiz for this week](/course/software-security/assets/week6_quiz.docx) covers all of the material for this week.

## Project

There is no new project for this week. All outstanding projects and assessments are due by 8am ET the week after the course ends.

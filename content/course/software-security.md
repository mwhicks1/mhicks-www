---
title: "Software Security"
subtitle: "Online Course"
excerpt: "This course explores the foundations of software security, covering important software vulnerabilities and attacks that exploit them, such as buffer overflows, SQL injection, and session hijacking."
date: 2015-01-01
author: "Mike Hicks"
draft: false
show_post_thumbnail: true
show_author_byline: true
show_post_date: true
categories:
  - Security
  - Software Engineering
links:
- icon: youtube
  icon_pack: fab
  name: YouTube Channel
  url: https://www.youtube.com/channel/UCLnvPv3HJdKJ8CYnNcFLUgw
---

## Overview

This course, originally developed in late 2014 and early 2015 for [Coursera](https://coursera.org/) as part of the [University of Maryland](https://www.umd.edu/)'s four-course specialization on cybersecurity, explores the **foundations of software security**. The course is old enough now that I don't feel comfortable charging money for it, so it is here hosted for free. All of the videos are collected on a [Youtube channel, Software Security](https://www.youtube.com/channel/UCLnvPv3HJdKJ8CYnNcFLUgw).

The course considers important software vulnerabilities and attacks that exploit them, such as *buffer overflows*, *SQL injection*, and *session hijacking*. The course also considers defenses that prevent or mitigate these attacks, including *advanced testing* and *program analysis* techniques. We take a **build security in** mentality, considering techniques at each phase of the development cycle that can be used to strengthen the security of software systems.

A video overview of the course is presented in the following lectures. The first two present an overview of cybersecurity generally, and software security in particular. The last is an overview of the course content, and a description of the learner's expected background.

### Course Introduction Videos

- [Introducing computer security](https://youtu.be/UZwxufJ4ABQ) (6:17)
- [What is software security?](https://youtu.be/3GQUxWWa78c) (7:48)
- [Tour of the course and expected background](https://youtu.be/C_x5znlu8ro) (11:37)

## Topics

The content of the course is as follows, with one topic per week linked to the relevant material:

1. [**Low-level, memory-based attacks**](../software-security-content/week1), including stack smashing, format string attacks, stale memory access attacks, and return-oriented Programming (ROP)
2. [**Defenses against memory-based attacks**](../software-security-content/week2), including stack canaries, non-executable data (aka W+X or DEP), address space layout randomization (ASLR), memory-safety enforcement (e.g., SoftBound), control-flow Integrity (CFI)
3. [**Web security**](../software-security-content/week3), covering attacks like SQL injection, cross-site scripting (XSS), cross-site request forgery (CSRF), and session hijacking, and defenses that have in common the idea of input validation
4. [**Secure design**](../software-security-content/week4), covering ideas like threat modeling and security design principles, including organizing ideas like favor simplicity, trust with reluctance, and defend in depth; we present real-world examples of good and bad designs
5. [**Automated reasoning for code security**](../software-security-content/week5), presenting foundations and tradeoffs and using static taint analysis and whitebox fuzz testing as detailed examples
6. [**Penetration testing and fuzz testing**](../software-security-content/week6), presenting an overview of goals, techniques, and tools of the trade

We have put together a [glossary of terms](../software-security-content/glossary) that you might find useful while going through the course.

## Projects and Assessment

There is a quiz for each week's materials. Each quiz is stored in a Microsoft Word .docx file, which includes both the questions and the answer. (I didn't find time to split them apart.)

The course also has three projects:

1. [**Buffer overflow attacks**](../software-security-content/project1): The lab walks you through how a buffer overflow occurs, and how it can be exploited.
2. [**Web application security**](../software-security-content/project2): The lab asks you to find and exploit common vulnerabilities in web applications, like SQL injection and cross-site scripting
3. [**Static analysis for finding security bugs**](../software-security-content/project3): The lab will give you some experience using tools that aim to find security flaws automatically

To do the projects, you will need to install the [Virtual Box](https://www.virtualbox.org/) virtual machine management software (which is free) on your own computer. Projects will be in VM images running [Ubuntu Linux](http://www.ubuntu.com/); you will install these images and run them to do the projects. Detailed instructions for doing so are on the relevant project pages.

## Expected Background

Successful learners in this course typically have completed sophomore/junior-level undergraduate work in a technical field, have some **familiarity with programming**, ideally in C/C++ and one other "managed" program language (like Python or Java), and have prior exposure to algorithms. Students not familiar with these languages but with others can improve their skills through online web tutorials.

To test whether you have sufficient background to take the course, we recommend students take the **[qualifying quiz](/courses/software-security/assets/qualifying_quiz.docx)**. Students who score less than 70% on the quiz may have difficulty with the technical concepts assumed by the presentations. (Note that the quiz does not count toward your final grade.) Much of the quiz is about **C programming**; most of the code in the course will be presented in C. *For the first two weeks, this is critical*: the low-level errors and defenses against them are germane to C and low-level programming. Students comfortable in other languages may be able to learn the necessary C concepts on their own. One book I recommend is K.A. Reek's [Pointers on C](http://www.cs.rit.edu/~kar/pointers.on.c/). Several previous students of this course recommended the free book, [Learning C the Hard Way](https://learncodethehardway.org/c/).

## Note about course content, and call for corrections

This course was originally put together in late 2014 and early 2015. Fortunately (for learning, not for security!), much of the course's core content is still relevant as of early 2024: The examples and some details are now nearly 10 years old, but the same sorts of vulnerabilities, attacks, defenses, methodologies, and technologies are still relevant.

Some readings such as this one have some added discussion and links to newer versions, or generations, of tools and technologies, and/or writeups about them. The first such updates were made in 2020, and some of these links may be dead or out of date. **I welcome corrections and contributions!** If you come across a dead/wrong link or would like to suggest some commentary to add, please either **e-mail me** (mwh@cs.umd.edu) or better yet, make the suggested change and **submit a pull request on GitHub**, where these course materials are hosted.

### Errata

There are some small mistakes in the video lectures for the course, identified below.

#### Week 1

- ***Other memory exploits*** lecture: Slide 5 (titled Heap overflow variants) in the recorded lecture implies that all C++ objects have vtables, but in fact only those with virtual methods do. This point has been corrected in the (downloadable) PDF version of the slides.

#### Week 2

- ***Week 2 Intro slide implies ROP bypasses stack cookies and ASLR***. The discussion was meant as a transition to thinking about more sophisticated attacks, but then seemed to imply that ROP is more powerful than it is. ROP is a way to overcome defenses against jumping to particular libc functions, by reusing together code fragments rather than whole functions. It does not bypass stack cookies or ASLR.
- **There is a typo in the secure coding lecture, "Design vs Implementation."** Should be "consistent" instead of "consonant". This is fixed in the PDF slides.

#### Week 5

- **Taintedness as a lattice**. In the flow analysis lecture, at time 5:00, Mike mis-speaks and says that tainted is less than untainted, which is wrong; it's the other way around. Note that he corrects himself immediately afterwards, and the slides are correct.

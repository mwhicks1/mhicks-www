---
title: "Week 5: Automated Reasoning for Code Security"
date: 2015-01-01
author: "Mike Hicks"
draft: false
weight: 5
layout: single
build:
  list: never
---

Last week we looked at how security fits into the various activities of the development process. Up to this point we have generally looked at particular software flaws and bugs and how to avoid them through good design and implementation practices.

This week we will look at the testing and validation phases of software development, and in particular how automated reasoning tools can assist developers and testers in finding important security bugs. We will focus on two technologies: *static analysis* and *symbolic execution*.

## Learning Objectives

After the completion of this week's material, you will:

- Know what static analysis (SA) and symbolic execution (SE) are, how they compare, and why they are hard
- Understand the basics of each approach
- Understand how to improve the precision and scalability of each approach
- Be aware of several commercial and open-source SA and SE tools, and how they compare

## Video Lectures

This week we cover two code analysis technologies: static analysis, and symbolic execution. The latter is often used as the core of a penetration testing technology called *whitebox* fuzz testing; we will discuss other fuzz testing techniques next week.

### Static Analysis

- [Static Analysis: Introduction part 1](https://youtu.be/jg6CnPhfGkI) (5:10)
- [Static Analysis: Introduction part 2](https://youtu.be/qG93Ta4wFps) (8:12)
- [Flow Analysis](https://youtu.be/9JTCPYBXuTo) (8:44)
- [Flow Analysis: Adding Sensitivity](https://youtu.be/AOE8jVqfi4Q) (8:57)
- [Context Sensitive Analysis](https://youtu.be/ePDjC2HR-8U) (8:53)
- [Flow Analysis: Scaling it up to a Complete Language and Problem Set](https://youtu.be/m8EF5GO9w-o) (11:40)
- [Static Analysis: Challenges and Variations](https://youtu.be/cUStBAfK_Vg) (8:01)

### Symbolic Execution

- [Introducing Symbolic Execution](https://youtu.be/cjNTsCqbf5k) (10:52)
- [Symbolic Execution: A Little History](https://youtu.be/00L_qdYnTjY) (3:05)
- [Basic Symbolic Execution](https://youtu.be/Tfs-rAOR9Ig) (14:17)
- [Symbolic Execution as Search, and the Rise of Solvers](https://youtu.be/ZGuV9v6uUZc) (12:45)
- [Symbolic Execution Systems](https://youtu.be/lxKT2zb04y4) (8:26)

### Break out: Interview with Andy Chou

In August 2014, Mike had the pleasure of interviewing [Andy Chou](https://www.linkedin.com/pub/andy-chou/0/88/149). In 2003, Andy co-founded Coverity, a company that developed static analysis (and other) tools for finding software defects. [Coverity's products](https://www.synopsys.com/software-integrity.html) started from Andy's Ph.D. research at Stanford, and grew as the company grew; the organization was at 300 employees when it was [acquired by SynopSys in 2014](https://news.synopsys.com/2014-03-25-Synopsys-Completes-Coverity-Acquisition). In this interview we discussed principles and practice of static analysis, and the path towards making a practical tool that is now in wide use. Like last week, the interview is optional from an assessment perspective -- there will no quiz questions on it. We hope you find it interesting!

[Mike Hicks interviews Andy Chou](https://youtu.be/Lwug4AJY1FQ) (32:31). Highlights, indexed by time:

- start - Intro to static analysis, and different sorts of analysis
- 5:52 - Static analysis's place in secure development practice; tradeoffs
- 9:33 - Coverity Scan open source analysis: what it is, and its impact
- 11:07 - Static analysis challenges with particular languages
- 13:11 - Dynamic analysis: a complement to static analysis
- 17:35 - The process of choosing which analyses go into your tools
- 21:16 - How the market for static analysis has matured over the last 15 years
- 25:08 - More challenges for use and development of static analysis; looking ahead
- 29:19 - Free service Code Spotter; eating your own dogfood; closing thoughts

## Supplemental Links

Here is some additional reading material, if you are interested in learning more.

- [Scaling Static Analyses at Facebook](https://research.fb.com/publications/scaling-static-analyses-at-facebook/) (August 2019) - An article explaining how Facebook uses various kinds of static analysis heavily in their development process.
- [Lessons from Building Static Analysis Tools at Google](https://cacm.acm.org/magazines/2018/4/226371-lessons-from-building-static-analysis-tools-at-google/fulltext) (April 2018) - How Google is using static analysis for software development
- [A Few Billion Lines of Code Later: Using Static Analysis to Find Bugs in the Real World](http://cacm.acm.org/magazines/2010/2/69354-a-few-billion-lines-of-code-later/fulltext) (February 2010) - A classic article by the Coverity team on their experience writing and deploying a commercial static analysis tool
- [What is noninteference, and how do we enforce it?](http://www.pl-enthusiast.net/2015/03/03/noninterference/) - A blog entry Mike wrote about using static analysis to find information leaks; relates to the lecture material on implicit flows and tainting analysis
- [All You Ever Wanted to Know About Dynamic Taint Analysis and Forward Symbolic Execution (but might have been afraid to ask)](http://users.ece.cmu.edu/~ejschwar/bib/schwartz_2010_dynamic-abstract.html) - mathematical presentation of these analyses and their variations

Here are some links to static analysis and symbolic execution tools you might find interesting.

### Static analyzers

- [Clang Analyzer](http://clang-analyzer.llvm.org/) - A static analyzer built on the LLVM framework for C and C++ programs
- [Infer](https://fbinfer.com/) - A static analyzer for a variety of languages, including C, C++, Objective C, Java, and more.
- [Joern](http://www.mlsec.org/joern/) - A static analyzer for C and C++ programs
- [ErrorProne](https://errorprone.info/) - A static analyzer for Java (the moral successor to [FindBugs](http://findbugs.sourceforge.net/))

### Symbolic executors

- [KLEE](http://klee.github.io/) - A symbolic executor for LLVM bitcode (primarily supporting C and C++)
- [Java Symbolic Pathfinder](https://github.com/SymbolicPathFinder) - A symbolic executor for Java bytecode
- [Triton](https://triton.quarkslab.com/) - A symbolic execution library and framework for x86 executables
- [angr](https://angr.io/) - A combination symbolic executor and static analyzer for x86 executables

### SMT solvers

These solvers are used by various of the tools mentioned above.

- [Z3](https://github.com/Z3Prover/z3) - developed at Microsoft Research
- [CVC5](https://cvc5.github.io/) - developed at Stanford and the University of Iowa
- [Yices](http://yices.csl.sri.com/) - developed at SRI

## Quiz

The [quiz for this week](/course/software-security/assets/week5_quiz.docx) covers all of the material for this week.

## Project

For [this week's project](../project3) you will get your feet wet using a symbolic execution tool called KLEE, and comparing its performance to a black box fuzzing tool called radamsa (which we will learn more about next week). When you finish it, take the [on-line assessment](/courses/software-security/assets/week5_fuzz_quiz.docx), due in three weeks.

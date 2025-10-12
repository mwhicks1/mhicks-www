---
title: "Week 2: Defenses against low-level attacks"
date: 2015-01-01
author: "Mike Hicks"
draft: false
weight: 2
layout: single
build:
  list: never
---

We continue our discussion of low-level software security by understanding ways to defend against memory-based attacks like buffer overflows and format string attacks, introduced last week.

Defenses fall into two categories: (1) *automatic*, and (2) *manual* (based on disciplined programming styles). We will also look at a sophisticated attack, called *return oriented programming*, that aims to overcome some of the automatic defenses, as well as an experimental defense against it. In the end, the most sure defense against low level attacks is to program with a *memory-safe* (or better yet, a *type-safe*) programming language in the situations that's possible.

## Learning Objectives

After the completion of this week's material, you will be able to:

- Comprehend the meaning of the properties *memory safety*, and *type safety* and why programs enjoying these properties are immune from memory based attacks
- Understand several common automatic defenses against memory-based attacks, including *stack canaries, data execution protection (DEP)*, and *address space layout randomization (ASLR)*
- Understand how attacks based on *return-oriented programming (ROP)* work
- Understand the concept of *control-flow integrity (CFI)* and how it can defeat ROP-based attacks
- Understand a series of rules of thumb for programming in C so as to avoid memory-based attacks

## Video Lectures

- [Defenses Against Low-Level Attacks: Introduction](https://youtu.be/kL6T8KvKrk0) (2:58)
- [Memory Safety](https://youtu.be/A-SVeu0ZKI4) (16:56)
- [Type Safety](https://youtu.be/q_vB6WyP16o) (4:39)
- [Avoiding Exploitation](https://youtu.be/pObdbiQJpsk) (9:38)
- [Return-Oriented Programming](https://youtu.be/1dTF_Np9Lcw) (11:30)
- [Control-Flow Integrity](https://youtu.be/lrkNs5qo5Cw) (14:51)
- [Secure Coding](https://youtu.be/A-6nVxB3F5M) (18:29)

## Required Readings

The following two blog posts cover the topics of memory safety and type safety in somewhat greater depth:

- [What is memory safety?](http://www.pl-enthusiast.net/2014/07/21/memory-safety/)
- [What is type safety?](http://www.pl-enthusiast.net/2014/08/05/type-safety/)

## Quiz

The [quiz for this week](/course/software-security/assets/week2_quiz.docx) covers all of this week's material.

## Supplemental readings and links

The following readings are optional: Check them out if you are interested in learning more about material we've covered in lecture (many were explicitly linked in the lecture slides).

### Attacks and modern defenses, generally

- [On the effectiveness of Address Space Randomization](http://cseweb.ucsd.edu/~hovav/papers/sppgmb04.html), by Shacham, Page, Pfaff, Goh, Modadugu, and Boneh - showed how ASLR implementations on 32-bit systems can be defeated relatively easily
- [Smashing the Stack in 2011](http://paulmakowski.wordpress.com/2011/01/25/smashing-the-stack-in-2011/) - Paul Makowski revisits the [1996 Aleph One article](http://insecure.org/stf/smashstack.html) (on the supplemental reading list from last week), considering defenses at that time
- [Low-level software security by example](http://www.google.com/search?lr=&ie=UTF-8&oe=UTF-8&q=Low-Level+Software+Security+by+Example+Erlingsson+Younan+Piessens), by Erlingsson, Younan, Piessens, describes several low-level attacks and defenses.

### Return-oriented Programming (ROP)

- [Geometry of Innocent Flesh on the Bone: Return to libc without Function Calls (on the x86)](https://cseweb.ucsd.edu/~hovav/dist/geometry.pdf), by Hovav Shacham - introduced the idea, and the term, return oriented programming
- [Q: Exploit Hardening Made Easy](https://www.usenix.org/legacy/event/sec11/tech/full_papers/Schwartz.pdf), by Schwartz, Avgerinos, and Brumley - explains how to automatically generate ROP exploits
- [Blind ROP](http://www.scs.stanford.edu/brop/) - return-oriented programming without source code, automatically

### Control-flow integrity (CFI)

- [Control Flow Integrity](http://research.microsoft.com/pubs/64250/ccs05.pdf), by Abadi, Budiu, Erlingsson, and Ligatti - paper that introduced CFI
- [CFI in Clang/LLVM](https://clang.llvm.org/docs/ControlFlowIntegrity.html) - modern versions of the Clang/LLVM compiler will introduce various kinds of CFI support via compilation flags. [RedHat has a nice tutorial description of it](https://www.redhat.com/en/blog/fighting-exploits-control-flow-integrity-cfi-clang).
- [Microsoft's Control Flow Guard (CFG)](https://docs.microsoft.com/en-us/windows/win32/secbp/control-flow-guard) implements a CFI-style defense to Visual Studio projects; it is used when building the distributed executables of Internet Explorer and the Edge browser. Some discussion about CFG as compared to CFI is given in this [blog post](https://blog.trailofbits.com/2016/12/27/lets-talk-about-cfi-microsoft-edition/). Both [CFG and CFI are now available in Clang/LLVM](https://msrc-blog.microsoft.com/2020/08/17/control-flow-guard-for-clang-llvm-and-rust/).
- See also the paper *Low-level software security by example*, above.

### Secure coding

These are a few references linked in the lecture slides. We will cover secure coding and design in more depth during week 4.

- [SEI CERT C coding standard](https://wiki.sei.cmu.edu/confluence/display/c/SEI+CERT+C+Coding+Standard)
- [Secure Programming HOWTO](http://www.dwheeler.com/secure-programs/Secure-Programs-HOWTO/internals.html) by David Wheeler
- [Robust Programming](http://nob.cs.ucdavis.edu/bishop/secprog/robust.html) by Matt Bishop
- [DieHard project](http://plasma.cs.umass.edu/emery/diehard.html) - drop-in replacement for malloc that uses randomization to defend against heap-based exploits

## Project

There is **no new project** this week. Don't forget to complete [Project 1](../project1) on exploiting buffer overflows. Take the [project quiz](/courses/software-security/assets/week1_BOF_quiz.docx) when you have completed that project.

## Notes on Course Content

Writing in October 2020, a number of things have changed since 2015. Here are some of them.

### Enforcing Memory Safety

In the lecture, I wrote "coming soon, Intel MPX!" Since then, Intel MPX has come ... and gone. As summarized on the [Wikipedia MPX page](https://en.wikipedia.org/wiki/Intel_MPX), "In practice, there have been too many flaws discovered in the design for it to be useful, and support has been deprecated or removed from most compilers and operating systems." As a specific example, the gcc compiler used to provide a compiler extension that could take advantage of the MPX instructions, but that [support has now been deprecated](https://www.phoronix.com/scan.php?page=news_item&px=MPX-Removed-From-GCC9/). A key problem is that the extra hardware doesn't actually improve performance over software-only implementations, and in some cases performance could be worse!

The [**CHERI (Capability Hardware Enhanced RISC Instructions)**](https://www.cl.cam.ac.uk/research/security/ctsrd/cheri/) project is a more promising alternative. It defines a set of hardware extensions that provide capabilities, which can be used for enforcing memory safety. Initial designs targeted just spatial safety, but later work targeted temporal safety as well. Ongoing effort has focused on developing a [C compiler that targets CHERI](https://www.cl.cam.ac.uk/techreports/UCAM-CL-TR-947.pdf).

**In** late 2015 Microsoft began developing [**Checked C**](https://www.checkedc.org/), an extension to C that aims to ensure spatial safety (and, to a degree, type safety); it has since been forked and is run by an independent foundation. Checked C is implemented as an [extension to the open-source Clang/LLVM compiler](https://github.com/microsoft/checkedc-clang); the compiler inserts run-time checks when needed for enforcing safety. Recent work (e.g,. in a [partial refactor of the FreeBSD operating system to use Checked C](https://cs.rochester.edu/u/jzhou41/papers/freebsd_checkedc.pdf)) shows such checks to be relatively inexpensive, e.g., around a few percent. Of course, the compiler is still under development so things may change. I think very highly of this effort, so I am working with the Checked C team both to design the language and to develop tools to automatically migrate legacy C code to Checked C.

Another mature effort to **ensure partial memory safety is** [**Address Sanitizer (ASAN)**](https://github.com/google/sanitizers/wiki/AddressSanitizer), but ASAN-ized code is much slower (e.g., 2x slowdown) with checks inserted, so it would not normally be used in production.

### Enforcing Type Safety

In the lecture, I said that modern languages are emerging that aim to ensure type safety while also providing good performance. I mentioned [Go](https://golang.org/), [Rust](https://www.rust-lang.org/), and [Swift](https://developer.apple.com/swift/), in particular. Since 2015, all three of these languages have become better developed and more popular. Indeed, I would say that **Rust has emerged as a strong contender to be the "go to" safe systems programming language**. Rust's notion of type safety implies not only memory safety, but also freedom from [data races](https://blog.regehr.org/archives/490). These owe to defects in concurrent programs, are difficult to find and debug, and can have security implications; Rust's type system ensures their absence. Developers love these benefits among others: According to Stack Overflow's annual poll of developers, [Rust has been the year's "most loved" language for five years in row](https://stackoverflow.blog/2020/06/05/why-the-developers-who-use-rust-love-it-so-much/)!

### Avoiding Exploitation

In the lecture, I talked about several defenses that aim to make memory safety bugs harder to exploit, e.g., address space layout randomization (ASLR) and stack canaries. These defenses are still relevant today, but have evolved while facing new threats.

Using the Clang/LLVM compiler, stack canaries are enabled with the -fstack-protector flag. It also provides another defense called [*shadow stacks*](https://en.wikipedia.org/wiki/Shadow_stack)**, which has the same goal as stack canaries but is more dependable**, while still being low overhead. The basic idea is to separate critical metadata, notably return addresses, into a separate stack so that it will not be overwritten by a stack-based buffer overflow. The [Clang/LLVM compiler's -fsanitize=safe-stack flag enables shadow stacks](https://clang.llvm.org/docs/SafeStack.html) (called "safe stacks"); the gcc compiler supports them as well.

ASLR is widely deployed, e.g., on [Linux](https://www.networkworld.com/article/3331199/what-does-aslr-do-for-linux.html), MacOS, IOS, and [Windows](https://techcommunity.microsoft.com/t5/windows-10-security/turn-on-mandatory-aslr-in-windows-security/m-p/1186989) (though for the last it is turned off by default). ASLR is effective when the base addresses of randomized process memory segments are hard to guess. A common part of an attack against an ASLR-protected system is to exploit a bug that leaks a base address. Software and hardware side channels, e.g., due to caches, are a [vector for such leaks](http://www.minemu.org/papers/anc_ndss17.pdf). Indeed, as mentioned last week, the [Spectre and Meltdown bugs](https://spectreattack.com/) have shown that hardware-based side channels are a significant threat. Moreover, recent work has shown that [information disclosure is not always needed to defeat ASLR](https://download.vusec.net/papers/pirop_eurosp18.pdf). As such, it remains to be seen whether ASLR remains an effective defense in the future.

### Control Flow Integrity (CFI)

In 2015, CFI was being seriously explored as a viable defense. Full CFI, as originally proposed, added too much performance overhead, so researchers were exploring less expensive alternatives with less protection. I updated the links in the supplemental material, above, to discuss CFI a bit more.

The [**Clang/LLVM compiler supports CFI**](https://clang.llvm.org/docs/ControlFlowIntegrity.html) **in various forms**; [Trail of Bits has written a nice tutorial about it](https://blog.trailofbits.com/2016/10/17/lets-talk-about-cfi-clang-edition/). One variant is [forward-edge only CFI](https://www.usenix.org/conference/usenixsecurity14/technical-sessions/presentation/tice) (FO-CFI), which does not protect returns via addresses on the stack, but does protect calls via function pointers and virtual method tables. (Shadow stacks could be enabled, at low cost, to provide protection for return addresses.) For FO-CFI, "a performance overhead of less than 1% has been measured by running the Dromaeo benchmark suite against an instrumented version of the Chromium web browser." [Mathias Payer also did a detailed study of Clang/LLVM CFI](https://nebelwelt.net/blog/20181226-CFIeval.html), and found per-dispatch overheads at around 20% (but forward-edge dispatches are relatively infrequent operations in the code). The [Chrome team planned to include Clang's CFI protections in the browser](https://www.chromium.org/developers/testing/control-flow-integrity). (Note that [clang is used to build Chrome for Windows](https://blog.llvm.org/2018/03/clang-is-now-used-to-build-chrome-for.html), too.)

The flip side of the lowered overhead is the lowered protection. How low is too low? [Muntean et al developed an empirical framework for evaluating the different levels of protection offered by CFI](https://arxiv.org/pdf/1910.01485.pdf) which aims to determine the post-CFI-protected attack surface on particular applications; for example, it will determine the number of possible allowed targets per callsite, for each CFI policy (fewer is better). These surfaces can then be compared to understand a ranking of the offered defense, compared to its overhead.

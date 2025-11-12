---
## Configure page content in wide column
title: "" # leave blank to exclude
number_featured: 0 # pulling from mainSections in config.toml
use_featured: false # if false, use most recent by date
number_categories: 0 # set to zero to exclude
show_intro: false
show_outro: false
---

<img src="/img/Michael-Hicks_08.26.25.jpg" alt="Mike Hicks" style="max-width: 300px; float: right; margin-left: 20px; margin-bottom: 20px; border-radius: 8px;">

I am the Cecilia Fitler Moore [Professor in the Computer and Information Science Department](https://directory.seas.upenn.edu/computer-and-information-science/) and the Director of the Schlein Center for Cybersecurity at the [University of Pennsylvania](https://directory.seas.upenn.edu/computer-and-information-science/), and I am an [Amazon Scholar](https://www.amazon.science/scholars) and an [ACM Fellow](https://awards.acm.org/fellows/award-recipients).

From 2022-2025 I was a Senior Principal Scientist at [Amazon Web Services](https://aws.amazon.com/). I am also a Professor Emeritus (active 2002-2022) of the [Computer Science Department](http://www.cs.umd.edu/) and [UMIACS](http://www.umiacs.umd.edu) at the [University of Maryland, College Park](http://www.umd.edu/). 

## [Research](/research/)

My research focuses on improving software availability, reliability, and security through programming languages and software engineering techniques. 

And: I'm looking to hire new PhD students in 2026!

### Ongoing projects

I am currently working in two main directions. First, I am working on ways to efficiently build high-quality and secure software, with a particular focus on **Fuzz testing and property-based testing**. These techniques are both highliy usable and effective at spotting bugs and improving software quality. I am currently exploring how GenAI-driven coding can improve, and be improved by, these techniques. In my first couple of years at Amazon, I worked on property-based testing for the [Cedar](https://cedarpolicy.com) authorization language (more below), and when I was at UMD, I developed methodologies for [evaluating fuzz testers](http://www.pl-enthusiast.net/2018/08/23/evaluating-empirical-evaluations-for-fuzz-testing/), [benchmarking them](http://mhicks.me/papers/zhang22fixreverter.html), and [combining them with property-based testing](/papers/lampropoulos19fuzzchick.html).

The second broad area I am exploring is [**Cyber Public Health**](https://cybergreen.net/cyber-public-health/), which is an effort to take lessons from public health practices and institutions and apply them to improving the practice of cybersecurity. As we have been reading about in my [class](/courses/CIS-7000-Fall2025/), it can be difficult to connect cybersecurity innovations to their impact because we lack data connecting them to observed outcomes. I am starting to talk with Penn colleagues in business, law, policy, and health about how we can change this state of affairs. A key concern in all this is the human user, so I am also engaging with experts in the [Usable Security and Privacy](https://www.usenix.org/conferences/byname/884) community.

### Other recent work

Here is an overview of other recent projects.

- **[Cedar](https://cedarpolicy.com)** is a domain-specific language for writing authorization policies. I co-led (with [Emina Torlak](https://emina.github.io/)) its development while at AWS. It is the core of [Amazon Verified Permissions](https://aws.amazon.com/verified-permissions/) and is now in use by big tech companies like MongoDB and CloudFlare, and startups like [StrongDM](https://www.strongdm.com/). You can read more about Cedar in its [scientific paper](https://dl.acm.org/doi/pdf/10.1145/3649835), and check out the [code on GitHub](https://github.com/cedar-policy)
- **Verification-guided development** (VGD) is an [approach to developing secure, high-assurance software](https://www.amazon.science/publications/how-we-built-cedar-a-verification-guided-approach), combining formal proof and property-based testing. We used this approach for Cedar, and all of [our proofs and tests are open-source](https://github.com/cedar-policy/cedar-spec). I speak about VGD as part of [this talk at the DARPA Resilience meeting](https://www.youtube.com/watch?v=ZuPGZ3W-ITA&list=PL6wMum5UsYvbc1h-qcpfmT6aXQsW7LItz&index=6).
- **Secure programming**: I helped develop [Checked C](https://www.checkedc.org/), a memory-safe extension to C for legacy code migration; and conceived and conducted [Build it, Break it, Fix it](https://builditbreakit.org) contests to evaluate secure development practices; and working with safe languages like Rust. (We might try to bring these back, with an eye toward AI-driven coding!)
- **Quantum computation**: I led efforts to create verified compiler stacks for quantum programs, including [VOQC](https://github.com/inQWIRE/pyvoqc), and develop robust quantum programs for near-term devices.

Other projects include dynamic software updating ([Kitsune](https://github.com/kitsune-dsu), [Rubah](https://www.luispina.me/projects/rubah.html)), information flow control (LWeb, Prob), languages for expressing secure multiparty computations ([Wysteria](https://bitbucket.org/aseemr/wysteria/wiki/Home), [Symphony](https://github.com/plum-umd/symphony-lang)) as well as authenticated data structures and compiler-optimized oblivious RAM (Lobliv), incremental computation (Adapton), type systems for Ruby (Diamondback Ruby), symbolic execution (Otter), data race detection ([LockSmith](https://www.cs.umd.edu/projects/PL/locksmith/)), and the memory-safe C dialect [Cyclone](http://cyclone.thelanguage.org/).

Here is my current [vita](cv.pdf). My [research](/research/) page lists publications, my resource group, and activities.

## [Teaching](/courses/)

- **Current**: [Empirical Security & Privacy, for Humans](/courses/CIS-7000-Fall2025/) (UPenn CIS 7000, Fall 2025)
- **Recent (UMD)**: Organization of Programming Languages (CMSC 330, multiple semesters); Program Analysis and Understanding (CMSC 631, multiple semesters); [Software Security](https://www.coursera.org/learn/software-security/) MOOC (now free, originally on Coursera)
- **Past (UMD)**: [Build it, Break it, Fix it](https://www.cs.umd.edu/class/winter2020/cmsc388N/) contest (CMSC 388N); Mechanized Proof and Verified Software (CMSC 838G); Cybersecurity Lab (CMSC 498L); Operating Systems (CMSC 412)

## [Service, professional activities](/research/professional-activities/)

- **Editor in Chief**: [Proceedings of the ACM on Programming Languages (PACMPL)](https://dl.acm.org/journal/pacmpl) (2023-2028); Associate Editor for TOPLAS (2012-2016)
- **[ACM SIGPLAN](https://sigplan.org/)**: Chair (2015-2018), Past Chair (2018-2021); POPL Steering Committee Chair (2018-2021); Founder and Editor of [PL Perspectives blog](https://blog.sigplan.org/) (2019-2021)
- **Recent program committees**: CSF, OOPSLA, S&P, POPL, PLDI (Area Chair), CCS (Area Chair), ASPLOS, SecDev, and many others
- **Past roles**: Co-PC Chair for CSF 2015-2016, SecDev 2016; inaugural Director of [Maryland Cybersecurity Center](https://cyber.umd.edu/) (2011-2013); CTO of startup Correct Computation, Inc (2018-2021); founder and director of [**PLUM**, the lab for *Programming Languages research at the University of Maryland*](https://plum-umd.github.io/).
---
title: "Fuzz Testing & Property-Based Testing"
subtitle: "Efficient, scalable techniques for building high-quality secure software"
excerpt: "Research on fuzzing, property-based testing, and their combination to improve software quality and security."
categories:
  - Research
  - Testing
weight: 3
---

## Overview

Fuzz testing (fuzzing) and property-based testing are powerful techniques for automatically finding bugs and security vulnerabilities in software. My research focuses on making these techniques more effective, easier to use, and applicable to a wider range of software systems. A key area of current interest is how GenAI-driven coding can improve, and be improved by, these testing techniques.

These approaches are particularly valuable because they:
- Automatically generate test inputs to explore program behavior
- Scale to large, complex software systems
- Find bugs that traditional testing misses
- Integrate well into development workflows

While at Amazon, I worked extensively on **property-based testing for the [Cedar](https://cedarpolicy.com) authorization language**. This work demonstrates how property-based testing can provide strong assurance for security-critical systems when combined with formal verification as part of *verification-guided development* (VGD).

## Current Projects

### GenAI and Testing
I am exploring how GenAI-driven coding can be enhanced by fuzz testing and property-based testing, and vice versa. This includes using LLMs to generate better test oracles, improve fuzzer performance, and automatically repair bugs found during testing. In my work at Amazon, I've helped [integrate property-based testing](https://kiro.dev/blog/property-based-testing/) into the [Kiro](https://kiro.dev/) specification-driven coding assistant.

### Property-based Testing for Lean
[QuickChick](https://softwarefoundations.cis.upenn.edu/qc-current/index.html) is a library for property-based testing for the Rocq proof assistant. With QuickChick you can attempt to *falsify* a theorem first, before you attempt to prove it. I have been working with Amazon and academic colleagues to develop a property-based testing library for Lean, starting from the [Plausible](https://reservoir.lean-lang.org/@leanprover-community/plausible) library, and working toward (and surpassing) parity with QuickChick.

## Key Publications

### Evaluating and Improving Fuzzers

- **[Evaluating Fuzz Testing](/papers/klees2018fuzzeval.html)** (CCS 2018)
  Developed methodologies for rigorously evaluating fuzzer effectiveness. Shows that common evaluation practices can be misleading and proposes better statistical methods.
  [Blog post: Evaluating Empirical Evaluations for Fuzz Testing](http://www.pl-enthusiast.net/2018/08/23/evaluating-empirical-evaluations-for-fuzz-testing/)

- **[FixReverter: A Realistic Bug Injection Methodology for Benchmarking Fuzz Testing](/papers/zhang22fixreverter.html)** (USENIX Security 2022)
  Addresses the challenge of benchmarking fuzzers by creating bug benchmarks based on historical bug patterns that emerge when reverting bugfixes. **Distinguished Paper Award**.

### Property-based Testing

- **[Coverage Guided, Property Based Testing](/papers/lampropoulos19fuzzchick.html)** (OOPSLA 2019)
  Extends property-based testing in QuickChick with coverage guidance to explore programs more thoroughly, combining the strengths of fuzzing and property-based testing.

- **[How We Built Cedar: A Verification-Guided Approach](/papers/disselkoen24vgd.html)** (ESEC/FSE 2024)
  Describes how property-based testing and differential random testing were used alongside formal verification to build Cedar, demonstrating the practical application of these techniques to security-critical systems.
---
title: "Beyond Penetrate-and-Patch"
subtitle: "Why AI's Greatest Security Contribution Will Be Secure-by-Design"
excerpt: "Anthropic's Claude Mythos Preview and Mozilla's record patch batch suggest AI bug-finding could finally tip software security toward defenders. But penetrate-and-patch is the wrong end state. AI's lasting contribution to security will come from making whole classes of vulnerability impossible to express in the first place."
date: 2026-05-05
author: "Mike Hicks and [Steve Lipner](https://www.stevelipner.org/) (SAFECode)"
draft: false
layout: single
tags:
  - security
  - ai
  - secure-by-design
  - formal-methods
  - memory-safety
categories:
  - software-security
  - software-engineering
---

In April, Anthropic announced Claude Mythos Preview alongside Project Glasswing, reporting that the model had identified thousands of high-severity zero-day vulnerabilities across every major operating system and web browser, including a 27-year-old bug in OpenBSD.[^mythos] Days later, Mozilla announced patches for 271 vulnerabilities Mythos had surfaced in Firefox — a roughly twelve-fold leap over the 22 bugs Opus 4.6 had found only weeks earlier. Mozilla's CTO declared, in a blog post titled "The zero-days are numbered," that defenders finally had a chance to win decisively.[^zerodays] Anthropic, in its own announcement, argued that once the security landscape reaches a new equilibrium, powerful language models will benefit defenders more than attackers.

If you take both posts at face value, an end state is in view: AI systems become so much better at finding bugs than the humans who wrote them that the residual exploitable surface eventually shrinks to zero. The asymmetry that has favored attackers for decades — they need to find only one exploitable bug while defenders must find and fix them all[^anderson] — becomes irrelevant because defenders *can* actually find and fix all of the bugs.

While we are optimistic that AI can ultimately favor the defense, we don't believe penetrate-and-patch — even with a superhuman bug-finder — is how defenders win. AI is a critical aid for patching the vulnerable code we have *today*, but defenders win in the *long term* with AI that is skilled at *security by design*: building code in which broad classes of vulnerability cannot be expressed, rather than auditing unsafe code until it appears clean.

## I. Three Reasons for Skepticism

### The narrow shape of the wins so far

Mythos's clearest wins so far are memory corruption vulnerabilities in C and C++ codebases. These matter — they account for a meaningful fraction of critical CVEs — but they are one slice of the CWE Top 25, alongside logic flaws, authorization bugs, business-logic errors, broken cryptographic protocols, and deserialization-based injection variants. Penetrate-and-patch as an end-state strategy is unforgiving about that gap. The defender has to find *all* the bugs, or close enough that the residual surface is too thin to attack; the attacker needs one. A bug-finder with 90% recall against a 1,000-bug codebase still leaves 100 bugs in play.

Memory corruption is the class where autonomous discovery has come closest to that bar, and the reason is instrumentation. AddressSanitizer and its descendants give an agent a definitive oracle: run the candidate exploit, see whether the target crashes. Even here, no one claims completeness; bugs that evade ASan's instrumentation, or that require specific environmental conditions to trigger, remain. For many other CWE classes, definitive oracles do not exist. Confirming a logic flaw or an authorization bug requires contextual knowledge of intent that is hard to recover from code alone, by any reviewer, human or model.

### The same models that find bugs are writing them — and the gap is architectural

Mythos's results are on code that humans wrote. The trajectory of software development today suggests that most code in the not-too-distant future will be primarily AI-authored. A natural hope is that this helps. Models good enough to find subtle bugs across decades-old codebases ought to be good at not introducing those bugs in the first place.

The hope does not hold, at least not yet. Veracode's 2025 GenAI Code Security Report found that 45% of AI-generated code samples failed security tests and introduced OWASP Top 10 security vulnerabilities into the code.[^veracode] Recent experiments show this puzzling mismatch exists *within a single model*:[^sandoval] an LLM that correctly flags `sprintf` as dangerous in 90% of code-review trials proceeds to generate `sprintf` in 93% of code-generation trials. The model knows. It generates the bug anyway.

The asymmetry is between review mode and generation mode of the same model weights, and it is architectural rather than contingent on training data — it reflects how transformers manage competing objectives during generation. Sandoval et al. propose some mechanisms that can improve the situation but do not offer a wholesale fix.

### The economics push the wrong way

As AI agents make code cheaper and faster to produce, the attack surface grows in step. Why? Most organizations have a backlog of projects that were previously out of budget but now fit within it thanks to AI. More projects means more code, and thus more work for AI-driven audits. If AI auditors are 10x better than humans at finding bugs, but AI coders have generated 10x more code, we have not fundamentally changed the mismatch that exists today.

This reality reflects that AI usage is a zero-sum game. As organizations choose how to use AI capabilities within their allotted budgets, they must decide whether to use AI to build products (writing code) or defend products they already have (hunting for vulnerabilities in that code). The market incentives outlined by Anderson[^anderson] decades ago have not changed: There is still incentive to be a first mover and to favor usability over security, and still a risk of a tragedy of the commons. Market incentives will drive technology development, not technology security.

Large vendors with enormous user bases — OS maintainers, browser shippers, payment processors — may favor security more than before. Smaller organizations, startups, and the long tail of open-source maintainers face a different calculus, and the economics will tilt them toward shipping unaudited code from cheaper models. Anthropic has funded Alpha-Omega, OpenSSF, and the Apache Foundation through Glasswing — a deliberate program, but a small one against a long tail that grows in step with model capability. The scale problem is already visible inside the consortium itself: by Anthropic's own count, fewer than 1% of the vulnerabilities Mythos identified had been patched as of the announcement.[^mythos] Even DARPA's AIxCC, which paired automated discovery with automated patching, produced narrow point fixes rather than structural rewrites. Discovery is outrunning remediation in the best-resourced defender setting we have.

## II. The Path We Should Be On: Secure by Design

The deeper observation behind the limits of penetrate-and-patch is that although code security results in part from an understanding of vulnerabilities, *code security is not the same as finding vulnerabilities in code*. If we want secure software at scale, we need AI that *produces* secure code by construction — not code that is then audited until it appears clean.

### Memory- and type-safe languages

Rust, Go, Java, and other memory-safe languages eliminate entire vulnerability classes by construction. Rust has unsafe blocks, but in practice they are small, audited, and often abstracted behind safe APIs. The decades-long hope that we could simply train developers to write C++ correctly has been falsified by every shipped browser, kernel, and runtime that has ever existed. Mozilla's own footnote in the "zero-days are numbered" post is telling: their progress depends not just on Mythos but on years of Rust adoption, sandboxing, and process isolation. Other Glasswing partners are hedging the same way — consortium reporting describes a shift toward memory-safe languages and AI-assisted review *before* code reaches production. The defenders with the earliest access to Mythos do not appear to be betting on it as a terminal strategy either.

Memory safety is necessary but not sufficient. Type safety with secure API design extends the same logic further. Google's Secure-by-Design effort has shown that a language's type system can be turned into a correct-by-construction taint analysis, nearly eliminating SQL injection and cross-site scripting in Go and TypeScript codebases.[^google-sbd] The general principle: a programming discipline that precludes broad avenues of attack is structurally stronger than any pipeline that detects them after the fact.

The historic objection — that Rust's borrow checker and type-driven APIs demand expensive developer retraining — is less compelling under agentic coding. Models already produce borrow-checker-satisfying Rust, including in safety-critical contexts. That retraining cost is exactly the cost frontier coding agents are best positioned to absorb. We should be pushing AI agents *toward* memory- and type-safe targets, not relying on them to clean up the consequences of using unsafe ones.

### Formal methods as the next horizon

Beyond type safety lies formal verification of richer security properties: mathematical proof, mechanically checked, that code meets a specification. This is not the toy-example domain it was a generation ago. Microsoft Research's Project Everest delivered a formally verified, deployable HTTPS stack — including a TLS 1.3 implementation, the HACL\* and EverCrypt cryptographic libraries, and Vale-verified assembly — interoperating with mainstream browsers and powering Microsoft's QUIC implementation.[^everest] AWS rebuilt its authorization engine, which fields a billion requests per second, as a Dafny-verified system that shipped in 2024 with both higher assurance and a threefold performance improvement over the legacy Java code it replaced.[^aws-iam] These are production systems at internet scale, not academic exercises. What has held verification back most recently is not the technology but the cost: for every line of verified code, a team of specialists must write specifications and proofs.

AI is collapsing that cost. The recent VeriCoding benchmark shows verification success rates in Dafny rising from 68% to 96% over a single year of model improvement, with Rust/Verus and Lean trailing but climbing.[^vericoding] Most strikingly, an AI agent recently converted zlib — the compression library embedded in nearly every device on earth — to Lean and proved a decompress-of-compress roundtrip theorem with minimal human guidance, using a general-purpose model with no specialized training for theorem proving.[^zlib] What once required research teams is now within reach of a single engineer guiding an agent. A wholesale switch to formal verification is not yet practical, to be sure, but the trajectory matters: every additional capability gain in agentic coding is also a capability gain in agentic verification. Penetrate-and-patch competes with code generation for compute; formal methods compose with it.

## III. What an Honest End State Looks Like

Penetrate-and-patch with AI is real, and useful especially for the code we have today. The Mythos numbers are extraordinary, and Mozilla's response is the right one for a large existing codebase: take the gift, integrate the tool into the product workflow, ship the patches, then keep going. But expecting penetrate-and-patch to reach a "defenders win" destination for *all* code — including the code being written tomorrow — leads to the wrong strategic course. The economics will not sustain a permanent compute race between attacker AIs and defender AIs across the long tail of software. The model that finds bugs is, mechanistically, the same model that writes them. And the bugs Mythos finds most reliably are exactly the bugs that secure-by-construction disciplines would prevent in the first place. There are encouraging signs that the industry is beginning to internalize this: Microsoft has stated they are integrating Mythos into their Security Development Lifecycle, and (independent of Glasswing) AWS has adopted an AI-based threat modeling tool for security design analysis. But much of the public comment around Mythos still centers on discovery and response capacity rather than secure-by-construction development.

The asymmetric advantage we should be pursuing is not only a better bug-finder; it is a programming discipline that makes broad classes of bugs impossible to express. Memory safety, type-driven secure APIs, and formal verification are the validation backstops. Their historical cost — developer retraining and unfamiliar idioms — is exactly the cost that frontier coding agents are uniquely positioned to absorb. As they do, vulnerability discovery will be important — it will mop up an ever-shrinking residual rather than running on a treadmill. The right use of AI in security is not just to find vulnerabilities in the unsafe code we already have; it is to make new unsafe code unnecessary in the first place.

## References

[^mythos]: Anthropic Frontier Red Team, "Claude Mythos Preview," April 2026, [https://red.anthropic.com/2026/mythos-preview/](https://red.anthropic.com/2026/mythos-preview/). See also Anthropic, "Project Glasswing," [https://www.anthropic.com/glasswing](https://www.anthropic.com/glasswing).

[^zerodays]: Bobby Holley, "The zero-days are numbered," Mozilla Blog, April 2026, [https://blog.mozilla.org/en/privacy-security/ai-security-zero-day-vulnerabilities/](https://blog.mozilla.org/en/privacy-security/ai-security-zero-day-vulnerabilities/).

[^anderson]: Ross Anderson, "Why Information Security is Hard – An Economic Perspective," *17th Annual Computer Security Applications Conference (ACSAC)*, 2001.

[^veracode]: Jens Wessling, "We Asked 100+ AI Models to Write Code. Here's How Many Failed Security Tests.," Jul 30, 2025, [https://www.veracode.com/blog/genai-code-security-report/](https://www.veracode.com/blog/genai-code-security-report/)

[^sandoval]: Gustavo A. Sandoval, Brendan Dolan-Gavitt, and Siddharth Garg, "Surgical Repair of Insecure Code Generation in LLMs: From Mechanistic Diagnosis to Deployment-Ready Intervention," 2026, [https://arxiv.org/abs/2604.16697](https://arxiv.org/abs/2604.16697).

[^google-sbd]: See Christoph Kern et al., from Google's Secure-by-Design effort, on using type systems to provide taint-tracking guarantees that eliminate SQL injection and XSS in Go and TypeScript codebases by construction: [https://storage.googleapis.com/gweb-research2023-media/pubtools/7661.pdf](https://storage.googleapis.com/gweb-research2023-media/pubtools/7661.pdf).

[^everest]: Jonathan Protzenko et al., "Project Everest: Perspectives from Developing Industrial-Grade High-Assurance Software," Microsoft Research, 2025. [https://www.microsoft.com/en-us/research/publication/project-everest-perspectives-from-developing-industrial-grade-high-assurance-software/](https://www.microsoft.com/en-us/research/publication/project-everest-perspectives-from-developing-industrial-grade-high-assurance-software/)

[^aws-iam]: Aleks Chakarov et al., "Formally Verified Cloud-Scale Authorization," ICSE 2025. [https://www.amazon.science/publications/formally-verified-cloud-scale-authorization](https://www.amazon.science/publications/formally-verified-cloud-scale-authorization)

[^zlib]: Leonardo de Moura, "When AI Writes the World's Software, Who Verifies It?" February 2026. [https://leodemoura.github.io/blog/2026-2-28-when-ai-writes-the-worlds-software-who-verifies-it/](https://leodemoura.github.io/blog/2026-2-28-when-ai-writes-the-worlds-software-who-verifies-it/)

[^vericoding]: "A Benchmark for Vericoding: Formally Verified Program Synthesis," 2025, [https://arxiv.org/abs/2509.22908](https://arxiv.org/abs/2509.22908).

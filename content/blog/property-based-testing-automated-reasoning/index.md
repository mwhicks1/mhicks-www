---
title: "Property-Based Testing Is For Finding Disproofs"
subtitle: ""
excerpt: "Property-based testing is often billed as a lightweight alternative to formal methods. But I think a more productive way of thinking is that PBT provides definitive disproofs of universal conjectures: This mindset raises questions about the role and capabilities of existing PBT tools."
date: 2026-03-12
author: "Mike Hicks"
draft: false
layout: single
_build:
  list: never
tags:
  - testing
  - verification
  - automated-reasoning
  - property-based-testing
categories:
  - programming-languages
  - software-engineering
---

Over the years I've done [research on fuzzing and property-based testing](http://localhost:1313/research/fuzz-testing/) (PBT). Property-based testing is often billed as a lightweight formal method: Don't prove properties, which is difficult; rather, test them thoroughly. The argument goes that PBT can be more widely adopted than full-blown formal verification, and its overall impact might therefore be greater than adhering strictly to formal methods.

In this post I want to make the case that PBT should not be considered primarily as a way of providing positive but indefinite evidence for a conjecture, but rather as a way of generating definite **disproof** of a conjecture. Thus it can be viewed as a complementary element of an automated reasoning-based approach: symbolic reasoning and other technology seeks proof, and PBT seeks disproof. I.e., both together, not one or the other. I would argue that the disproof-finding mindset also benefits the use and development of PBT technology.

## What is automated reasoning in formal methods?

[Formal Methods](https://shemesh.larc.nasa.gov/fm/fm-what.html) are mathematically rigorous techniques and tools for the specification, design, and verification of software and hardware systems. [Automated reasoning](https://en.wikipedia.org/wiki/Automated_reasoning) is the automated use of mathematical logic to draw valid conclusions, and both [automated theorem proving](https://en.wikipedia.org/wiki/Automated_theorem_proving) and [automated proof checking](https://en.wikipedia.org/wiki/Proof_assistant#Automated_proof_checking) are kinds of automated reasoning used with formal methods. In essence, both the specification and implementation of a system can be expressed as mathematical logic, and automated reasoning can be used to prove that the latter corresponds to the former.

Traditional methods of automated theorem proving, as used in modern [SMT solvers](https://en.wikipedia.org/wiki/Satisfiability_modulo_theories), often search for proofs of conjectured logical formulae by leveraging the structure of rules for logical deduction. A successful search produces a valid proof by construction. Alternatively, heuristic methods such as those based on machine learning can be used to conjecture a proof which is then checked for validity. For example, [Harmonic's Aristotle tool](https://aristotle.harmonic.fun/) uses generative AI to search for proofs of conjectures formalized in [Lean](https://lean-lang.org/), and uses Lean's proof checker to confirm a proof's validity.

## What kinds of conjectures are subject to automated reasoning?

The most interesting kinds of automated reasoning techniques prove conjectures that involve universal quantifiers. Otherwise, classical unit testing could also be considered a kind of automated reasoning, where the conjecture involves only specific input/output pairs. For example, a conjecture `sort [3,1,2] = [1,2,3]` can be decided by simply running `sort [3,1,2]` and making sure the output is `[1,2,3]`. An automated reasoning tool can prove a more powerful conjecture such as `∀ xs ys. sort(xs) = ys ⟹ (Permutation xs ys) ∧ (Sorted ys)`. Proof of this conjecture is far more useful!

## What is the API of an automated reasoning tool?

In general, an automated theorem proving tool will take a conjecture _P_ and provide one of three answers:

1. Conjecture _P_ is true (and provides a proof).
2. Conjecture _P_ is false (and provides a disproof, e.g., a counterexample).
3. Conjecture _P_'s truth or falsehood is unknown.

All three possibilities are inevitable when the logic used to form conjectures is at least [first-order](https://en.wikipedia.org/wiki/First-order_logic) (i.e., includes quantifiers), since [first-order logic is generally undecidable](https://en.wikipedia.org/wiki/Decidability_(logic)). As a practical matter, we prefer a tool that returns answers 1 and 2 as much and as quickly as possible, and answer 3 as little as possible.

## What is property-based testing?

[Property-based testing (PBT), as exemplified by the QuickCheck library](https://en.wikipedia.org/wiki/QuickCheck), is a kind of automated testing that can be applied to conjectures with universal quantifiers. For example, given the property `∀ xs ys. sort(xs) = ys ⟹ (Permutation xs ys) ∧ (Sorted ys)`, a PBT engine would repeatedly (say, 10,000 times):

1. randomly synthesize input list `xs`, and then run `sort(xs)` to produce `ys`
2. run `(Permutation xs ys)` and make sure it returns `true`, and likewise run `(Sorted ys)` and check that it returns `true`

If step 2 ever failed, that the input `xs` is a counterexample to the claimed property: There is a bug in the sorting algorithm. If step 2 never fails, then we have some assurance that `sort` is correct (maybe moreso than we would from typical unit tests), *but we do not know for sure.*

## How is property-based testing typically framed?

One way of framing PBT is as an improvement over unit testing. By formulating a general property and automating input generation, PBT can potentially discover corner-case bugs missed by ad hoc unit tests. Another way of framing PBT is as a _lightweight_ formal method. While not providing the full proofs, the PBT methodology at least gets engineers thinking about specifications with universal quantifiers and provides some evidence that those specifications hold. In the case that proofs are impossible or impractical (due to resource or tool constraints), PBT is better than nothing.

## Should property-based testing be considered as a kind of automated reasoning?

In one sense, no, and in another sense, yes.

PBT _cannot_ prove a universally-quantified conjecture such as `∀ xs ys. sort(xs) = ys ⟹ (Permutation xs ys) ∧ (Sorted ys)` discussed above. The "lightweight formal method" framing may mislead people into thinking that PBT provides proof-like assurance in a practical sense, but I think this mindset is a little dangerous.

At the same time, PBT _can_ prove properties that have *existential* quantifiers — the negation of a universal is existential. So we could use PBT to prove that `sortbad` was buggy via `∃ xs ys. sortbad(xs) = ys ⟹ ¬((Permutation xs ys) ∧ (Sorted ys))`.

Moreover, since PBT can prove existential properties, it can **provide a proof that a universal conjecture is *false***, i.e., it can provide a disproof. Thus it fulfills an important role (option 2, from above) in the API of an automated theorem proving tool.

## Is finding disproofs useful?

Automating disproofs can be enormously helpful. With disproofs in hand, users can quickly identify incorrect definitions and theorem statements before they waste time on a proof that could never succeed, and thereby accelerate their path to a proof of the right theorem. By "users," we might also be referring to AI agents, such as those attempting to generate code according to a logical specification, and a disproof gives them actionable feedback about their mistakes. Disproof has been shown to be useful in state-of-the-art automated solvers, such as Harmonic's Aristotle. Quoting from their [paper](https://arxiv.org/pdf/2510.01346)

>in order to prune states and disprove statements, we augment each single-goal state with a state transition corresponding to the logical negation of that goal, to which the search algorithm can allocate search budget.

In Harmonic's case they are using the same symbolic methods as proof. This is a matter of engineering. Harmonic is reasoning about mathematical structures in Lean, where non-constructive axioms are often assumed, and thus an executable interpretation is not available. However, in some cases (such as executable representation of programs), we retain the computational interpretation and PBT is relevant.

## Is PBT a good way of finding disproofs?

PBT is an effective tool at finding counterexamples when the objects being reasoned about are executable, e.g., programs. Programs are by their very nature executable, and also suffer from the state-space explosion problem when reasoning symbolically. Actually executing programs with concrete inputs allows us to sidestep this problem, and instead relies on the CPU doing what it's great at: running programs. Random testing and its variants (such as fuzzing) have proven enormously beneficial when universal specifications exist, and are the dominant tool in the industry to disprove low-level security specifications such as memory safety.

## Why is this a different way of thinking about PBT?

The framing that PBT is a lightweight formal method suggests that it's primarily about finding positive but incomplete evidence for a conjecture. The framing that PBT aims to find disproofs suggests that its power is in finding _negative_ evidence for a conjecture, i.e., bugs.

There is a subtle distinction here. If you are looking for positive evidence, you are not necessarily motivated to question what it means when you don't find any bugs. Are there actually no bugs, or have you not tried hard enough to find them? The first framing biases you toward the former conclusion, the second framing biases toward the latter.

When we are biased toward the latter conclusion, we start probing our assumptions more. Are my input generators good enough? Am I executing unusual and tricky code paths? Surprisingly, PBT tools largely don't provide answers to these questions. The recent [Tyche](https://andrewhead.info/assets/pdf/tyche.pdf) work aims to provide some help here, but I think there's a lot more the research community could do.

Once you've used PBT to find bugs, of course it makes sense to run it in CI/CD, to keep up the hunt. But you should not delude yourself (without additional rigorous argument) that PBT is "good enough."
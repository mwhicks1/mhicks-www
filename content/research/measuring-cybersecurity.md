---
title: "Measuring Cybersecurity"
subtitle: "From Build it, Break it, Fix it contests to Cyber Public Health"
excerpt: "Research on measuring and improving cybersecurity practices, developer behavior, and end-user impact."
categories:
  - Research
  - Security
  - Measurement
weight: 4
---

## Overview

A fundamental challenge in cybersecurity is connecting innovations to their real-world impact. How do we know if a new security tool, technique, or policy actually makes people safer? How do we assess the effectiveness of secure development practices? My research aims to apply empirical measurements to better understand and improve cybersecurity outcomes.

## Build it, Break it, Fix it Contests

[**Build it, Break it, Fix it** (BIBIFI)](https://builditbreakit.org)) is a security-oriented programming competition my collaborators and I created to encourage and study secure software development. BIBIFI has three phases, essentially marrying a traditional programming contest with a capture-the-flag contest:

1. **Build it**: Teams implement a secure system according to a specification
2. **Break it**: Teams try to find vulnerabilities in other teams' submissions
3. **Fix it**: Original teams patch the vulnerabilities found in their code

This structure is tantamount to a quasi-controlled experiment that allows us to measure:
- Common security vulnerabilities developers introduce
- Effectiveness of different secure coding practices
- How developers respond to security feedback
- Trade-offs between security, functionality, and performance

### Papers and Talks

- **[Build it, Break it, Fix it: Contesting Secure Development](/papers/ruef16bibifi.html)** (CCS 2016)
  Presents the contest design and initial results, with data analysis revealing (un)successful attack and defense strategies. The [long version](/papers/ruef16bibifi-long.html) (ACM TOPS) includes results from an additional contest.

- **[Understanding security mistakes developers make: Qualitative analysis from Build It, Break It, Fix It](/papers/votipka19bibifiqual.html)** (USENIX Security 2020) **Distinguished Paper**
  Qualitative analysis of vulnerabilities in BIBIFI contest submissions, revealing that conceptual design mistakes were the most significant source of vulnerability.

- **Talk**: [Build it, Break it, Fix it: Contesting Secure Development](https://www.youtube.com/watch?v=Sh03HKhNrlk) (2020)

## Cyber Public Health

[Cyber Public Health](https://cybergreen.net/cyber-public-health/) applies lessons from public health to cybersecurity. Public health tracks disease outbreaks and intervention effectiveness; we need similar efforts to improve cybersecurity. In particular:

- **Measuring end-user cyber harm**: Developing methodologies to quantify the actual harm users experience from cyber incidents
- **Outcomes-based metrics**: Moving beyond counting vulnerabilities to measuring real security impacts
- **Data-driven interventions**: Using empirical data to guide security improvements

I am working with Penn colleagues in business, law, policy, and health to advance this agenda. It is early days for us: Get in touch if you have interest or ideas!

### Resources

- Talk: [Measuring End-User Cyber Harm](https://www.youtube.com/watch?v=q9uG0TIwyEc) (17th Cyber Public Health Workshop, 2025)
- Course: [Empirical Security and Privacy, for Humans](/courses/cis-7000-fall2025/) (UPenn CIS 7000, Fall 2025)
  My seminar course exploring empirical methods in security and privacy research, with emphasis on human factors.
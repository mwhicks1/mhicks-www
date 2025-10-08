---
title: "Week 4: Building Secure Software"
date: 2015-01-01
author: "Mike Hicks"
draft: false
weight: 4
layout: single
build:
  list: never
---

Most of our time so far has been spent focusing on implementation-level issues---*bugs* that constitute vulnerabilities, and means of avoiding those bugs, mitigating them, or recovering from them. But we must also be concerned about *flaws*, which are security problems in a software system's design.

To address both flaws and bugs effectively, we need to consider security through the entire development process. In this unit, we will step back and look at what that entails, taking on the goal of *building security in*.

## Learning Objectives

After the completion of this week's material, you will be able to:

- Identify how security-minded thinking, or security engineering, is integrated into the software development process
- Enumerate a series of design principles for writing secure software
- Explain how such principles can be violated, pointing to actual incidents
- Put these principles into practice by drawing inspiration from well-designed, secure systems

## Video Lectures

- [Designing and Building Secure Software: Introduction](https://youtu.be/Nm3Rgb1EuJo) (7:23)
- [Threat modeling (Architectural risk analysis)](https://youtu.be/SbkJ7l8JVEA) (9:25)
- [Security Requirements](https://youtu.be/6ZEsnxHIjjA) (13:56)
- [Avoiding Flaws with Principles](https://youtu.be/6WdvIwqlVNI) (8:12)
- [Design Category: Favor Simplicity](https://youtu.be/qMcWCYCshnA) (10:50)
- [Design Category: Trust With Reluctance](https://youtu.be/B_qkiiSU9lc) (12:32)
- [Design Category: Defense in Depth, Monitoring/Traceability](https://www.youtube.com/watch?v=cxBPbJcqZtg) (5:20)
- [Top Design Flaws](https://youtu.be/5tJ79GmJipg) (9:18)
- [Case Study: Very Secure FTP Daemon](https://youtu.be/vS420g1egfw) (12:24)

### Break out: Interview with Gary McGraw

In August 2014, Mike had the pleasure of interviewing [Gary McGraw](https://www.garymcgraw.com/). Gary is a celebrated author and authority on software security, which he practiced professionally as the CTO of [Cigital, Inc. until they were acquired by SynopSys in 2016](https://www.synopsys.com/blogs/software-security/synopsys-acquires-cigital-codiscope/). In this interview we discussed many things relevant to this week's topic of secure design and secure development. The interview is optional from an assessment perspective -- there will no quiz questions on it (but note it may help cement topics in the lectures). We hope you find it interesting!

[Mike Hicks interviews Gary McGraw](https://youtu.be/-kw5nptAOYo) (40:52). Highlights, indexed by time:

- start-3:47 Gary's background and early activities in software security
- 3:48-8:10 Software security: What, why, and who
- 8:10-14:55 Security throughout the development lifecycle: Secure design, not just secure coding
- 14:56-18:27 Moving towards more secure development practices
- 18:27-26:58 [Building Security In Maturity Model (BSIMM)](http://bsimm.com/)
- 26:58-32:42 Measuring security: How can BSIMM help?
- 32:42-37:19 Looking ahead: Improving secure design
- 37:19-40:52 Closing: Free time, art, music, and computer science

## Supplemental Links

These links go into more depth about topics covered during lecture.

- [Protection of Information in Computer Systems](http://web.mit.edu/Saltzer/www/publications/protection/), by Saltzer and Shroeder. Classic paper from 1975 that is still highly relevant today.
- Bruce Schneier's [plea for simplicity](https://www.schneier.com/essays/archives/1999/11/a_plea_for_simplicit.html) in computer systems.
- [Avoiding the top 10 Security Design Flaws](https://ieeecs-media.computer.org/media/technical-activities/CYBSI/docs/Top-10-Flaws.pdf), brought to you be the [IEEE Center on Secure Design](http://cybersecurity.ieee.org/center-for-secure-design.html)
- [Very Secure FTPD](https://security.appspot.com/vsftpd.html); here is some description of VSFTPD's [design](https://security.appspot.com/vsftpd/DESIGN.txt), [implementation](https://security.appspot.com/vsftpd/IMPLEMENTATION.txt), and assumptions of [trust](https://security.appspot.com/vsftpd/TRUST.txt) (and their impact on the implementation).
- Gary McGraw's book, [Software Security: Building Security In](http://www.swsec.com/).

## Quiz

The [quiz for this week](/course/software-security/assets/week4_quiz.docx) covers all of the material for this week.

## Project

There is **no new project** this week. Don't forget that [Project 2](../project2) on exploiting web application vulnerabilities, issued last week, is still outstanding, and is due in two weeks.

---
title: "Week 3: Web Security"
date: 2015-01-01
author: "Mike Hicks"
draft: false
weight: 3
layout: single
build:
  list: never
---

Now we move away from low-level security and turn our attention to security on the worldwide web (WWW).

The web utilizes a variety of technologies, from HTTP (hypertext transfer protocol) and HTML (hypertext markup language) to SQL (standard query language) and the Javascript programming language. Unfortunately, these technologies can be used in ways that constitute significant vulnerabilities. We will examine several important kinds of vulnerabilities, see how they can be exploited, and explore how to defend against them.

## Learning Objectives

After the completion of this week's material, you will be able to:

- Understand how **SQL injection** attacks affect web application back ends
- Understand how the web implements *session state*, using *cookies* and *hidden form fields*, and how improper implementations are subject to **session hijacking** and **Cross-site Request Forgery (CSRF)** attacks
- Understand how popular, browser-executed *Javascript* programs can be used incorrectly by web sites, leading to **Cross-site Scripting (XSS)** vulnerabilities
- Avoid flaws and bugs that introduce these vulnerabilities, with a focus on employing **input validation** and **sanitization**

## Video Lectures

- [Security for the Web: Introduction](https://youtu.be/UMayZxyQUg0) (3:33)
- [Web Basics](https://youtu.be/gkUxGq09wSs) (10:31)
- [SQL Injection](https://youtu.be/n8lkVAri7c0) (10:35)
- [SQL Injection Countermeasures](https://youtu.be/n_rVX4r65zE) (9:17)
- [Web-based State Using Hidden Fields and Cookies](https://youtu.be/U_gUy0hZsrs) (13:51)
- [Session Hijacking](https://youtu.be/Mcg8AIlb59g) (6:56)
- [Cross-site Request Forgery (CSRF)](https://youtu.be/5ffy65DKAZw) (6:36)
- [Web 2.0](https://youtu.be/TmT02T7X0Fw) (5:16)
- [Cross-site Scripting](https://youtu.be/RW7qpjybD3U) (13:39)

### Break out: Interview with Kevin Haley

In March 2015, Mike had the pleasure of interviewing [Kevin Haley](https://www.linkedin.com/in/khaley/). Kevin was a Director of Symantec Security Response. In this interview we discussed the state of cybersecurity at that time: the trends, the hacks, and the situations that define the state of play in which technology developers and users find themselves. The interview is optional from an assessment perspective -- there will no quiz questions on it. We hope you find it interesting!

[Mike Hicks interviews Kevin Haley](https://youtu.be/1gwi01aLfws) (21:13). Highlights, indexed by time:

- start-2:11 Kevin's background and early activities in security
- 2:11 Symantec's vantage point
- 4:14 Scope of the security threat
- 5:38 Commoditization of vulnerability exploitation
- 7:31 Vulnerabilities trending upward
- 8:16 Role and approach of anti-virus and related technologies
- 11:38 Advice on building secure systems, and education
- 16:14 The expanding security landscape
- 19:44-end Learning more

## Readings

No readings are required for this week, but you may find the following references helpful.

- [OWASP's guide to SQL injection](https://www.owasp.org/index.php/SQL_Injection) - This is a good overview. You might find the linked page on [Testing for SQL injection](https://owasp.org/www-project-web-security-testing-guide/latest/4-Web_Application_Security_Testing/07-Input_Validation_Testing/05-Testing_for_SQL_Injection) to be useful for the project.
- [SQL injection cheat sheet](http://ferruh.mavituna.com/sql-injection-cheatsheet-oku/) - This is a good reference for doing SQL injection
- [OWASP's guide to cross-site scripting (XSS)](https://owasp.org/www-community/attacks/xss/) - Pay particular attention to the testing guide, for finding XSS vulnerabilities.
- [OWASP's guide to session hijacking](https://www.owasp.org/index.php/Session_hijacking_attack) - Note that they give an example of stealing a session cookie via XSS, which is in play for the project.
- [OWASP's guide to cross-site request forgery (CSRF)](https://owasp.org/www-community/attacks/csrf)
- [CWE/SANS top 25 most dangerous software errors](http://cwe.mitre.org/top25/) - past versions are [archived](https://cwe.mitre.org/top25/archive/).

## Quiz

The [quiz for this week](/course/software-security/assets/week3_quiz.docx) covers all of the material for this week. You must submit the quiz no later than the start of week 5.

## Project

The [second project](../project2) tests your ability to exploit vulnerabilities in a web application called BadStore. It is due in three weeks, at the start of week 6. You will complete the work for the project on your own computer, and then take the [on-line assessment](/course/software-security/assets/week3_badstore_quiz.docx) to show that you've done so.

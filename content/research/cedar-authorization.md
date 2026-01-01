---
title: "Cedar & Authorization"
subtitle: "Expressive, fast, safe, and analyzable authorization policies"
excerpt: "The Cedar policy language for authorization, and verification-guided development methodologies for building high-assurance systems."
categories:
  - Research
  - Security
  - Languages
weight: 5
---

## Overview

[**Cedar**](https://cedarpolicy.com) is a domain-specific language for writing and enforcing authorization policies. You write Cedar policies to say who can do what in your application, which invokes the Cedar authorization engine to allow/deny each user request. Cedar is designed to be:

- **Expressive**: Rich enough to encode complex authorization requirements
- **Fast**: Efficient authorization decisions even at cloud scale
- **Safe**: Type system prevents common policy errors
- **Analyzable**: Automated reasoning can verify policy properties

Cedar demonstrates how programming language techniques — type systems, formal semantics, verification — can underpin practical, high-assurance security tools. I co-led Cedar's development (with [Emina Torlak](https://emina.github.io/)) during 2022-2024 while full-time at Amazon Web Services, and I'm still involved today as a Cedar user and maintainer.

*Cedar is open-source*. You can find its main implementations in Rust and Go, its formal specification and differential testing apparatus, and a variety of examples at [https://github.com/cedar-policy/](https://github.com/cedar-policy/). Join [Cedar's Slack](https://communityinviter.com/apps/cedar-policy/cedar-policy-language) to meet and chat with Cedar developers and users.

*Cedar is used in production*. Here are several examples:

- **[Amazon Verified Permissions](https://aws.amazon.com/verified-permissions/)**: AWS's managed authorization service built on Cedar
- **MongoDB**: Uses Cedar for authorization in Atlas and other products
- **Cloudflare**: Deployed for internal authorization decisions
- **[StrongDM](https://www.strongdm.com/)**: Startup using Cedar for access management services

## Verification-Guided Development (VGD)

Cedar pioneered an approach we call **verification-guided development**, which combines formal verification, property-based and differential testing, and careful API design to build high-assurance software:

1. **Formal specification**: Mathematical model of system behavior in Lean
2. **Mechanized proofs**: Verify critical security properties of Cedar's design
3. **Property-based testing**: Use thousands of automatically generated inputs in an attempt to falsify key implementation properties
4. **Differential testing**: Conformance-test implementations (in Rust and Go) against the formal specification

**Talk**: [Amazon's Formal Methods Journey](https://www.youtube.com/watch?v=ZuPGZ3W-ITA) (DARPA Resilience Meeting, 2025)

## Key Publications and talks

- **Cedar: A New Language for Expressive, Fast, Safe, and Analyzable Authorization**: [PDF](https://dl.acm.org/doi/pdf/10.1145/3649835) (OOPSLA 2024) [Youtube](https://www.youtube.com/watch?v=hdc5JZZNDSs)
  The definitive paper and talk on Cedar's design, including its type system, semantics, validator, and verification approach.

- **[How We Built Cedar: A Verification-Guided Approach](https://www.amazon.science/publications/how-we-built-cedar-a-verification-guided-approach)** (ESEC/FSE 2024, Industrial Track)
  Details on our development methodology and lessons learned building a production security system with formal methods.

## Future Directions

- Extending Cedar's expressiveness while maintaining analyzability
- New analysis capabilities (policy optimization, coverage checking)
- Integration with GenAI for Cedar policy generation and explanation, especially of natural-language policy documents

## Resources

- **[Official Cedar Website](https://cedarpolicy.com)**
- **[Cedar Documentation](https://docs.cedarpolicy.com/)**
- **[Cedar GitHub Organization](https://github.com/cedar-policy)**
- **[AWS Verified Permissions](https://aws.amazon.com/verified-permissions/)**
- **[Cedar Playground](https://www.cedarpolicy.com/en/playground)** - Try Cedar in your browser
- **[Cedar Academic Paper](https://dl.acm.org/doi/pdf/10.1145/3649835)**

---
layout: cv
title: Justin Martin
---
# Justin Martin
Principal Engineer: market data, optimization, formal verification, AI systems

<div id="webaddress">
<a href="mailto:justin@thefrozenfire.com">justin@thefrozenfire.com</a> | <a href="https://github.com/TheFrozenFire">github.com/TheFrozenFire</a> | BC, Canada
</div>

## Profile

Principal-level engineer with 15+ years building production systems where correctness matters: real-time market data and pricing, execution optimization, high-throughput messaging, and compliance. I pair hands-on Rust and TypeScript engineering with numerical methods and machine-checked proofs (Rocq), and I build day to day with AI coding agents. Looking to apply this to AI and finance.

### Specialized in

* Market data, pricing and execution optimization
* Numerical and convex optimization, constrained curve fitting
* Formal verification (Rocq, CAS cross-checking, fuzzing)
* AI agent tooling and LLM-in-the-loop workflows
* Applied cryptography and security engineering
* Observability, load testing, infrastructure as code
* Telecom systems (SMS, VoIP, SMPP, SIP)

### Research interests

* Verified financial algorithms
* Mechanism design
* Privacy
* Adversarial Interoperability
* Due Process by Design

## Experience

`Jan 2026 – Oct 2026`
__Reserve (ABC Labs)__

Index-fund products on digital-asset markets. Built the Rust service that prices assets and plans basket creation/redemption across fragmented trading venues, replacing the prior TypeScript generation.

- Built a real-time market data and pricing engine
  - Direct-from-source ingestion of assets, trading venues and reference price feeds across three markets
  - Three-strategy pricing chain (venue midpoint, recursive basket decomposition, reference-feed fallback), kept separate from side-effectful data gathering
  - Event-sourced journal pipeline with upstream-retraction handling and resumable replay
  - Graph-based market model (Neo4j, then embedded graph DB); found and fixed an O(N) edge-upsert defect behind CPU saturation
  - Data catalog on Open Data Contract Standard v3.1: 42 contracts, 14 external APIs
- Built the execution routing optimizer
  - Convex (Clarabel) formulation with flow-conservation constraints, matching 100% of the incumbent Nelder–Mead output on test cases
  - Cut the optimizer hot loop 37% (44.6µs to 28.7µs) on a ~1,100-dimension problem
  - Conservative, monotone market-impact curve fits using a hand-written Lawson–Hanson NNLS solver and an exact monotonicity certifier
  - Synthetic benchmark suite with difficulty-weighted scoring; double-double (~32-digit) arithmetic for value comparisons
- Formalized the routing problem: dual-SOCP hybrid method, an NP-hardness result (3-Partition), convergent upper bounds; Rocq proofs bound to production tests
- Built a competitive batch-auction order solver and brought it up in shadow mode in production
- Pre-trade simulation and execution planning for multi-step transactions
- Typed risk model covering 18 funds and 120 assets, with provenance on every claim
- Observability and testing: Grafana/Loki prod-vs-staging dashboards, live replay of production traffic to staging, Locust load tester, large-order regression suites
- Infrastructure: data-provider routing (fixed retry storms cascading into rate limits), Ansible fleet, and a Terraform provider written in Go
- Wrote LLM-facing API documentation (llms.txt, AGENTS.md); built AI meeting-transcript tooling

`2022 – 2025`
__Keyring Network__

- Built a privacy-preserving identity verification (KYC/AML) protocol for regulated finance from the ground up
- Built zero-knowledge proof primitives and a circuit development toolchain (Circom, TypeScript, Rust), including blinded RSA signing
- Productionized TLS Notary to prove facts about web data without revealing it
- Advised on privacy, security and trust minimization

`2021 – 2023`
__Ethereum Foundation (Privacy & Scaling Explorations), eth.limo__

- Built a zero-knowledge system for proving possession of identity-provider JWTs (privacy-preserving authentication)
- Published open-source cryptographic primitives; supported developers adopting privacy tooling
- Research program management: talent scouting, grants coordination, product processes for taking grant projects to production
- eth.limo: built Chauffeur, a local name-resolution and serving stack; advised on privacy and performance

`2013 – 2021`
__CallFire / EzTexting__

- Built an automated heuristic and machine-learning messaging compliance system enforcing industry content regulations
- Principal Engineer, Growth: bootstrapped a Growth team that used A/B testing to substantially reduce churn and raise conversion and ARPU
- Built an anti-spam, anti-fraud threat modelling engine
- Built an Operational Intelligence platform for reporting, monitoring and analysis of infrastructure and telephony operations
- "Cloud Caller" provisioning automation enabling a 20× increase in outbound capacity
- Principal Engineer, Operations: infrastructure, security, carrier operations; led migration to automated cloud provisioning and monitoring
- Platform Architect: refactored most of EzTexting's message processing, routing and origination software
- Professional services for enterprise customers (custom scheduling, routing, reporting); wrote CallFire's PHP SDK

`2013 – 2019`
__Roave__

- Built and ran SMSCloud, a high-throughput SMSC connecting businesses to carrier networks (later a CallFire vendor)
- Ran agency operations: contracts, recruitment

`2012`
__MediaDevils__

- High-volume ecommerce for direct-response ("As Seen on TV") products; membership video streaming and online learning platforms

## Selected projects

`2025 – 2026`
__Formal methods__

- Corpus reproducing historic financial-contract failures as proof/counter-proof pairs, each confirmed by 2+ tools; axiom-free Rocq proofs
- Rocq model that classifies legal contracts by conformance to law
- Upstream fixes to a Solidity-to-Rocq compiler; MCP server for agent-driven Rocq proof workflows
- Rocq and CAS theory of groups of unknown order and classical cipher analysis

`2025 – 2026`
__Performance and payments__

- GPU number-theory kernels: 62× over CPU, with Montgomery batch inversion
- Reduced an ECDSA proof circuit 38% (2.58M to 1.59M constraints)
- Rust EMV payment-card certificate reader over NFC

## Patents

`2019`
Blockchain network communication management, [US20210243036A1](https://patents.google.com/patent/US20210243036A1/en)

## FOSS

`2008 – 2016`
__PHP__

- [Credited](https://www.php.net/manual/en/preface.php#contributors) documentation maintainer and voting [project member](https://people.php.net/frozenfire)
- Founded PHP Mentoring; contributed to Zend Framework; community management

`Last updated: October 2026`

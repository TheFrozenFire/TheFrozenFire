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

Sections marked ▸ expand for technical detail.

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

Index-fund products on digital-asset markets. Led the engineering of the service that prices assets and plans basket creation/redemption across fragmented trading venues: first a TypeScript generation (Jan–Jun), then a Rust rewrite (Mar–Oct) that replaced it. About 6,300 commits across 20+ repositories.

<details markdown="1">
<summary markdown="span">**Market data and pricing engine**: real-time, multi-venue ingestion into an event-sourced journal and graph market model</summary>

- **Pricing as pure arithmetic.** Separated problem construction (side-effectful search, quoting, redemption simulation) from price computation, which is pure arithmetic over a valuation object, so pricing logic is deterministic and testable in isolation
- **Three-strategy pricing chain** in confidence order: venue swap midpoint, then recursive basket decomposition (pricing each component), then reference-feed fallback; prices in synthetic USD anchored to a stablecoin; epoch-scoped price cache and a multi-anchor swap pricer
- **Journalled ingestion.** Per-protocol mappers emit field-level deltas into a journal; tables give pending writes precedence and isolate upstream chain reorganizations (data retractions); catch-up reads indexed by (source, block, sequence, write id) for exact resumption
- **Graph market model.** Projected the routing graph into Neo4j, then into the embedded graph database grafeo, with a staged cutover; isolated an O(N) edge-upsert scaling defect that was saturating CPU; resumable, cursor-aware replay
- **Kind-agnostic job scheduler**; migrated stats, scoring and edge workloads onto it
- **Venue coverage:** constant-product, concentrated-liquidity and stableswap market makers (Uniswap V2/V3/V4, Curve, Balancer V2/V3, Aerodrome, SushiSwap), yield vaults (ERC-4626) and lending markets (Morpho), across Ethereum, Base and BSC
- **Data-provider validation:** `rpc-doctor`, a capability and throughput prober that discovers batch-size and execution-cost limits of node providers
- **Data contracts:** catalog on Open Data Contract Standard v3.1 covering 42 contracts and 14 external APIs
</details>

<details markdown="1">
<summary markdown="span">**Execution routing optimizer**: constrained multi-venue order routing via convex and derivative-free optimization</summary>

- **Convex formulation.** Added a Clarabel (interior-point conic) solver alongside Nelder–Mead, with flow-conservation constraints across the venue graph; matched 100% of Nelder–Mead output on a native-tick test case
- **Hot-path performance.** Cut Nelder–Mead objective evaluation from 44.6µs to 28.7µs (−37%) on a 357-node, ~1,100-dimension fixture; 500ms per-call budget; deterministic RNG seeding; solver config and trace harness for reproducible runs
- **Warm starts.** Execution-cost-free merit-order initialization; LP warm start in the formal method (below)
- **Numerical robustness.** Bisection fixed for extreme asset scales (a 27-order-of-magnitude bracket); double-double (~32-digit) arithmetic for value comparisons; paths ranked by output capacity rather than spot rate
- **Benchmark "gym".** Synthetic graphs with power-law weights and venue depths from $1K to $10M, difficulty-weighted scoring; basket tests assert ≥95% efficiency and ≤5% residual dust
</details>

<details markdown="1">
<summary markdown="span">**Market-impact curve fitting**: conservative, provably monotone fits replacing step-function liquidity</summary>

- Ported a log-log polynomial fit per trading edge from an earlier Rust data service, giving the optimizer smooth curves instead of tick-boundary cliffs
- Fits are conservative by construction: they never over-predict output
- Monotone-constrained fit via a Bernstein-basis derivative, solved with a hand-written Lawson–Hanson non-negative least squares (NNLS) solver
- Exact Bernstein monotonicity certifier to verify fitted curves
</details>

<details markdown="1">
<summary markdown="span">**Formal theory and verification**: optimization theory with a hardness result, and machine-checked proofs bound to production tests</summary>

- **Theory of ratio-constrained routing:** dual-SOCP hybrid method, LICQ (constraint-qualification) characterization, an NP-hardness barrier by reduction from 3-Partition, convergent upper bounds, LP warm start; synthetic experiments S1–S13 validated against arXiv:2601.03799
- **Rocq proofs with CAS witnesses** (PARI/GP) bound to production tests, e.g. a "Full-Budget Principle", an implicit-function-theorem concavity bracket factorization, and 16 theorems bound to Nelder–Mead tests
- **Layered architecture design** (vegvisir): L0–L3 routing substrate with Rocq models and a parity gate against production (member set 120/120, venue evaluation 6/6 within 0.5%) over ~708k venues
- **Fuzzing** of quote round-trips to catch phantom arbitrage (664+ corpus entries)
</details>

<details markdown="1">
<summary markdown="span">**Batch-auction order solver**: competitive best-execution engine, run in production shadow mode</summary>

- Solver engine scaffold, order filtering and settlement lowering for CoW Protocol batch auctions
- Mainnet shadow bring-up with operational runbook
- Solver multiplexer fanning auctions out to multiple engines and choosing a winner by fills, then surplus, then latency
</details>

<details markdown="1">
<summary markdown="span">**Execution planning and pre-trade simulation**</summary>

- Transaction planner on the Weiroll VM with venue encoders (Curve, Balancer, ERC-4626)
- Batched pre-trade simulation (`eth_callMany`) with balance-slot resolution
- Upstream fix to a node client's multi-block simulation (`eth_simulateV1` parent-header lookup)
</details>

<details markdown="1">
<summary markdown="span">**Prior TypeScript generation**: domain-driven refactor and migration to Rust</summary>

- Domain-driven refactor: extracted a block-state service, introduced protocol base classes; graph-build timing instrumentation
- Diagnosed pathological venues requiring 35–50M+ execution units per quote; made the quoter cap configurable (10M default); tracked p90 latency (~730ms)
- Ran the migration to the Rust service with a dedicated regression environment
</details>

<details markdown="1">
<summary markdown="span">**Risk and research products**: fund risk model and prediction-market index design</summary>

- Typed YAML risk model covering 18 funds and 120 assets, with provenance tags on every claim
- Explored a perpetual prediction-market index (Polymarket), including phase analysis of entry and exit
- Test coverage for an auction-bidding bot, including race conditions
</details>

<details markdown="1">
<summary markdown="span">**Observability, regression and load testing**</summary>

- Grafana dashboards comparing production and staging on response time, market impact and residual dust; slippage and loss panels
- Live replay of production traffic into staging by tailing Loki; custom Rust Loki tracing layer
- Moved the load tester from aiohttp to Locust with swap, price and mixed user profiles
- Regression suites including $1M creation/redemption tests at <2% market impact; Marimo notebook suites bucketed by market cap
</details>

<details markdown="1">
<summary markdown="span">**Infrastructure**: data-provider routing, node fleet, infrastructure as code</summary>

- Fixed retry storms in the provider proxy (~54 calls/min per upstream cascading into rate limits); capability-aware routing via block availability (eRPC); WebSocket head-tracking resilience
- Node operations: raised simulation limits, recovered a node stalled after a network upgrade
- Ansible fleet playbooks, Vault, Traefik and Gatus; Go backup CLI
- Wrote a Terraform provider in Go (data sources, CRUD resources, HCL generator)
- MongoDB replica set and Neo4j staging deployments with versioned reingestion
</details>

<details markdown="1">
<summary markdown="span">**AI and agent tooling**</summary>

- LLM-facing API documentation (`llms.txt`, ~5,400-word `llms-full.txt`, AGENTS.md)
- Meeting tooling: X Spaces download, transcription and AI-generated minutes; transcript processing into weekly journals
- Agent-heavy development practice (Claude Code, Devin), with repository-level agent instructions and agent review loops
</details>

`2022 – 2025`
__Keyring Network__

Privacy-preserving identity verification (KYC/AML) for regulated finance, built from the ground up.

<details markdown="1">
<summary markdown="span">**Detail**: protocol, proof primitives, toolchain, web proofs</summary>

- Designed and built the zero-knowledge compliance protocol: users prove they passed verification without disclosing identity data
- Built zero-knowledge primitives in Circom, TypeScript and Rust, including blinded RSA signing constructed in-circuit
- Built a circuit development toolchain in TypeScript
- Productionized TLS Notary (MPC-TLS) to prove facts about web data without revealing it
- Built a decentralized protocol messaging layer (OrbitDB)
- Advised on privacy, security and trust minimization
</details>

`2021 – 2023`
__Ethereum Foundation (Privacy & Scaling Explorations), eth.limo__

Privacy-preserving authentication research and research program management.

<details markdown="1">
<summary markdown="span">**Detail**</summary>

- Built a zero-knowledge system proving possession of JWTs issued by social identity providers
- Published open-source cryptographic primitives; supported developers adopting privacy tooling
- Infrastructure support for compiling large proof circuits
- Research program management: talent scouting, grants coordination, product processes for taking grant projects to production
- eth.limo: built Chauffeur, a local name-resolution and serving stack; advised on privacy, decentralization and performance
</details>

`2013 – 2021`
__CallFire / EzTexting__

Principal Engineer across platform, operations, security and growth for a high-volume business messaging and voice platform.

<details markdown="1">
<summary markdown="span">**Machine learning, compliance and growth**</summary>

- Built an automated heuristic and machine-learning messaging compliance system enforcing industry content regulations
- Built an anti-spam, anti-fraud threat modelling engine
- Principal Engineer, Growth: bootstrapped a Growth team that used A/B testing to substantially reduce churn and raise conversion and ARPU
- Built an Operational Intelligence platform for reporting, monitoring and analysis of infrastructure and telephony operations
</details>

<details markdown="1">
<summary markdown="span">**Platform, operations and infrastructure**</summary>

- "Cloud Caller" provisioning automation enabling a 20× increase in outbound capacity
- Principal Engineer, Operations: infrastructure, security, carrier operations; led migration to automated cloud provisioning and monitoring
- Platform Architect: refactored most of EzTexting's message processing, routing and origination software
- Professional services for enterprise customers (custom scheduling, routing, reporting); wrote CallFire's PHP SDK
- Started as SMS connectivity vendor via SMSCloud
</details>

`2013 – 2019`
__Roave__

- Built and ran SMSCloud, a high-throughput SMSC connecting businesses to carrier networks
- Ran agency operations: contracts, recruitment

`2012`
__MediaDevils__

- High-volume ecommerce for direct-response ("As Seen on TV") products; membership video streaming and online learning platforms

## Selected projects

`2025 – 2026`
__Formal methods__

Machine-checked reasoning about financial, legal and cryptographic systems in Rocq, cross-checked with computer algebra.

<details markdown="1">
<summary markdown="span">**Detail**</summary>

- **Financial-contract failure corpus:** verification/counter-proof pairs reproducing historic exploits (e.g. a ~$80M reward over-distribution; vault share-price manipulation), each confirmed by 2+ independent tools; Rocq proofs with zero axioms (one family: 39 theorems)
- **Legal-contract conformance:** Rocq model classifying legal contracts by how well they conform to law
- **Compiler work:** upstream fixes to a Solidity-to-Rocq compiler (C++ codegen bugs, a contract-call proof rule, mapping-of-struct storage)
- **Agent tooling:** MCP server for Rocq that surfaces diagnostics and hints to drive agent-based proof workflows
- **Groups of unknown order:** Rocq and CAS theory, including factoring RSA moduli from the private exponent and a catalog of key-generation leaks; a proving system over RSA groups (powers of tau, QAP, Fiat–Shamir)
- **Cipher analysis:** Rocq laboratory for classical ciphers with differential and linear S-box analysis
- **Shared library:** modular arithmetic, quadratic fields Z[√d], cipher theory
- **Governance-contract verification:** 100% Rocq compile coverage with findings dispositions; 26-script CAS suite across 13 domains
</details>

`2025 – 2026`
__Performance, math and payments__

<details markdown="1">
<summary markdown="span">**Detail**</summary>

- GPU digest-search kernels: 62× over CPU, 38% of it from Montgomery batch inversion
- Reduced an ECDSA (secp256k1) proof circuit 38%, from 2.58M to 1.59M constraints; hybrid Poseidon/Keccak commitment bridge
- Aperiodic (Spectre) tiling analysis in Rust at 142K–974K tiles, with PARI/GP algebraic number theory
- Rust EMV payment-card certificate reader over PC/SC NFC, detecting SDA/DDA/CDA card authentication
</details>

`2025 – 2026`
__AI applications__

<details markdown="1">
<summary markdown="span">**Detail**</summary>

- Agent-assisted property due diligence: seller-position analysis, comparable sales, financing; generalized into a reusable workflow
- Browser extension doing batched LLM classification of replies with throttling, plus a Grok search integration
- Client injection for a Rust LLM builder library; meeting-transcript knowledge base driven by Claude Code
</details>

## Patents

`2019`
Blockchain network communication management, [US20210243036A1](https://patents.google.com/patent/US20210243036A1/en)

## FOSS

`2008 – 2016`
__PHP__

- [Credited](https://www.php.net/manual/en/preface.php#contributors) documentation maintainer and voting [project member](https://people.php.net/frozenfire)
- Founded PHP Mentoring; contributed to Zend Framework; community management

`Last updated: October 2026`

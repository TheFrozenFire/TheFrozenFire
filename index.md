---
layout: cv
title: Justin Martin
---
# Justin Martin
Principal Engineer: AI systems, market data and execution, formal verification

<div id="webaddress">
<a href="mailto:justin@thefrozenfire.com">justin@thefrozenfire.com</a> | <a href="https://github.com/TheFrozenFire">github.com/TheFrozenFire</a> | BC, Canada
</div>

## Profile

Engineer with 15+ years of building production systems: real-time pricing and execution engines, high-volume messaging platforms, compliance automation and privacy-preserving identity. I write Rust and TypeScript, use numerical optimization and machine-checked proofs (Rocq) to show that systems do what they claim, and build agent tooling whose output is checked by a proof assistant or test suite rather than trusted.

### Specialized in

* Market data, pricing and execution optimization
* Numerical and convex optimization; constrained curve fitting
* Formal verification (Rocq, computer algebra, fuzzing)
* AI agent tooling with machine-checked output
* Data pipelines and distributed systems
* Security and privacy engineering (applied cryptography)

### Research interests

* Verified financial algorithms
* Mechanism design
* Privacy
* Adversarial interoperability
* Due process by design

## Experience

`Jan 2026 – Oct 2026`
__Reserve (ABC Labs)__

*Engineering Lead, Trading Infrastructure*

Reserve issues index-fund products on digital-asset markets.

- Led engineering for the routing and pricing engine that creates and redeems fund baskets across trading venues
- Rewrote the routing and pricing engine from first principles
- Did infrastructure and security work for the engine and its data services
- Explored formal verification of production contracts (unmerged)

`2022 – 2025`
__Keyring Network__

*Applied Cryptographer, R&D*

- Built a privacy-preserving KYC/AML protocol for regulated finance: users prove they passed verification without disclosing their identity data
- Deployed an MPC-TLS system for extracting identity documents from web sessions as verifiable evidence

<details markdown="1">
<summary><b>Proof systems, toolchain and messaging</b></summary>

- Wrote cryptographic proof primitives in Circom, TypeScript and Rust (compiled to WASM), including blinded RSA signing verified inside a proof circuit
- Built a circuit development toolchain in TypeScript
- Integrated TLS Notary for MPC-TLS web proofs
- Built a browser extension and an IPFS-based peer-to-peer protocol messaging layer (OrbitDB)

</details>

`2022 – 2023`
__eth.limo__

*Infrastructure Engineer, R&D*

- Maintained and improved a public gateway that serves decentralized websites over the regular web
- Built Chauffeur, a gateway users run locally for name resolution and content serving

`2021 – Aug 2022`
__Ethereum Foundation, Privacy & Scaling Explorations__

*Grants Coordinator, DevRel, R&D*

- Built a proof system for showing possession of a JSON Web Token from a social identity provider without revealing it
- Issued and supervised research grants; scouted talent and routed it to the ecosystem support program

<details markdown="1">
<summary><b>Open source, developer relations and program management</b></summary>

- Published open-source cryptographic proof primitives and supported developers adopting privacy tooling
- Bootstrapped product management processes for taking grant projects to production
- Supported infrastructure for compiling large proof circuits

</details>

`2013 – 2021`
__CallFire / EzTexting__

*Principal Engineer (DevOps, Compliance, Carrier Ops)*

- Built an automated messaging compliance system combining heuristics and machine learning to enforce industry content regulations
- Bootstrapped the Growth Engineering team, which used A/B testing to reduce churn and raise conversion and ARPU
- Refactored the core backend and trained the backend team in design patterns, testing and software lifecycle

<details markdown="1">
<summary><b>Compliance, fraud and operational intelligence</b></summary>

- Built an anti-spam, anti-fraud threat modeling engine
- Built an operational intelligence platform for reporting, monitoring and analysis of infrastructure and telephony operations
- Oversaw application security

</details>

<details markdown="1">
<summary><b>Platform, DevOps and carrier operations</b></summary>

- Joined through an acqui-hire as the SMS connectivity vendor
- Led DevOps: infrastructure orchestration, observability and incident response methodology; migrated to automated cloud provisioning and monitoring
- Built "Cloud Caller" provisioning automation, enabling a 20× increase in outbound calling capacity
- Oversaw platform architecture; refactored most of EzTexting's message processing, routing and origination software
- Ran carrier operations as Principal Engineer, Operations
- Delivered professional services for enterprise customers (custom call scheduling, routing and reporting)
- Wrote CallFire's public PHP SDK and did developer relations

</details>

`2013 – 2019`
__Roave__

*Lead Engineer*

- Built and ran SMSCloud, a high-throughput SMS gateway (SMSC) connecting businesses to carrier networks
- Ran agency operations, including contract negotiation and recruitment

`2012`
__MediaDevils__

*Lead Engineer*

- Built e-commerce sites for direct-response ("As Seen on TV") products, membership video streaming platforms and online learning platforms

## Selected projects

`2025 – 2026`
__AI systems__

- Built an MCP server for the Rocq proof assistant that surfaces diagnostics and hints to agents, so an agent's proof attempts are checked by the prover rather than trusted
- Built an agent-assisted research workflow for property due diligence (seller position, comparable sales, financing) and generalized it into a reusable template

<details markdown="1">
<summary><b>More</b>: LLM classification, agent knowledge bases, agent conventions</summary>

- Built a browser extension that classifies replies with an LLM in batches of 50, with throttling
- Built a meeting-transcript knowledge base maintained by a coding agent
- Wrote agent engineering conventions: domain-driven design, test-driven development, plans recorded as architecture decision records

</details>

`2025 – 2026`
__Formal methods for finance and law__

- Built a formal-verification harness and methodology: each property is stated as a proof and a counter-proof, confirmed by at least two independent tools, with Rocq proofs that use no axioms
- Applied it to a corpus reproducing historic financial-contract failures, including a reward over-distribution of about $80M and vault share-price manipulation
- Built a Rocq model that classifies legal contracts by how well they conform to law

<details markdown="1">
<summary><b>Compiler fixes, shared libraries, algebra</b></summary>

- Fixed C++ code generation bugs, added a contract-call proof rule and supported mapping-of-struct storage in my fork of a Solidity-to-Rocq compiler
- Maintained a shared Rocq library: modular arithmetic, quadratic fields Z[√d], cipher theory
- Analyzed the Spectre aperiodic tiling in Rust at 142K–974K tiles, with algebraic number theory in PARI/GP

</details>

`2025 – 2026`
__Performance and payments__

- Wrote GPU kernels for digest search, about 62× faster than the CPU version; batching field inversions with Montgomery's trick cut kernel time 38% (47.7ms to 29.4ms)
- Built a Rust reader for EMV payment-card certificates over NFC (PC/SC) that detects the card's authentication method (SDA, DDA, CDA)

`2025 – 2026`
__Cryptography__

<details markdown="1">
<summary><b>Proof circuits, unknown-order groups, cipher analysis</b></summary>

- Cut an ECDSA (secp256k1) signature-verification circuit from 2.58M to 1.59M constraints (38%)
- Formalized groups of unknown order in Rocq and computer algebra, including the textbook recovery of RSA factors from the private exponent and a catalog of key-generation leaks; sketched a proving system over RSA groups
- Built a Rocq laboratory for classical ciphers, with differential and linear analysis of S-boxes

</details>

## FOSS

`2008 – 2016`
__PHP__

- Maintained documentation as a [credited](https://www.php.net/manual/en/preface.php#contributors) contributor; voting [project member](https://people.php.net/frozenfire)
- Founded PHP Mentoring, contributed to Zend Framework and managed community channels

## Other

__Keywords__

Rust, TypeScript, Python, Go, PHP, SQL, Postgres, MySQL, MongoDB, Neo4j, Redis, Elasticsearch, Pandas, Jupyter, AWS, GCP, Cloudflare, Kubernetes, Terraform, Ansible, Grafana, Loki, LLM agents, MCP, machine learning, optimization, A/B testing, formal verification, Rocq

__Patent__

`2021`
Co-inventor, [US Patent 10,917,244](https://patents.google.com/patent/US10917244B1/en) (2021, CallFire): bridging SMS/telephony messaging and smart contracts

<p class="updated">Last updated October 2026</p>

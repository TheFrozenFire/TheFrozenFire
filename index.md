---
layout: cv
title: Justin Martin
---
# Justin Martin
Principal Engineer, Applied Cryptography, R&D

<div id="webaddress">
<a href="mailto:justin@thefrozenfire.com">justin@thefrozenfire.com</a> | <a href="https://github.com/TheFrozenFire">github.com/TheFrozenFire</a> | BC, Canada
</div>

## Profile

Seasoned software engineer with 15+ years of experience across infrastructure, data science, cryptography and full-stack development. I thrive on novelty, difficulty and the esoteric. I'm great at marshaling uncertainty and making complexity coherent. R&D and Growth Engineering are my specialty.

### Specialized in

* ZK cryptography
* Web proofs (zk-TLS)
* R&D and growth engineering
* Operational intelligence
* Formal verification
* Market data, pricing and execution optimization
* AI agent tooling with machine-checked output

### Research interests

* Sybil resistance
* Cryptoeconomics
* Privacy
* Adversarial interoperability
* Due process by design

## Experience

`Jan 2026 – Oct 2026`
__Reserve (ABC Labs)__

*Lead Engineer, DeFi Engineering*

Reserve issues index-fund products on digital-asset markets.

- Developed and maintained the core product, a hyper-optimized DeFi transaction solver
- Built a multi-chain DeFi market data engine
- Developed a novel graph-based convex optimization algorithm for multi-input, multi-output order flow solving
- Formal verification of ETL, optimization algorithms, application security, smart contracts
- Infrastructure management and security
- Established fully agentic development practices, guard rails, deployment processes, observability

`2022 – 2025`
__Keyring Network__

*Applied Cryptographer, R&D*

- Developed a ZK KYC/AML protocol from the ground up for regulated finance: users prove they passed verification without disclosing their identity data
- Deployed an MPC-TLS solution for extracting identity documents from web sessions as verifiable evidence
- Developed and deployed Circom circuits; Rust-based WASM development; Solidity smart contract development

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

- Improved and maintained the core ENS Gateway, which serves decentralized websites over the regular web
- Developed Chauffeur, a user-local ENS Gateway for name resolution and content serving
- R&D on IPFS, ENS and bridging decentralized protocols with the traditional internet

`2021 – Aug 2022`
__PSE Team @ Ethereum Foundation__

*Grants Coordinator, DevRel, R&D*

- Developed a ZK prover for JSON Web Tokens: proves possession of a token from a social identity provider without revealing it
- Issued and supervised grant projects; scouted talent and routed prospects to ESP projects

<details markdown="1">
<summary><b>Open source, developer relations and program management</b></summary>

- Published open-source ZK cryptographic primitives
- Ecosystem developer relations, supporting developers adopting privacy tooling
- Bootstrapped product management processes for taking grant projects to production
- Supported infrastructure for compiling large proof circuits

</details>

`2013 – 2021`
__CallFire / EzTexting__

*Principal Engineer (DevOps, Compliance, Carrier Ops)*

- Developed a heuristic-and-ML messaging compliance system to enforce industry content regulations
- Bootstrapped the Growth Engineering team; drove a major decrease in churn and increases in conversion and ARPU through A/B testing
- Total refactor of the core backend codebase; instituted engineering best practices and trained the team on design patterns, testing methodologies and software lifecycle

<details markdown="1">
<summary><b>Compliance, fraud and operational intelligence</b></summary>

- Developed anti-spam, anti-fraud threat modeling
- Developed an Operational Intelligence platform producing reporting, monitoring and analysis of infrastructure and telephony operations
- Oversaw platform architecture and application security

</details>

<details markdown="1">
<summary><b>Platform, DevOps and carrier operations</b></summary>

- Joined through an acqui-hire as the SMS connectivity vendor
- Acted as DevOps lead: infrastructure orchestration, observability and incident response methodology; migrated to automated cloud provisioning and monitoring
- Built "Cloud Caller" provisioning automation, enabling a 20× increase in outbound calling capacity
- Oversaw platform architecture; refactored most of EzTexting's message processing, routing and origination software
- Ran carrier operations as Principal Engineer, Operations
- Delivered professional services for enterprise customers (custom call scheduling, routing and reporting)
- Wrote CallFire's public PHP SDK and did developer relations

</details>

`2013 – 2019`
__Roave__

*Lead Engineer*

- Developed and managed SMSCloud, a high-throughput telephony SMSC connecting businesses to carrier networks
- Oversaw operations of a software development agency (contract negotiations, recruitment)

`2012`
__MediaDevils__

*Lead Engineer*

- Ecommerce sweatshop
- Built numerous custom e-commerce websites for "As Seen on TV" products
- Built custom membership video streaming platforms
- Built specialized social network and online learning platforms

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

*Documentation Maintainer, Community Manager*

- Maintained documentation as a [credited](https://www.php.net/manual/en/preface.php#contributors) contributor; voting [project member](https://people.php.net/frozenfire)
- Founded PHP Mentoring, contributed to Zend Framework and managed community channels (IRC, Reddit, etc.)

## Other

__Tech stack__

Rust, WASM, TypeScript · Circom, Solidity, EVM, IPFS · GCP, AWS, Cloudflare · Elasticsearch, Redis · MySQL, Postgres · Python, Pandas, Jupyter · Ansible, Terraform, Kubernetes

__Keywords__

Rust, WASM, TypeScript, Circom, Solidity, Python, Go, PHP, SQL, Postgres, MySQL, MongoDB, Neo4j, Redis, Elasticsearch, Pandas, Jupyter, AWS, GCP, Cloudflare, Kubernetes, Terraform, Ansible, Grafana, Loki, LLM agents, MCP, machine learning, optimization, A/B testing, formal verification, Rocq

__Patent__

`2021`
Co-inventor, [US Patent 10,917,244](https://patents.google.com/patent/US10917244B1/en) (2021, CallFire): bridging SMS/telephony messaging and smart contracts

<p class="updated">Last updated November 2026</p>

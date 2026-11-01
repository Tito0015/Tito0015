Hi, I'm Tarek 👋

Founder & Lead Architect @ Veraptos — building the universal rule compiler for AppSec ("Terraform for Threat Detection"). Write abstract vulnerability logic once (CPG/AST) $\rightarrow$ compile & lower directly into native CodeQL | Semgrep | Opengrep | Nuclei | YARA | Sigma | Hexens Glider rules across Web2 & Web3.

⚡ Bridging abstract threat modeling with verified, native detection across enterprise AppSec and Web3 toolchains.
---
### 🔄 The Meta-Compiler Architecture

```text
 ┌────────────────────────────────────────────────────────┐
 │                Abstract Threat Invariant               │
 │       (Write once: Natural Language, YAML, or Code)    │
 └───────────────────────────┬────────────────────────────┘
                             │
                             │ (1) AI translation
                             ▼
 ┌────────────────────────────────────────────────────────┐
 │                    Agentic AI Layer                    │
 │               Translation & Graph Mapping              │
 └───────────────────────────┬────────────────────────────┘
                             │
                             │ (2) Standardized Logic
                             ▼
 ┌────────────────────────────────────────────────────────┐
 │         Veraptos Lowering Engine (CPG / AST)           │
 │            (Closed Core / Proprietary IR)              │
 │                                                        │
 │   • High-Fidelity Graph Traversals                     │
 │   • Feature Extraction & AST Mapping                   │
 │   • Deterministic Rule Compilation & Optimizers        │
 └───────────────────────────┬────────────────────────────┘
                             │
     ┌───────┬───────┬───────┼───────┬───────┬───────┬───────┬───────┐
     │       │       │       │       │       │       │       │       │
     ▼       ▼       ▼       ▼       ▼       ▼       ▼       ▼       ▼
 ┌───────┐┌───────┐┌───────┐┌───────┐┌───────┐┌───────┐┌───────┐┌───────┐┌───────┐
 │CodeQL ││Semgrep││Opengp ││ Joern ││Nuclei ││Glider ││Slither││ YARA  ││ Sigma │
 └───────┘└───────┘└───────┘└───────┘└───────┘└───────┘└───────┘└───────┘└───────┘
```
> **Architecture Note:** The pipeline cleanly separates intent from enforcement. LLM components are restricted to front-end invariant drafting from natural language or specifications. The closed-core Veraptos engine then takes over: validating candidate logic against Code Property Graph (CPG) semantics, checking reachability, and deterministically compiling the invariant into syntax-checked, native queries with zero manual refactoring.
---
### Upstream Contributions & Veraptos Validation

#### 1. Core Toolchain & Engine Patches (Found & Authored via Veraptos R&D)

*Contributions to upstream engines made while developing, stress-testing, and improving intermediate representation lowering:*

* **Joern Dataflow Core** (`joernio/joern`): [#6358](https://github.com/joernio/joern/pull/6358) - Core REACHING_DEF path drop fixes for nested structs & pointer derefs `[Merged Oct 4, 2026]`


* **Joern CPG Engine** (`joernio/joern`): [#6298](https://github.com/joernio/joern/pull/6298) - C2CPG double-pointer dataflow reachability fixes `[Merged Sep 24, 2026]`


* **Joern CPG Linker** (`joernio/joern`): [#6355](https://github.com/joernio/joern/pull/6355) - Link dynamic pointer calls to method refs in conditional receivers `[Merged Oct 9, 2026]`


* **Joern Ruby CPG** (`joernio/joern`): [#6440](https://github.com/joernio/joern/pull/6440) - rubysrc2cpg: emit STATIC modifier for singleton methods `[Merged Oct 21, 2026]`


* **Opengrep CLI** (`opengrep/opengrep`): [#844](https://github.com/opengrep/opengrep/pull/844) - fix(cli): make --test work on Windows `[Merged Oct 20, 2026]`



---

#### 2. Detections & Rule Lowering (Veraptos Compiled & Verified)

*Native rules and query artifacts compiled from abstract threat invariants down to target scanner syntaxes:*

* **CodeQL** (`github/codeql`): [#22438](https://github.com/github/codeql/pull/22438) - C++ MMIO un-sanitized memcpy query `[Merged Sep 21, 2026]`


* **Semgrep** (`semgrep/semgrep-rules`): [#4052](https://github.com/semgrep/semgrep-rules/pull/4052) - TypeScript MCP command injection & SSRF `[Merged Sep 21, 2026]`


* **Nuclei** (`projectdiscovery/nuclei-templates`): [#17286](https://github.com/projectdiscovery/nuclei-templates/pull/17286) - Harden CVE-2025-29927 against middleware-bypass false positives `[Merged Oct 13, 2026]`


* **Nuclei** (`projectdiscovery/nuclei-templates`): [#17007](https://github.com/projectdiscovery/nuclei-templates/pull/17007) - changedetection.io LFI non-destructive refactor & cleanup (CVE-2024-51483) `[Merged Oct 8, 2026]`


* **Nuclei** (`projectdiscovery/nuclei-templates`): [#17171](https://github.com/projectdiscovery/nuclei-templates/pull/17171) - Ray RCE (CVE-2025-62593) `[Merged Sep 24, 2026]`



---

#### 3. Web3 & Glider (Hexens) Query Suite (`Tito099` - Invariant Detection)

Author of 7 automated Solidity AST invariant detection queries on Glider IDE:

* `[+]` **Decimal Precision Loss via Scale-to-Single/Dual-Vault** `[Pending merge - Aug 30, 2026]`


* `[+]` **Native Asset Double-Spend via settle/sweep logic** `[Pending update - Aug 6, 2026]`


* `[+]` **Duplicate Signature Quota Bypass via reuse** `[Pending update - Aug 5, 2026]`


* `[+]` **Risc0 ZK Unbound Journal Digest** `[Pending update - Aug 4, 2026]`


* `[+]` **Merkle Shift-Compose Overflow via verifier logic** `[Pending update - Aug 4, 2026]`


* `[+]` **Governance Check-Effects-Interactions (CEI)** `[Pending merge - Aug 3, 2026]`


* `[+]` **ABI Smuggling - Fixed-Offset Calldata** `[Pending merge - Jun 22, 2026]`

---

### 🔬 Featured Projects & Technical Analysis

* ⚡ **[cpg-nuclei-compiler](https://github.com/Tito0015/cpg-nuclei-compiler)** [![Marketplace](https://img.shields.io/badge/Marketplace-v1.0.0-blue?logo=github)](https://github.com/marketplace/actions/cpg-nuclei-compiler-verification-harness): Deterministic Joern CPG-to-Nuclei YAML compiler & Docker verification harness. Available as a **[v1 GitHub Action](https://github.com/marketplace/actions/cpg-nuclei-compiler-verification-harness)** for automated non-destructive template testing in CI.
* 📖 **Medium Article:** [CPG Compilation vs. LLM AI Generation: Empirical Analysis of CVE-2025-62593 Rule Accuracy](https://medium.com/@mhiritarek/cpg-compilation-vs-llm-ai-generation-empirical-analysis-of-cve-2025-62593-rule-accuracy)
---

### 📫 Connect
- **LinkedIn:** [in/tarek-mhiri](https://www.linkedin.com/in/tarek-mhiri/)
- **X / Twitter:** [@TITO088](https://x.com/TITO088)
- **Medium:** [@mhiritarek](https://medium.com/@mhiritarek)
---
*Self-funding the Veraptos R&D floor one pizza 🍕 at a time while lowering CPG ASTs into multi-format threat rules.*
  

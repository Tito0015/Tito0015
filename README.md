Hi, I'm Tarek 👋

Founder & Lead Architect @ Veraptos — building the universal rule compiler for AppSec ("Terraform for Threat Detection"). Write abstract vulnerability logic once (CPG/AST) $\rightarrow$ compile & lower directly into native CodeQL | Semgrep | Opengrep | Nuclei | YARA | Sigma | Hexens Glider rules across Web2 & Web3.

⚡ The upstream contributions below were compiled, lowered, and verified using the Veraptos engine.
---
### 🔄 The Meta-Compiler Architecture

```text
┌─────────────────────────────────────────┐
│        Abstract Threat Invariant        │
└────────────────────┬────────────────────┘
                     │ (Write once: CPG/AST)
                     ▼
┌─────────────────────────────────────────┐
│        Veraptos Lowering Engine         │
└────┬──────────┬──────────┬──────────┬───┘
     │          │          │          │
┌────▼───┐ ┌────▼───┐ ┌────▼───┐ ┌────▼───┐
│CodeQL  │ │Semgrep │ │ Nuclei │ │ Glider │ + YARA/Sigma
└────────┘ └────────┘ └────────┘ └────────┘
```

<p align="center">

```text
┌─────────────────────────────────────────┐
│        Abstract Threat Invariant        │
└────────────────────┬────────────────────┘
                     │ (Write once: CPG/AST)
                     ▼
┌─────────────────────────────────────────┐
│        Veraptos Lowering Engine         │
└────┬──────────┬──────────┬──────────┬───┘
     │          │          │          │
┌────▼───┐ ┌────▼───┐ ┌────▼───┐ ┌────▼───┐
│CodeQL  │ │Semgrep │ │ Nuclei │ │ Glider │ + YARA/Sigma
└────────┘ └────────┘ └────────┘ └────────┘
</p>
```
---
### 🛡️ Upstream Proof-of-Work & Merged Contributions

* **CodeQL** ( `github/codeql` ): [#22438](https://github.com/github/codeql/pull/22438) — C++ MMIO un-sanitized memcpy query **[Merged Sep 21, 2026]**
* **Semgrep** ( `semgrep/semgrep-rules` ): [#4052](https://github.com/semgrep/semgrep-rules/pull/4052) — TypeScript MCP command injection & SSRF **[Merged Sep 21, 2026]**
* **Nuclei** ( `projectdiscovery/nuclei-templates` ): [#17171](https://github.com/projectdiscovery/nuclei-templates/pull/17171) — Ray RCE (CVE-2025-62593) **[Merged Sep 24, 2026]**
* **Joern CPG Engine** ( `joernio/joern` ): [#6298](https://github.com/joernio/joern/pull/6298) — C2CPG double-pointer dataflow reachability fixes **[Merged Sep 24, 2026]**
---

### ⛓️ Web3 & Glider (Hexens) Query Suite (`Tito099` — Pending Update)

Author of 7 automated Solidity AST invariant detection queries on Glider IDE:

* 🔵 **Decimal Precision Loss via Scale-to-Single/Dual-Vault** *(Pending merge — 30 Aug 2026)*
* 🔵 **Native Asset Double-Spend via settle/sweep logic** *(Pending update — 6 Aug 2026)*
* 🔵 **Duplicate Signature Quota Bypass via reuse** *(Pending update — 5 Aug 2026)*
* 🔵 **Risc0 ZK Unbound Journal Digest** *(Pending update — 4 Aug 2026)*
* 🔵 **Merkle Shift-Compose Overflow via verifier logic** *(Pending update — 4 Aug 2026)*
* 🔵 **Governance Check-Effects-Interactions (CEI)** *(Pending merge — 3 Aug 2026)*
* 🔵 **ABI Smuggling — Fixed-Offset Calldata** *(Pending merge — 22 Jun 2026)*

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
  

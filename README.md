# Hyunwoo Kim · 김현우

**Blockchain Core Engineer | Transaction correctness · Incident response · Protocol validation**

I build transaction, fee, settlement, and refund logic for Cosmos-based chains. At Gurufin, I work across core implementation, source-level incident resolution, and validation of protocol changes.

## What I bring

- **Cross-chain transaction correctness.** Owned FX core development for a public testnet spanning **7 chains**, including settlement and failure refunds. Integrated it with wallet and explorer services and supported deployment and monitoring. [Refund tracking](https://github.com/gurufinglobal/guru/pull/66) · [Subsequent FX integration](https://github.com/gurufinglobal/guru/pull/75)
- **Source-level incident resolution.** Traced missing EVM receipt logs to an upstream storage-format change, fixed RPC decoding, and deployed the fix to live testnet Sentry nodes. Also implemented bounded gas/fee recovery for failing relayers, with backups, cooldowns, and rollback.
- **Execution and policy validation.** Reduced shared fee-account contention, improving median independent-transfer throughput by **3.3× in an in-memory execution/commit benchmark**, excluding network consensus and persistent storage. Checked sequential/parallel state equivalence and used same-account transfers as a control. Also contributed fee and validator policies to the public mainnet release candidate. [Fee accounting](https://github.com/gurufinglobal/guru/pull/78) · [Policy boundaries](https://github.com/gurufinglobal/guru/pull/87)
- **Protocol security research.** Analyzed consensus, IBC, and state/accounting failure paths. The **Cosmos project team acknowledged the technical validity of 8 reports**: **2 Medium Confirmed** and **6 duplicate or previously known issues**, submitted through Immunefi and project-team review.

## Background

Master's degree in Blockchain Computing and Cryptoeconomics, Hanyang University (2025), with research in BFT execution, optimistic concurrency control, and sharding. I also built multi-chain RPC integrations and wallet backend APIs during graduate research collaborations.

**Core stack:** Go · Cosmos SDK / EVM · CometBFT · IBC / Hermes

## Experience and case studies

- **Résumé:** [English](https://app.notion.com/p/4087ff6b6c108104a0f5c8cc50513fb2) · [한국어](https://app.notion.com/p/4087ff6b6c1081dc99a7da83e5637bdc) — roles and outcomes.
- **Portfolio:** [English](https://app.notion.com/p/4087ff6b6c1081da8ee5c1b24e507279) · [한국어](https://app.notion.com/p/4087ff6b6c1081ec9e07ce1fc1e6c46f) — problems, decisions, and validation.

Public work contributions: [KimHyunwoo-99](https://github.com/KimHyunwoo-99). This is my personal profile.

[Email](mailto:rmrehd604@gmail.com)

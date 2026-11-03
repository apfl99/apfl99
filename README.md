# Hyunwoo Kim · 김현우

**Blockchain Core Engineer | Protocol Security · Transaction Correctness · Incident Response**

[Work contributions: KimHyunwoo-99](https://github.com/KimHyunwoo-99) · [Email](mailto:rmrehd604@gmail.com)

I work on Go/Cosmos core development at Gurufin, focusing on protocol failure analysis and cross-chain settlement and refund logic. My earlier testnet work included source-level diagnosis, regression testing, and deployment.

## Core strengths

- **Protocol security research.** Investigate consensus, IBC, and state/accounting failure paths using controlled multi-validator experiments. Project reviewers acknowledged **8 reports as technically valid: 2 confirmed at Medium severity through Immunefi; 6 classified as duplicate or previously known**. Reports were submitted through Immunefi and directly to the project team, with source analysis, case-specific reproductions, impact, recovery, and proposed corrections.
- **Cross-chain transaction correctness.** Primary developer for FX logic on a public testnet spanning **7 chains**, including quotes, swaps, fees, settlement, and refunds. Collaborated with wallet, explorer, and DevOps engineers on integration and operations. In a subsequent testnet rebuild, integrated FX with IBC refund handling and verified transfers, balances, fees, and acknowledgement-based settlement across **3 chains**.
- **Source-level incident resolution.** Restored missing EVM receipt logs by tracing an upstream storage-format change, fixing RPC decoding, and deploying to live testnet sentry nodes. Corrected FX accounting-state errors and tested invariants and failure paths. Automated bounded gas/fee recovery for selected testnet relayers, with backups, cooldowns, and rollback.
- **Execution and policy validation.** Reduced shared fee-account contention using transaction-local fee records and block-end settlement. Achieved approximately **3.3× the baseline median throughput** for independent-account transfers in an **in-memory execution/Commit benchmark: 4 workers, 100 signed MsgSend transactions per block, excluding network consensus and persistent storage**. Compared balances, nonces, and AppHash with sequential execution and used same-account transfers as a control. Also implemented fee and validator policies for Guru v2.1.0-rc.1; the current v2.1 testnet and mainnet have not launched.

## Code and validation evidence

| Work | Public code | What to review |
| --- | --- | --- |
| FX settlement and refund recovery | [PR #75](https://github.com/gurufinglobal/guru/pull/75) · [Earlier refund tracking, #66](https://github.com/gurufinglobal/guru/pull/66) | Custody boundaries, atomic accounting, asynchronous refunds, and failure recovery. |
| Parallel fee settlement | [PR #78](https://github.com/gurufinglobal/guru/pull/78) | Deterministic state comparisons, same-block visibility, and paired workload benchmarks. |
| Policy activation safety | [PR #87](https://github.com/gurufinglobal/guru/pull/87) | Committed consensus parameters, activation boundaries, and missed gas-price schedules. |

[Engineering evidence and validation scope](docs/engineering-evidence.md) records contribution boundaries, benchmark conditions, and the validation evidence available in these PRs.

## Background

Master's degree in Blockchain Computing and Cryptoeconomics, Hanyang University (2025), with research in BFT execution, optimistic concurrency control, and sharding. I also built multi-chain RPC integrations and wallet backend APIs during graduate research collaborations.

**Core stack:** Go · Cosmos SDK / EVM · CometBFT · IBC / Hermes


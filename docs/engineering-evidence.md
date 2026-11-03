# Engineering evidence and validation scope

This page connects my [résumé](https://app.notion.com/p/4087ff6b6c108104a0f5c8cc50513fb2) to selected public engineering work at Gurufin. The three PRs below were authored through my [work account, KimHyunwoo-99](https://github.com/KimHyunwoo-99), and are merged. I use [apfl99](https://github.com/apfl99) as my personal account.

## FX settlement and refund recovery

[PR #75](https://github.com/gurufinglobal/guru/pull/75) integrates the FX exchange layer and IBC refund handling. My focus was exchange policy, custody and accounting boundaries, packet execution, and bounded refund recovery.

The PR also incorporates collaborators' Oracle and runtime work. Its full diff is broader than my individual FX contribution. The commit history and the PR's review order identify the relevant modules.

Useful evidence:

- Exchange and reserve accounting, atomic state transitions, refund liabilities, and duplicate-callback handling.
- Tests for custody boundaries, rollback, refund state transitions, and two-chain acknowledgement and timeout paths.
- An explicit limitations section and a file-by-file review guide.

The public Validation checklist records `git diff --check` as complete; the listed test, lint, and generation commands remain unchecked. Test code is available, but that checklist should not be read as a record that every listed command passed.

The seven-chain testnet operation described in my résumé and the later three-chain FX integration checks are separate scopes.

## Parallel fee settlement

[PR #78](https://github.com/gurufinglobal/guru/pull/78) removes the shared per-transaction fee-collector write while retaining real fee-payer debits. Transaction-local records are reconciled at block end.

The public tests cover sequential/parallel state equivalence, same-block visibility, mixed Cosmos/EVM execution, and fee deduction behavior. The [benchmark source at the PR revision](https://github.com/gurufinglobal/guru/blob/3879c6ee561c4de083b844faa1b87339d5790740/app/blockstm_cosmos_virtual_fee_benchmark_test.go) includes independent-payer and same-account workloads.

The result summarized in my résumé has this scope:

| Item | Measurement scope |
| --- | --- |
| Result | Approximately 3.3× the baseline median throughput for transfers from independent accounts |
| Configuration | 4 workers; 100 signed MsgSend transactions per block |
| Timed path | In-memory execution/FinalizeBlock and Commit |
| Excluded | Network consensus and persistent storage |
| Correctness checks | Balances, nonces, and AppHash compared with sequential execution |
| Control workload | Transfers from the same account |

The PR contains the implementation and benchmark harness, but does not publish the 3.3× result table or its raw runs. Its example command uses a different configurable workload: 10 workers and 1,000 transactions. The reported result is specific to the measured configuration and is not a network-wide TPS claim.

## Policy activation safety

[PR #87](https://github.com/gurufinglobal/guru/pull/87) uses committed consensus parameters for Oracle Vote Extension activation and handles future, due, and missed minimum-gas-price schedules explicitly. It aligns Genesis validation with the initial block height.

The PR documents successful tests on a dedicated IDC runner, including root/Oracle test suites, race checks, module verification, focused regressions, and opt-in four-validator acceptance checks. It distinguishes these checks from overall release approval and records known boundaries.

<details>
<summary>Public CI status at the PR revision, checked November 3, 2026</summary>

The 12 check runs show 9 successful, 2 failed, and 1 skipped result. The failed [root](https://github.com/gurufinglobal/guru/actions/runs/33580514520/job/100093610818) and [Oracle](https://github.com/gurufinglobal/guru/actions/runs/33580514520/job/100093610676) Govulncheck jobs stopped during tool installation: Govulncheck v1.7.0 requires Go 1.25 or later, while the runner used Go 1.23.8 with `GOTOOLCHAIN=local`.

Those failures are toolchain compatibility errors, not reported vulnerability findings. The public race/fuzz job was skipped; the separate IDC race-test result is documented in the PR body. The public CI record should not be described as entirely green.

</details>

# Verification and evidence guide

## Evidence levels

| Evidence | What happened | Boundary |
| --- | --- | --- |
| Real API sample, October 22, 2026 | DeepSeek Flash changed a fresh sample; an independent clean-checkout test run passed. | Direct built-in runner, no tenant queue/VM/native CLI/publication. |
| Deterministic controls, same sample | Correct fixture passed, broken calculation failed, excluded test edits were refused. | Real Git/tests/policy, fixed candidates rather than model behavior. |
| Console screenshots and GIF | Existing interface displayed saved results with replay labels. | Illustrative source/account metadata; no live workstation. |
| Historical native trials, October 2–9 | Authenticated CLI sessions and Codex task/file/result delivery exercised in Linux services. | Private dated records; public package does not independently reproduce them. |
| Source regression snapshot | Last recorded full backend run: 1540 passed, 22 skipped, 5 live deselected. | Maintainer-reported development evidence, not a runnable public suite or production certification. |
| Installed CP1 | Combined native execution, independent verification and exact application. | Not complete; retired environment must be configured before another acceptance run. |

The source regression and native-history statements come from private development
records. The public package includes the sample's actual artifacts, not the full
backend suite or raw historical native journals.

## The real sample input

The [sanitized run record](../evidence/live-run.json) contains the exact goal,
scope and exclusions. The agent was asked to repair `apply_discount` in
`src/pricing.py`, inspect the source and acceptance tests first, modify only that
source file and run `python -I -B -m unittest discover -s tests -v`.

| Requirement | Observable expected behavior |
| --- | --- |
| REQ-001 | Zero discount preserves the price. |
| REQ-002 | A 20% discount on 1000 cents yields 800. |
| REQ-003 | Full discount yields zero; zero price remains zero. |
| REQ-004 | Fractional cents round down: 199 with 10% discount yields 179. |
| REQ-005 | Negative price or discount outside 0–100 raises `ValueError`. |

These requirements were fixed by the demonstration, not discovered or certified
complete by an autonomous specification agent. The real model run used six rounds
at most and a 180-second agent deadline. Recorded timestamps are
11:59:12.513594Z–11:59:19.562083Z on October 22, 2026; this is one observation,
not a latency benchmark, SLA or cost estimate.

## What the verifier independently observed

The [actual patch](../evidence/live-change.diff) changes only `src/pricing.py`.
It subtracts the percentage and adds invalid-input checks. The verifier's receipt
records a secret scan, scope validation, patch application at the frozen base and
native test execution. The [test log](../evidence/live-tests.log) records five
passing acceptance tests; the grade is `verified_basic`.

The original sample source/tests/HEAD were preserved. No candidate was published
or applied to a user project. The agent's [own response](../evidence/agent-response.md)
is retained separately from the independent test log. There was no semantic
reviewer in this run. The receipt's `merge_eligible` value is local sample evidence,
not proof that a merge, deployment or workstation application occurred.

## Refusal behavior

The [control records](../evidence/controls.json) retain three fixed candidates:

1. A correct implementation establishes that the real verification path can pass.
2. A deliberately incorrect discount establishes that acceptance tests can fail.
3. An excluded test-file edit establishes scope refusal before candidate tests run.

Together these show a permitted case and two different failure classes. They do
not establish that every malicious change will be caught or that the live model
tried to tamper with tests. Refusing an out-of-scope patch does not establish an
OS sandbox around the process that produced it.

## Checking the public artifacts

The [capture manifest](../evidence/manifest.json) contains SHA-256 values for the
saved evidence, original screenshots and GIF. This capture manifest is retained
with the files; it does not hash itself. The showcase folder is copied directly
to the separate public repository when the owner triggers publication.

The patch's SHA-256 is:

```text
7fe04967b2c6cd00af6e4d5ff80dcfa51ecbdbbf1493a6be581e0bd23b6ed506
```

Hash comparisons use original bytes, including patch context and log line endings.
JSON viewers and editors can change those bytes when saving. Git attributes retain
the captured evidence as binary-preserved text. Publication commits only this
folder's files in the separate showcase repository, with no private source history.

Local executable/home paths were redacted from the exported receipt. Its original
private evidence digest is retained for reference. Sanitization means it is
presentation evidence, not a replayable runtime authorization receipt. A matching
hash proves consistency with the supplied manifest, not external certification of
the run. Public readers cannot audit the private verifier implementation here.

## Media provenance

Nine JPEGs are browser captures. Six of those views form a 24-second GIF montage,
with an added caption band stating recorded evidence, console replay and no live
VM. The montage contains no live cursor interaction, simulated execution timeline
or AI-generated UI frames. The complete evidence screenshot is also provided at
full height for inspection. Recorded console data is not a production queue.

See [limitations](limitations.md) for what remains unproven.

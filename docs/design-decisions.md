# Design decisions and tradeoffs

These are explanations of implemented choices, not a backlog of promised
features. Read the [architecture](architecture.md) for component relationships.

## 1. A small task contract before agent execution

**Problem:** A conversation can leave the intended file scope, readiness and
approval ambiguous. A powerful model does not remove that ambiguity.

**Choice:** Freeze a goal, allowed scope, exclusions, readiness and risk, with
project/base/context identity at dispatch. Clarification and reviewed acceptance
precede mutation when required.

**Tradeoff:** More explicit state than forwarding the latest chat message to a
CLI. The benefit is a concrete contract for policy and verification. A well-formed
contract still cannot establish that all business requirements are complete.

## 2. Separate Git worktrees for attempts

**Problem:** Two attempts modifying the main checkout make attribution and safe
comparison difficult, especially after failure or cancellation.

**Choice:** Give each attempt its own worktree anchored at a frozen base. Keep
the original project as the comparison/application target. Independent verification
uses another clean checkout instead of trusting the implementer's working state.

**Tradeoff:** Extra checkout/storage/lifecycle work. Git isolation does not isolate
OS processes, credentials or the network. The direct API example uses a trusted
sample; hosted hostile execution would need a separate security boundary.

## 3. Verification owned outside the implementer

**Problem:** An agent can claim a test passed, change the tests, or test a workspace
different from the eventual patch.

**Choice:** Collect actual diff bytes, validate scope, reapply against the base and
run the verifier's checks. Bind the receipt to the base and patch identity. Keep
implementer prose as supplementary evidence rather than the verdict.

**Tradeoff:** Duplicate test execution and extra latency. Mechanical checks find
classes of defects but cannot prove arbitrary behavior, requirements completeness
or production safety. `verified_basic` is a bounded grade, not a release approval.

## 4. One provider gateway and replaceable runner adapters

**Problem:** Vendor SDK types and model-specific assumptions can spread through
task, policy and persistence code. Native subscription sessions and API models
also have different runtime/authentication contracts.

**Choice:** Keep provider SDKs behind the gateway/provider boundary. Native
runner adapters normalize execution separately; the built-in API runner uses the
same gateway for tool calls. Model quality requirements apply before preference
and quota ranking.

**Tradeoff:** An abstraction cannot make all providers identical. Authentication,
tool support, native session behavior and error normalization still need real
connector-specific proof. This showcase exercises one API provider/model.

## 5. Persistent workstation before disposable job containers

**Problem:** Recreating an environment for every job complicates native login
portability, project continuity and evidence recovery before their value is proven.

**Choice:** Keep user login/project state in a persistent tenant workstation and
isolate attempts with worktrees. Treat ephemeral execution containers as deferred
design work. Verification containers serve a separate operator-owned purpose.

**Tradeoff:** Persistent environments need maintenance and have nonzero idle cost.
Worktrees alone do not provide tenant security isolation. This is a one-owner
sequential-job delivery baseline, not automatic SaaS VM provisioning.

## 6. Durable ownership and idempotent evidence delivery

**Problem:** If an upload acknowledgement is lost, blindly retrying the whole job
can run a paid agent twice. Restarted processes may also have uncertain ownership.

**Choice:** Persist job attempts/leases and tenant receipt/execution journals.
Retry frozen evidence uploads, not uncertain agent execution. Preserve typed
review-required states and repair projections only from matching saved evidence.

**Tradeoff:** More state transitions and recovery code. The system intentionally
stops for review where it cannot prove ownership or stop status. Availability is
sacrificed at that boundary instead of silently creating competing attempts.

## 7. Separate result, verification, publication and application

**Problem:** “Agent finished”, “tests passed”, “commit published” and “user project
updated” are different facts. A stale target branch can invalidate an otherwise
correct candidate.

**Choice:** Retain exact result/verification identity and gate subsequent Git
operations against frozen revisions. Native report delivery can finish unverified;
code application needs its separate evidence/acknowledgement path.

**Tradeoff:** More visible intermediate/review states. Local proof of these paths
does not substitute for the remaining installed end-to-end CP1 trial. No GitHub
push or deployment is implicit in the product's publication terminology.

## 8. Source-private portfolio with public inspection material

**Problem:** Freezing a PoC should preserve engineering value without releasing
the implementation or taking on a public product support obligation.

**Choice:** Maintain a curated public payload inside the private development repo.
Publish only documentation, recorded media and sanitized synthetic-example
evidence directly under `showcase/`. When explicitly triggered, copy that folder
into the separate showcase repository and commit/push changes. Keep publication
as a small workflow; there is no ZIP build or custom export framework. Private
Git parents and repository metadata are not copied.

**Tradeoff:** Public readers can inspect the patch, logs, hashes and explanations,
but cannot audit the application implementation or independently reproduce the
entire product from this repository. Hashes establish artifact consistency, not
independent authorship or authenticity. The GIF is a labelled evidence montage,
not a live recording. Feature work is frozen unless concrete demand justifies it.

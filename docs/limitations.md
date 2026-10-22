# Limitations and project status

**Status: engineering proof of concept; portfolio delivery and feature freeze.**

The source remains private. This repository is documentation, recorded media and
sanitized example evidence. It is not an installable application, an open-source
SDK or a customer-facing hosted service.

## Proven sample versus broader system

The included API example is a small deterministic problem with a real model
implementation and real independent checks. It does not establish reliability
across arbitrary repositories, languages, commands, long-running jobs or ambiguous
business requirements. Five passing sample checks are not a comprehensive
correctness guarantee. Deterministic refusal controls test specific behavior
classes, not the live model's motives or all adversarial behavior.

The built-in runner's worktree is a version-control boundary, not a security
sandbox. Its command tool uses the operator environment. Prompt constraints are
not enforced network/credential isolation. An untrusted multi-tenant execution
service would need a separately proven process/container/VM boundary.

## Installed native acceptance remains open

Earlier Linux trials exercised authenticated native CLI sessions and job/result
delivery. The owner removed the WSL/Docker environment on October 14, 2026.
Screenshots replay saved evidence and do not recreate that environment.

The complete installed acceptance milestone, CP1, still requires independently
verified code and exact publication/application through the configured services.
Local tests of individual components and historical native delivery are separate
evidence. No current VM, automatic environment creation, embedded subscription
login or fresh installed-native trial is included here.

## Deployment and operational limits

- Persistent workstation plus isolated worktrees is the near-term baseline;
  per-job disposable environments and zero-idle-cost execution are deferred.
- No self-service signup/VM provisioning, production billing, hosted recovery or
  production SSO is claimed. Browser accounts are operator-provisioned.
- SQLite/fenced attempts and durable journals improve local ownership/recovery;
  remaining file-backed state and process-local publication coordination prevent
  a claim of complete multi-process/multi-node production persistence.
- Native cancellation and local process cleanup cannot prove remote/provider-side
  stop. Unknown ownership/stop status requires review, not automatic redispatch.
- Optional workstation verification, BASIC promotion, control Git publication and
  tenant apply are separate opt-ins with separate evidence. They are not a default
  automatic delivery promise. Product publication is not GitHub push/deployment.
- Enterprise/fleet modules and passing local tests do not establish production
  hypervisor isolation, operational resilience, autoscaling or tenant security.

## What a public reader can verify

The supplied patch, requirements, test log, control receipts and hashes can be
inspected for internal consistency. The application implementation, full test
suite and raw private native journals are not included. Consequently this is a
maintainer-curated case study, not independently reproducible product certification.

Sanitized receipts cannot authorize runtime operations. Hashes do not independently
authenticate authorship, execution truth or provenance. Source-only exports and
text secret checks cannot detect every confidential detail concealed in prose or
pixels; public material is curated before export.

The GIF is a montage of recorded screenshots. It must not be described as a live
walkthrough, a complete end-to-end native job video or an installed SaaS demo.

## What would justify reopening development?

The portfolio demonstrates contract design, isolated execution, independent
verification and conservative ownership/recovery. Further product work is deferred
until concrete user demand or a scoped commercial pilot justifies it. No public
support, feature roadmap or maintenance service is promised by this showcase.

# Honeypot R Us feature-parity audit

Last reviewed: 2026-08-24

This audit compares the HNPT ecosystem with the public capabilities documented
by OpenCanary, Canarytokens, Cowrie, T-Pot, CrowdSec, and MITRE Engage. It is a
product-direction record, not a claim that every comparable feature is already
production-ready.

## Current strengths

- Tenant-scoped PostgreSQL/CockroachDB contracts cover assets, sensors, decoys,
  observations, correlations, discoveries, quarantine cases/actions, isolated
  playpen sessions, outcomes, reviews, audit events, idempotency, and outbox
  delivery.
- Edge containment requires a signed, short-lived decision and uses only an
  HNPT-owned isolated playpen. It never redirects suspicious traffic to an
  unrelated third party.
- Quarantine is reviewable, expiring, reversible, and separated from detection.
- Rust executables audit their checked-in `flags-2-env` contracts, all ecosystem
  repositories use zed-pkg metadata, and the canonical local configuration is
  `$HOME/.hnpt/config/hnpt-config.toml`.
- The external client and interface matrices cover more than 15 languages,
  while Rust, TypeScript, and Dart receive the deepest implementation support.

## Parity matrix

| Capability | Comparable systems | HNPT state | Direction |
| --- | --- | --- | --- |
| Lightweight tripwires | Canarytokens HTTP, credential, document, database, command, and MCP tokens | Partial: decoy storage exists, lifecycle/API is incomplete | Add typed decoys, arming/rotation, trigger ingestion, and deployment reminders |
| Multi-protocol emulation | OpenCanary protocol modules; T-Pot honeypot catalog | Gap | Add opt-in sensor profiles for HTTP, SSH/Telnet, Git, database, Redis, generic TCP banners, and passive metadata |
| Session capture | Cowrie command/file/session telemetry | Partial: evidence and playpen-event storage exists | Add bounded session transcripts, file hashes, encrypted evidence references, and replay metadata |
| Signal correlation | OpenCanary correlator; CrowdSec grouped leaky-bucket scenarios | Partial: durable tables exist | Add tenant-isolated time windows, distinct-signal counting, coalescing, suppression, and explainable scores |
| Alert delivery | OpenCanary syslog/email/hpfeeds/webhooks; Canarytokens near-real-time alerts | Gap | Add secret-reference-only destinations, signed webhook delivery, durable attempts, retry policy, and delivery audit |
| Detection/enforcement separation | CrowdSec Security Engine and remediation components | Strong foundation | Preserve explicit decisions, signed leases, dry runs, expiry, review, and cleanup semantics |
| High-interaction isolation | Cowrie backend pools; T-Pot high-interaction components | Partial | Use disposable HNPT-owned environments with per-session reset, no customer secrets, and constrained egress |
| Analyst experience | T-Pot dashboards and attack maps | Bootstrap | Add decoy, alert, correlation, evidence, and response timelines across web, desktop, and Flutter |
| Operational health | T-Pot health monitoring | Partial | Add sensor heartbeats, stale-sensor alerts, delivery backlog metrics, and safe restart diagnostics |
| Adversary-engagement planning | MITRE Engage goals, approaches, and activities | Gap | Require an objective, target behavior, desired perception, guardrails, and measurable outcome for each campaign |

## 2026-08-24 implementation wave

The first parity wave deliberately stops before public exposure or automatic
blocking. It adds:

1. Typed decoy and alert-destination contracts.
2. Portable alert-destination and alert-delivery tables for PostgreSQL and
   CockroachDB, with endpoints represented only by secret-manager references.
3. A tenant-isolated, bounded-window correlation engine that counts distinct
   signals and produces explainable, review-first recommendations.
4. API validation and local CLI/daemon visibility for decoys and alerts.
5. Regression tests for tenant isolation, time-window boundaries, duplicate
   coalescing, secret leakage, idempotency, and non-enforcement defaults.

## Safety gates before broader parity work

- Test every exact commit in `honeypot-r-us-test`; promote only a green tested
  commit to `honeypot-r-us`.
- Replace bootstrap bearer tokens with ES256/JWKS verification and enforce
  tenant authorization before public API exposure.
- Apply reviewed declarative migrations outside service startup and verify
  convergence independently on PostgreSQL and CockroachDB.
- Keep all playpens HNPT-owned, isolated, resettable, free of real customer
  secrets, and constrained from reaching unrelated systems.
- Never make an irreversible response decision from an IP address, user-agent,
  or browser-automation signal alone.

## Primary references

- OpenCanary documentation: https://github.com/thinkst/opencanary/blob/master/docs/index.rst
- Canarytokens documentation: https://docs.canarytokens.org/
- Cowrie documentation: https://docs.cowrie.org/en/stable/README.html
- T-Pot Community Edition: https://github.com/telekom-security/tpotce
- CrowdSec Security Engine: https://docs.crowdsec.net/docs/next/intro/
- CrowdSec scenarios: https://docs.crowdsec.net/docs/next/log_processor/scenarios/intro
- MITRE Engage: https://engage.mitre.org/

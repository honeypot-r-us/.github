# Honeypot R Us — Claude project

- Incubate in `honeypot-r-us-test`; promote the exact reviewed commit to
  `honeypot-r-us` only after tests and security review pass.
- Use `.zpkg.toml` as dependency/release authority and `.cli-flags.toml` plus
  `flags-2-env` for executable command surfaces. Never expose secrets as flags.
- Resolve local configuration from `$HOME/.hnpt/config/hnpt-config.toml`.
- Ship the equivalent CLI binaries `hnpt` and `hpt`.
- Keep one portable PostgreSQL/CockroachDB SQL contract, backed by shared SQL
  definitions and `dpm diff/apply/verify`. Never migrate at service startup.
- Treat Rust, Dart, and TypeScript as deep-integration lanes while preserving
  the documented 17-language client/interface surface.
- Treat network and automation patterns as evidence, not identity. Quarantine
  must be tenant-scoped, idempotent, leased, expiring, reversible, reviewable,
  and audited.
- Use only HNPT/customer-owned isolated playpens; never redirect suspected
  actors to an unrelated third party.

Planning source: Linear project `github.com/honeypot-r-us`. Coordination:
`#honeypot-r-us` and `#honeypot-r-us-test` in the ORESoftware Slack workspace.

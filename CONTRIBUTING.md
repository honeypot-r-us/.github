# Contributing to Honeypot R Us

## Rust-first testing and CI automation

Use **Rust, not Python**, for new repository-owned test scripts, CI validators, mutation/property tests, schema/code-generation checkers, and automation scripts. Prefer Rust integration tests in the existing crate, reproducible `cargo test --locked`, `cargo fmt --all -- --check`, and Clippy checks.

When changing an older Python testing/checking tool, migrate the script and its CI call sites to Rust and remove the replaced entrypoint. Keep a failing/blocked gate visible until equivalent test coverage is demonstrably green; never silently delete a security or generated-contract check to make CI pass.

This does **not** retire the product's Python SDK or prohibit a language-specific smoke compile of shipped Python source. It governs how the fleet authors tests and automation.

See [TESTING.md](TESTING.md) for complete policy, exact-commit provenance requirements, and private-repository CI safety.

## Review and promotion

Keep drafts unmerged until all required checks, independent security review and executable proof pass. Incubate in `honeypot-r-us-test` when applicable and promote only the exact verified commit. Never expose secrets through CI command-line arguments, logs, or cross-org personal access tokens.

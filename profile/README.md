# Honeypot R Us 🍯

Honeypot R Us builds defensive infrastructure, SaaS, PaaS, endpoint agents,
edge controls, and developer tooling that help B2B teams detect attackers
early, correlate deceptive interactions, and respond safely.

We turn signals such as decoy interaction, IP/ASN history, browser automation,
velocity, asset relationships, and repeated behavioral patterns into auditable
discoveries. A signal is evidence, not identity. Containment remains bounded,
leased, reversible, and reviewable.

The ecosystem includes Rust API/web/daemon/native-desktop services, a Flutter
application, Cloudflare edge infrastructure, PostgreSQL/CockroachDB persistence,
opto-sync-backed development synchronization, and generated interfaces plus
SDKs across 17 languages. Rust, Dart, and TypeScript are the deepest integration
lanes.

Suspected actors may be placed in an HNPT/customer-owned isolated playpen. We do
not redirect them to unrelated third parties. The playpen contains no real
tenant data, credentials, privileged network path, or irreversible action.

All changes incubate in [honeypot-r-us-test](https://github.com/honeypot-r-us-test)
before exact reviewed commits are promoted here. Dependencies use zed-pkg,
command contracts use flags-2-env, and database changes use declarative
migrations with convergence proofs on PostgreSQL and CockroachDB.

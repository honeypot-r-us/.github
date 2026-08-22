# Security policy

Do not open a public issue containing an active exploit, credential, customer
identifier, raw evidence, production hostname, or bypass technique. Use GitHub's
private vulnerability reporting on the affected repository. If that feature is
unavailable, contact the organization owners through an established private
channel and include only the minimum information needed to establish a secure
follow-up.

Reports should identify the affected repository/version, expected security
boundary, reproducible impact, and whether the issue can cause cross-tenant
access, containment without authorization, playpen escape, evidence exposure,
or authentication/cryptographic failure.

Never test against a customer, third party, or production environment without
written authorization. Reproduce in `honeypot-r-us-test` with synthetic data.
Do not redirect traffic to an unrelated site or include live secrets in a proof
of concept.

Supported versions are the latest production release and the currently tested
promotion candidate. Security fixes incubate privately, pass PostgreSQL and
CockroachDB migration convergence where applicable, and promote by exact commit.

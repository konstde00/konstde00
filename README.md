### Kostiantyn Dementiev

Backend and platform engineer. Five years in software engineering, two of them in DevOps.
Java and Spring Boot mostly, Python for tooling and anything involving data, running on
PostgreSQL, Kubernetes and AWS.

I work on database-per-tenant multi-tenancy: adding a tenant to a running system, across
every replica, without a restart. Same problem for four years now, from a first modular
decomposition in 2022 to the artefact behind the current papers.

What turned out to be interesting is that isolation failure under dynamic routing is silent.
Replace the routing table while requests are in flight and one of them can come back from
another tenant's database. Nothing throws, nothing logs. A green test suite says nothing
about whether tenants were isolated while it ran, so half the work is figuring out how to
see the failure at all.

Lately I have been reading toward the other end of this problem: what you do when the data
cannot be pooled in the first place, either because there is too much of it to move or
because nobody is allowed to hold all of it. Distributed query engines, federated
computation, the systems where sheer volume is the reason the architecture looks the way it
does. It is the same question I already have, only larger: who gets to see what, and how do
you show that the boundary held.

### Repositories

[runtime-tenant-onboarding](https://github.com/konstde00/runtime-tenant-onboarding) is the
artefact behind one paper under review and two in preparation. Replica reconciliation, the
benchmark harness, the Kubernetes deployment and the measurements.

[multitenancy_overview](https://github.com/konstde00/multitenancy_overview) is the October
2022 implementation the papers build on.

[genetic-timetable-scheduler](https://github.com/konstde00/genetic-timetable-scheduler)
solves university timetabling under hard constraints with a genetic algorithm.
[number-theory-algorithms](https://github.com/konstde00/number-theory-algorithms) implements
the arithmetic behind public-key cryptography from scratch.

### Upstream

Two merged pull requests to [Redash](https://github.com/getredash/redash):
[redash#7178](https://github.com/getredash/redash/pull/7178) and
[website#775](https://github.com/getredash/website/pull/775), hardening Google OAuth for
deployments behind a TLS-terminating load balancer. Flask only sees the plain HTTP hop from
the proxy, so it was building the redirect URI with an `http` scheme, and since Google
matches redirect URIs exactly, sign-in broke. The change lets an operator pin the scheme the
stack actually terminates on, so the authorisation redirect stays on https instead of the
proxy being weakened until Google accepts it.

konstde00@gmail.com

### Kostiantyn Dementiev

Backend and platform engineer, about five years across software engineering and DevOps. Java
and Spring Boot for services, Python for data work, on PostgreSQL, Snowflake, AWS and
Kubernetes, with Terraform underneath and the CKA, CKAD and CKS certifications behind the
Kubernetes part.

Most of what I have built falls into two groups. Systems that many customers share without
seeing each other, and the data platforms sitting underneath them. On one of those platforms
the analytical side held more than 100 TB in Snowflake, and my work there was replication that
keeps personal data out of the analytical copy, transformation and analysis in Python over the
warehouse, and the access and cost questions that arrive with a lakehouse of that size.

The two halves turn out to ask the same question. Multi-tenancy is about who may read what. So
is a warehouse several teams query.

### Research

I work on database-per-tenant multi-tenancy: adding a tenant to a running system, across every
replica, without a restart. Four years on the same problem now, from a first modular
decomposition to the artefact behind the papers.

The part that turned out to matter is that isolation failure under dynamic routing is silent.
Replace the routing table while requests are in flight and one of them can come back from
another tenant's database. Nothing throws, nothing logs. A green test suite says nothing about
whether tenants stayed isolated while it ran, so half the work is finding a way to see the
failure at all.

Lately I have been reading toward the other end of the same question: what you do when the data
cannot be pooled in the first place, either because there is too much of it to move or because
nobody is permitted to hold all of it. Distributed query engines, federated computation,
privacy-preserving analysis over data that stays where it is.

### Repositories

[runtime-tenant-onboarding](https://github.com/konstde00/runtime-tenant-onboarding) is the
artefact behind the papers: replica reconciliation, the benchmark harness, the Kubernetes
deployment and the measurements.
[multitenancy_overview](https://github.com/konstde00/multitenancy_overview) is the earlier
implementation they build on.

[genetic-timetable-scheduler](https://github.com/konstde00/genetic-timetable-scheduler) solves
university timetabling under hard constraints with a genetic algorithm.
[number-theory-algorithms](https://github.com/konstde00/number-theory-algorithms) implements
the arithmetic behind public-key cryptography from scratch.

A design walkthrough of the multi-tenant architecture is on
[Medium](https://medium.com/@konstde00/spring-boot-multi-tenant-architecture-overview-88198ea3991f).

### Upstream

Two merged pull requests to [Redash](https://github.com/getredash/redash):
[redash#7178](https://github.com/getredash/redash/pull/7178) and
[website#775](https://github.com/getredash/website/pull/775), hardening Google OAuth for
deployments behind a TLS-terminating load balancer. Flask sees only the plain HTTP hop from the
proxy, so it built the redirect URI with an `http` scheme, and because Google matches redirect
URIs exactly, sign-in broke. The change lets an operator pin the scheme the stack actually
terminates on, keeping the authorisation redirect on https.

### Contact

Faculty of Computer Science and Cybernetics, Taras Shevchenko National University of Kyiv.
ORCID [0009-0001-0795-1306](https://orcid.org/0009-0001-0795-1306) · konstde00@gmail.com

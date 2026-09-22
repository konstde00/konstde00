### Kostiantyn Dementiev

Backend and platform engineer, five years across software engineering and DevOps, working from
Kyiv, Ukraine. I use Java and Spring Boot for services, Python for data work, and run them on
PostgreSQL, Snowflake, AWS and Kubernetes with Terraform underneath.

I hold nine cloud certifications: AWS Solutions Architect, Developer, SysOps Administrator and
Security Specialty; HashiCorp Terraform Associate; Snowflake SnowPro Core; and all three
Kubernetes certifications, CKA, CKAD and CKS.

For five years I owned the AWS platform behind a martech and digital-analytics SaaS serving
enterprise customers, along with the Snowflake data platform underneath it. The analytical side
held more than 100 TB. My work there was the replication that keeps personal data out of the
analytical copy, transformation and analysis in Python over the warehouse, and the access and
cost questions that arrive with a lakehouse of that size.

### Research

I work on **multi-tenancy**: how one running system serves many parties from separate databases,
and what it takes to add a party to it without a restart and without anyone seeing anyone else's
data. Four years on that single question, from a first modular decomposition to the artefact
behind the papers, and all of it done from Ukraine alongside full-time engineering.

The finding that reframed the work is that isolation failure under dynamic routing is silent.
Replace the routing table while requests are in flight and one of them comes back from another
tenant's database. Nothing throws, nothing logs, and the response is well formed. A passing test
suite is therefore not evidence of isolation, because the failure needs a reader and a writer to
interleave before it appears at all. Isolation under dynamic routing is a concurrency property,
and only a concurrent test can observe it. Measuring it meant building a way to see it: 202 of
4,000 requests served from the wrong database under one update discipline, zero under the other,
with no error surfacing in either run.

That question generalises in a direction I want to keep working in. When data cannot be pooled,
because there is too much of it to move, or because no single party is permitted to hold all of
it, the same problem returns as a design constraint rather than a bug: federated and
privacy-preserving computation, distributed query engines, analysis over data that stays where
it is. Who may read what, and how you demonstrate that the boundary held.

### Repositories

[runtime-tenant-onboarding](https://github.com/konstde00/runtime-tenant-onboarding) is the
artefact behind the papers: replica reconciliation across ten replicas, the benchmark harness,
the Kubernetes deployment and the measurements.
[multitenancy_overview](https://github.com/konstde00/multitenancy_overview) is the earlier
implementation they build on.

[genetic-timetable-scheduler](https://github.com/konstde00/genetic-timetable-scheduler) solves
university timetabling under hard constraints with a genetic algorithm.
[number-theory-algorithms](https://github.com/konstde00/number-theory-algorithms) implements the
arithmetic behind public-key cryptography from scratch.

A design walkthrough of the multi-tenant architecture is on
[Medium](https://medium.com/@konstde00/spring-boot-multi-tenant-architecture-overview-88198ea3991f).

### Upstream

Two merged pull requests to [Redash](https://github.com/getredash/redash), which has around 29k
stars: [redash#7178](https://github.com/getredash/redash/pull/7178) and
[website#775](https://github.com/getredash/website/pull/775). Both address how an identity
survives a trust boundary. Behind a TLS-terminating load balancer, Flask sees only the plain
HTTP hop from the proxy, so it built the Google OAuth redirect URI with an `http` scheme, and
because Google matches redirect URIs exactly, sign-in broke. The fix lets an operator pin the
scheme the stack actually terminates on, keeping the authorisation redirect on https rather than
weakening the proxy until the identity provider accepts it. Carrying an identity intact across a
boundary somebody else controls is the same concern as the research above, one layer out.

### Contact

Faculty of Computer Science and Cybernetics, Taras Shevchenko National University of Kyiv.
ORCID [0009-0001-0795-1306](https://orcid.org/0009-0001-0795-1306) · konstde00@gmail.com

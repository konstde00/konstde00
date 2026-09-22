### Kostiantyn Dementiev

I work on multi-tenant systems: how a system shared by many customers keeps their data apart,
and how to show that it did. I'm a backend and platform engineer in Kyiv, Ukraine, with five
years in industry, and for the past four years I've been doing this research independently.

### Research

I found that when tenants are added to a system while it is running, isolation can fail without
leaving a trace. In my benchmark, rebuilding the routing table in place while requests were in
flight sent 202 of 4,000 requests to the wrong database, and not one of them raised an error or
wrote to the log. Replacing the table atomically, with no fallback, brought that to zero. The
failure only shows up when a request and an update overlap, so a test suite that checks one
tenant at a time can pass while isolation is broken. Much of the work since has gone into
building tests that can catch it.

The question gets harder when the data can't be brought into one place at all, because there is
too much of it or because nobody is allowed to hold all of it. That's where I'd like to take it
next: federated and privacy-preserving computation, and analysis over data that stays where it
lives.

### Engineering

Those five years have been at a digital-analytics SaaS serving enterprise customers, working
across software engineering and DevOps: the backend services, the AWS platform they run on, and
a Snowflake data platform holding more than 100 TB. On the data side that meant the replication
that keeps personal data out of the analytical copy, and analysis over the warehouse in Python.

I use Java and Spring Boot for services and Python for data, and deploy on AWS and Kubernetes
with Terraform. I hold nine cloud certifications: AWS Solutions Architect, Developer, SysOps
Administrator and Security Specialty, HashiCorp Terraform Associate, Snowflake SnowPro Core, and
CKA, CKAD and CKS for Kubernetes.

### Open source

I contribute to [Redash](https://github.com/getredash/redash), the open-source BI tool.
[redash#7178](https://github.com/getredash/redash/pull/7178) fixed Google sign-in for
deployments behind a TLS-terminating load balancer: Redash built the OAuth redirect with an
`http` scheme, and because Google matches redirect URIs exactly, sign-in failed. The change lets
an operator set the scheme the deployment actually uses, and
[website#775](https://github.com/getredash/website/pull/775) documents it. Both are merged
upstream.

### Repositories

[runtime-tenant-onboarding](https://github.com/konstde00/runtime-tenant-onboarding) holds the
implementation and the measurements behind the papers, including replica reconciliation and the
benchmark harness. [multitenancy_overview](https://github.com/konstde00/multitenancy_overview)
is the earlier version it grew from, with the design written up on
[Medium](https://medium.com/@konstde00/spring-boot-multi-tenant-architecture-overview-88198ea3991f).

[genetic-timetable-scheduler](https://github.com/konstde00/genetic-timetable-scheduler) builds
university timetables with a genetic algorithm under hard constraints.
[number-theory-algorithms](https://github.com/konstde00/number-theory-algorithms) implements the
arithmetic behind public-key cryptography from scratch.

Away from research I built [Ty yak?](https://github.com/konstde00/ty_yak_fe), a check-in app for
air raids and other emergencies: one person asks the people close to them whether they're safe,
and each of them answers.

BSc in Computer Science, Taras Shevchenko National University of Kyiv ·
ORCID [0009-0001-0795-1306](https://orcid.org/0009-0001-0795-1306) · konstde00@gmail.com

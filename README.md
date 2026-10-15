### Kostiantyn Dementiev

I'm a backend and platform engineer from Kyiv, Ukraine, with 5 years in industry. Most of my work is related to multi-tenant systems: how a system shared by many customers keeps their data apart, and how to show that it actually did. For the past 4 years I've been researching this on my own.

### Research

Isolation can break without any trace when tenants are added to a running system. In my benchmark, rebuilding the routing table in place while requests were in flight sent 202 of 4,000 requests to the wrong database, and none of them raised an error or wrote anything to the log, while replacing the table atomically (with no fallback) brought it to zero. It happens only when a request and an update overlap, so a test suite that checks one tenant at a time passes even though isolation is broken. That's why most of my work since then went into tests that can catch it.

The problem gets harder when the data can't be brought into one place, because there is too much of it or nobody is allowed to hold all of it. This is where I'd like to go next: federated and privacy-preserving computation, and analysis over data that stays where it is.

### Engineering

Since 2022 I've been working as backend and platform engineer at a digital-analytics SaaS that audits enterprise websites for analytics and privacy compliance (26 data-processing and reporting services, more than 100 TB of data a year). I joined as a backend developer and from late 2023 took over most of the platform work:

- Led the platform modernization: 11 services moved from Rancher to ECS and Fargate, 11 Jenkins pipelines to CircleCI, Consul retired across 8 services, and Redis moved to ElastiCache without downtime.
- Traced a 10x latency spike at double the request rate to connection-pool starvation (the fix cut the endpoint's CPU use by 34%). Separately cut an enterprise report page from 17 s to under 2 s, and a 10-table analytics query over ~10 TB from 21 s to 2.1 s.
- Found why tripling an enterprise tenant's concurrency limit (10 -> 30) left its throughput flat: the scheduler admitted only one audit per tenant per cycle, so I proposed a bounded per-tenant admission rate.
- Worked on the replication that keeps personal data out of the analytical copy, and on analysis over the Snowflake warehouse in Python.
- Led weekly incident reviews for the reporting services, wrote ~20 design documents and mentored 2 junior developers.

There I got Product and Engineering Team Member of the Year 2025 (Ukraine), the Take Accountability award in 2024 for migrating dozens of services off Rancher, Jenkins and Nexus, and 3 of the 13 quarterly Operational Excellence Champion awards since Q3 2023 (the most of any recipient). I also won "Most Impactful" at the company's AI hackathon in 2023 with an AI grammar and spelling checker.

I write services in Java and Spring Boot and data code in Python, and deploy to AWS and Kubernetes with Terraform. I have 9 cloud certifications: AWS Solutions Architect, Developer, SysOps Administrator and Security Specialty, HashiCorp Terraform Associate, Snowflake SnowPro Core, and CKA, CKAD and CKS for Kubernetes.

### Open source

In [Redash](https://github.com/getredash/redash) I fixed Google sign-in for deployments behind a TLS-terminating load balancer ([redash#7178](https://github.com/getredash/redash/pull/7178), docs in [website#775](https://github.com/getredash/website/pull/775), both merged). Redash was building the OAuth redirect with `http`, and since Google matches redirect URIs exactly - sign-in failed, so the fix allows to set the scheme the deployment really uses.

### Repositories

[runtime-tenant-onboarding](https://github.com/konstde00/runtime-tenant-onboarding) has the implementation and the measurements behind my papers (replica reconciliation and the benchmark harness included). [multitenancy_overview](https://github.com/konstde00/multitenancy_overview) is the earlier version it grew from, and its design is described on [Medium](https://medium.com/@konstde00/spring-boot-multi-tenant-architecture-overview-88198ea3991f).

[genetic-timetable-scheduler](https://github.com/konstde00/genetic-timetable-scheduler) builds university timetables with a genetic algorithm under hard constraints, and [number-theory-algorithms](https://github.com/konstde00/number-theory-algorithms) implements the arithmetic behind public-key cryptography from scratch.

Outside of research I built [Ty yak?](https://github.com/konstde00/ty_yak_fe), a check-in app for air raids and other emergencies: one person asks the people close to them if they're safe, and each of them answers.

BSc in Computer Science, Taras Shevchenko National University of Kyiv · ORCID [0009-0001-0795-1306](https://orcid.org/0009-0001-0795-1306) · konstde00@gmail.com

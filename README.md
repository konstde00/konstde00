# Kostiantyn Dementiev

**Systems researcher and platform engineer**

I study tenant isolation in shared systems: when one tenant can read another's data, how to test for it, and what correct isolation costs.

[ORCID](https://orcid.org/0009-0001-0795-1306) · [LinkedIn](https://www.linkedin.com/in/kostiantyn-dementiev-699786223/) · [Medium](https://medium.com/@konstde00) · [Credly](https://www.credly.com/users/kostiantyn-dementiev) · [konstde00@gmail.com](mailto:konstde00@gmail.com)

## Research

The work began with database-per-tenant applications in my bachelor's thesis. It now covers multi-tenant LLM serving, where tenants share a base model and its prefix cache but use their own LoRA adapters.

Right now I'm measuring whether optimizations that make multi-adapter serving cheap also open channels between tenants: prefix-cache timing, batching interference, adapter memory left after eviction, and the scheduler's admission path. The goal is a ladder of defenses, each with a measured throughput cost, and an open test suite operators can run on their own deployments. The clinical case in point is when the tenants are separate hospitals, where even the topic of a query could be a disclosure.

### Manuscripts, single-author

1. **Adapter Identity in Multi-Tenant LLM Serving**, in preparation. In 31 of the 32 vLLM releases I tested, same-named LoRA adapters of different tenants shared prefix-cache blocks, enough for an attacker to tell a victim's fine-tuning domain among 4 candidates 9 times out of 10. Keying the cache on a digest of the weights costs about 3% of throughput, against 66 to 79% for the usual fixes.
2. **Runtime Tenant Onboarding in Database-per-Tenant Spring Boot Applications**, under review at IT&I 2026, Springer CCIS. The method adds tenants to a running system without restarts. On Kubernetes, all replicas converged in each of 160 provisioning runs, with a median of 419 ms at 3 replicas.
3. **A Verification Protocol for Silent Tenant-Isolation Failures in Dynamically Routed Database-per-Tenant Applications**, under review at Advances in Cyber-Physical Systems. Replacing the routing table in place sent 939 of 120,000 lookups to the wrong tenant's database, and atomic replacement sent none of 1,215,000. The protocol caught all 12 mutants, the existing tests only 1.
4. **Per-Tenant Connection Pools as TTL Caches**, under review at ACM SAC 2027. On minikube and Amazon EKS, the model predicts the mean of every pooler-free configuration to within 4%.

Code for papers 2 to 4: [runtime-tenant-onboarding](https://github.com/konstde00/runtime-tenant-onboarding)<br>
Smaller studies: [retry-storm-metastability](https://github.com/konstde00/retry-storm-metastability) · [observer-blur-coverage](https://github.com/konstde00/observer-blur-coverage)

## Open source and research artifacts

I run released artifacts of recent systems papers and send fixes upstream when something breaks, covering more than 150 papers so far. Merged fixes include:

- [SREGym](https://github.com/SREGym/SREGym), a benchmark of AI agents resolving production incidents: three grading oracles accepted wrong fixes, such as an image that never starts. PRs [#1107](https://github.com/SREGym/SREGym/pull/1107), [#1108](https://github.com/SREGym/SREGym/pull/1108), [#1109](https://github.com/SREGym/SREGym/pull/1109).
- [ZMap](https://github.com/zmap/zmap), the Internet-wide scanner, 6.4k stars: a single BACnet or DNS reply could end a whole scan, and TCP option parsing could read past the captured packet. PRs [#984](https://github.com/zmap/zmap/pull/984), [#983](https://github.com/zmap/zmap/pull/983).
- [PyHealth](https://github.com/sunlabuiuc/PyHealth), a deep learning toolkit for healthcare, 1.7k stars: its cleanup deleted other jobs' temp folders on a shared cache. PR [#1296](https://github.com/sunlabuiuc/PyHealth/pull/1296).
- [Redash](https://github.com/getredash/redash), a BI tool with 29k stars: Google sign-in now works behind a load balancer that terminates TLS. PR [#7178](https://github.com/getredash/redash/pull/7178), docs in [website#775](https://github.com/getredash/website/pull/775).

## Industry

Since 2022, I have been a backend and platform engineer at a digital-analytics SaaS auditing enterprise websites for analytics and privacy compliance, with 26 data-processing and reporting services and over 100 TB of data a year. I joined as a backend developer and took over most platform work in late 2023.

- Found why tripling an enterprise tenant's concurrency limit from 10 to 30 left throughput flat: the scheduler admitted one audit per tenant per cycle. I proposed a bounded per-tenant admission rate.
- Prototyped cross-customer isolation for the company's GitHub App, replaced long-lived CI keys with OIDC roles across about 30 repositories, and helped with SOC 2 hardening.
- Co-designed consent-status resolution, so trackers that match no consent category are reported as uncategorized instead of silently getting the wrong status.
- Traced a tenfold latency spike to connection-pool starvation; the fix cut the endpoint's CPU use by 34%. Reduced a 10-table query over about 10 TB from 21 s to 2.1 s.
- Worked on the Snowflake lakehouse and replication that keeps personal data out of the analytical copy. Compacting 2.1 million small S3 files with Athena let a backfill that failed after 4 hours finish in about 6 minutes.
- Moved 11 services from Rancher to ECS and Fargate, 11 Jenkins pipelines to CircleCI, retired Consul, moved Redis to ElastiCache without downtime, and cut AWS costs by 45% and incidents by over half.
- Wrote over 40 design and research documents and mentored two junior developers.

Recognition:

- Product and Engineering Team Member of the Year 2025, Ukraine
- Operational Excellence Champion in 3 of 13 quarters since Q3 2023, the most of any recipient
- Take Accountability award 2024, a cultural-belief award, for migrating dozens of services off Rancher, Jenkins and Nexus
- "Most Impactful" at the company's AI hackathon 2023

I also founded OpsServing, a DevOps and cloud consultancy, in 2025. Before this job, I was a Java developer at Impltech from 2021 to 2022.

## Education

**BSc in Computer Science**, Taras Shevchenko National University of Kyiv, 2025

- One of the top 3 diploma marks in a group of 22 students
- Thesis: *Methods for Building Distributed Multi-Tenant Applications with Spring Boot*, graded 95/100, supervised by Assoc. Prof. Oleksii M. Tkachenko
- Term paper on runtime tenant onboarding, graded 99/100, supervised by Asst. Prof. Anton O. Svystunov
- Courses: Software Specification and Verification Methods 95/100, Cloud Computing 97, Statistical Modeling in AI Problems 94, Distributed and Parallel Programming 91
- 1st place in the KNU Student Mathematics Olympiad 2021, with 50 of 50 points

## Writing and community

- Five technical articles on [Medium](https://medium.com/@konstde00) with about 20,000 views, and one on DOU, Ukraine's largest developer community, with 3,000+ views
- Volunteer DevOps engineer for Charity Hero, which distributes humanitarian aid in eastern Ukraine
- Built [Ty yak?](https://github.com/konstde00/ty_yak_fe), a check-in app for air raids and other emergencies

## Stack

<img src="https://skillicons.dev/icons?i=python,java,spring,scala,pytorch,kubernetes,aws,terraform,docker,postgres,kafka,githubactions&perline=12" alt="Python, Java, Spring, Scala, PyTorch, Kubernetes, AWS, Terraform, Docker, PostgreSQL, Kafka, GitHub Actions">

- **Languages:** Python, Java with Spring Boot, Scala, SQL, Bash
- **ML systems:** PyTorch, Hugging Face Transformers, PEFT for LoRA fine-tuning, vLLM for multi-LoRA serving
- **Data:** Snowflake, Kafka, PostgreSQL, DuckDB, Amazon Athena
- **Infrastructure:** AWS, Kubernetes, Terraform, Docker, CircleCI, GitHub Actions

<details>
<summary><b>Certifications</b>: CKA, CKAD, CKS, AWS Security Specialty and 5 more</summary>

<p>
  <a href="https://www.credly.com/badges/67dc8c25-cab5-491d-8df3-29a46d333d15/public_url"><img src="https://images.credly.com/size/110x110/images/53acdae5-d69f-4dda-b650-d02ed7a50dd7/image.png" width="80" alt="AWS Certified Security Specialty"></a>
  <a href="https://www.credly.com/badges/5037522f-ea73-4a2d-a416-93767fa35e33/public_url"><img src="https://images.credly.com/size/110x110/images/9945dfcb-1cca-4529-85e6-db1be3782210/kubernetes-security-specialist-logo2.png" width="80" alt="CKS: Certified Kubernetes Security Specialist"></a>
  <a href="https://www.credly.com/badges/b8b73a83-7fca-4677-a856-8ada1c4665b6/public_url"><img src="https://images.credly.com/images/8b8ed108-e77d-4396-ac59-2504583b9d54/cka_from_cncfsite__281_29.png" width="80" alt="CKA: Certified Kubernetes Administrator"></a>
  <a href="https://www.credly.com/badges/fff7f0ea-2239-4b71-98ce-8c3a364098d7/public_url"><img src="https://images.credly.com/images/cc8adc83-1dc6-4d57-8e20-22171247e052/blob" width="80" alt="CKAD: Certified Kubernetes Application Developer"></a>
  <a href="https://www.credly.com/badges/bb6fc71e-7a00-446e-8b71-c4cf1968fc5b/public_url"><img src="https://images.credly.com/images/0e284c3f-5164-4b21-8660-0d84737941bc/image.png" width="80" alt="AWS Certified Solutions Architect Associate"></a>
  <a href="https://www.credly.com/badges/1b42f230-4b64-4f64-acb0-98486541caad/public_url"><img src="https://images.credly.com/size/110x110/images/f0d3fbb9-bfa7-4017-9989-7bde8eaf42b1/image.png" width="80" alt="AWS Certified SysOps Administrator Associate"></a>
  <a href="https://www.credly.com/badges/c11fbcba-d572-4dd4-9c67-ee9e681ace9b/public_url"><img src="https://images.credly.com/size/110x110/images/b9feab85-1a43-4f6c-99a5-631b88d5461b/image.png" width="80" alt="AWS Certified Developer Associate"></a>
  <a href="https://www.credly.com/badges/2f94381d-1f8c-48ef-89f1-77136f8e74c7/public_url"><img src="https://images.credly.com/images/0dc62494-dc94-469a-83af-e35309f27356/blob" width="80" alt="HashiCorp Certified: Terraform Associate"></a>
</p>

- AWS Certified Security Specialty, 2026
- CKS: Certified Kubernetes Security Specialist, 2026
- Snowflake SnowPro Core, 2026
- CKA: Certified Kubernetes Administrator, 2025
- CKAD: Certified Kubernetes Application Developer, 2025
- AWS Certified Solutions Architect Associate, 2023
- AWS Certified SysOps Administrator Associate, 2023
- AWS Certified Developer Associate, 2023
- HashiCorp Certified: Terraform Associate, 2023

</details>

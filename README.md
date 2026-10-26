# Kostiantyn Dementiev

**Systems researcher and platform engineer**

I study tenant isolation in shared systems: when one tenant can read another's data, how to test for it, and what correct isolation costs.

[ORCID](https://orcid.org/0009-0001-0795-1306) · [LinkedIn](https://www.linkedin.com/in/kostiantyn-dementiev-699786223/) · [Medium](https://medium.com/@konstde00) · [Credly](https://www.credly.com/users/kostiantyn-dementiev) · [konstde00@gmail.com](mailto:konstde00@gmail.com)

## Research

Right now I'm measuring whether the optimizations that make multi-LoRA serving cheap also open channels between tenants, and what each defense costs in throughput.

Manuscripts, single-author:

1. **Adapter Identity in Multi-Tenant LLM Serving**, in preparation. In 31 of 32 vLLM releases, same-named LoRA adapters of different tenants shared prefix-cache blocks. Keying the cache on a digest of the weights costs about 3% of throughput.
2. **Runtime Tenant Onboarding in Database-per-Tenant Spring Boot Applications**, under review at IT&I 2026, Springer CCIS. Adds tenants to a running system without restarts.
3. **A Verification Protocol for Silent Tenant-Isolation Failures in Dynamically Routed Database-per-Tenant Applications**, under review at Advances in Cyber-Physical Systems. It caught all 12 mutants, and the existing tests caught only 1.
4. **Per-Tenant Connection Pools as TTL Caches**, under review at ACM SAC 2027.

Code for papers 2 to 4: [runtime-tenant-onboarding](https://github.com/konstde00/runtime-tenant-onboarding)<br>
Smaller studies: [retry-storm-metastability](https://github.com/konstde00/retry-storm-metastability) · [observer-blur-coverage](https://github.com/konstde00/observer-blur-coverage)

## Open source

I run released artifacts of recent systems papers (150+ so far) and send fixes upstream when something breaks. Merged fixes include:

- [SREGym](https://github.com/SREGym/SREGym): three grading oracles accepted wrong fixes. PRs [#1107](https://github.com/SREGym/SREGym/pull/1107), [#1108](https://github.com/SREGym/SREGym/pull/1108), [#1109](https://github.com/SREGym/SREGym/pull/1109)
- [ZMap](https://github.com/zmap/zmap) (6.4k stars): a single BACnet or DNS reply could end a whole scan. PRs [#984](https://github.com/zmap/zmap/pull/984), [#983](https://github.com/zmap/zmap/pull/983)
- [PyHealth](https://github.com/sunlabuiuc/PyHealth) (1.7k stars): its cleanup deleted other jobs' temp folders. PR [#1296](https://github.com/sunlabuiuc/PyHealth/pull/1296)
- [Redash](https://github.com/getredash/redash) (29k stars): Google sign-in behind a load balancer that terminates TLS. PR [#7178](https://github.com/getredash/redash/pull/7178)

## Industry

Backend and platform engineer since 2022 at a digital analytics SaaS (26 data processing and reporting services, over 100 TB of data per year), doing most of its platform work since late 2023.

- Replaced long-lived CI keys with OIDC roles across about 30 repositories, prototyped cross-customer isolation for the company's GitHub App, and helped with security hardening for SOC 2.
- Found why tripling a tenant's concurrency limit from 10 to 30 left throughput flat (one audit per tenant per scheduler cycle) and proposed a bounded per-tenant admission rate.
- Moved 11 services from Rancher to ECS and Fargate and 11 Jenkins pipelines to CircleCI, cutting AWS costs by 45% and incidents by over half.
- Benchmarked four ways to read 2.1 million small S3 files. Compacting them with Athena before loading into Snowflake let a backfill that had failed after 4 hours finish in about 6 minutes, and a K-means model of object sizes showed that deleting early beat lifecycle expiry for 97% of files.
- Cut a 10-table query over about 10 TB from 21 s to 2.1 s.

Recognition: Product and Engineering Team Member of the Year 2025 (Ukraine), Operational Excellence Champion in 3 of 13 quarters, Take Accountability award 2024, "Most Impactful" at the company's 2023 AI hackathon for an AI grammar and spelling checker.

Also founded OpsServing, a DevOps and cloud consultancy, in 2025. Java developer at Impltech, 2021-2022.

## Education

**BSc in Computer Science**, Taras Shevchenko National University of Kyiv, 2025. One of the top 3 diploma marks in a group of 22 students, thesis graded 95/100. 1st place in the 2021 KNU Student Mathematics Olympiad.

## Writing and community

Five articles on [Medium](https://medium.com/@konstde00) (about 20,000 views) and one on DOU (3,000+ views). Volunteer DevOps engineer for Charity Hero. Built [Ty yak?](https://github.com/konstde00/ty_yak_fe), a check-in app for air raids and other emergencies.

## Stack

<img src="https://skillicons.dev/icons?i=python,java,spring,scala,pytorch,kubernetes,aws,terraform,docker,postgres,kafka,githubactions&perline=12" alt="Python, Java, Spring, Scala, PyTorch, Kubernetes, AWS, Terraform, Docker, PostgreSQL, Kafka, GitHub Actions">

Also vLLM, Hugging Face Transformers, PEFT, Snowflake, DuckDB, Amazon Athena, and CircleCI.

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

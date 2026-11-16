### Hi, I'm Kostiantyn

I study tenant isolation in shared systems: when one tenant can read or affect another's data, how to test for that, and what correct isolation costs. I've worked in backend and platform engineering since 2021.

[**Website**](https://konstde00.github.io/) | [**CV**](https://konstde00.github.io/data/CV_Dementiev.pdf) | [**ORCID**](https://orcid.org/0009-0001-0795-1306) | [**Email**](mailto:konstde00@gmail.com)

Papers (single-author):

- Accepted for publication in Advances in Cyber-Physical Systems: [a verification protocol for silent tenant-isolation failures](https://doi.org/10.5281/zenodo.23859398). The protocol caught all 12 seeded bugs, and the existing tests caught 1.
- Under review: [runtime tenant onboarding for database-per-tenant applications](https://doi.org/10.5281/zenodo.23859166) (International Journal of Computing) and [per-tenant connection pools as TTL caches](https://doi.org/10.5281/zenodo.23859309) (ACM SAC 2027). Code and data for all three: [runtime-tenant-onboarding](https://github.com/konstde00/runtime-tenant-onboarding).
- In preparation: stale and shared adapter state in LLM prefix caches. In vLLM 0.31.0, after a LoRA adapter was updated through the stock API, 771 of 780 test requests were served cached prefix tokens computed before the update. With a digest of the weights in the cache key, no test run served stale state, at a cost of 3 to 8% of throughput on decode-heavy workloads. A crash I reported on the way is fixed upstream ([vLLM #64570](https://github.com/vllm-project/vllm/issues/64570)).

Merged upstream: [23 pull requests](https://github.com/search?q=author%3Akonstde00+is%3Apr+is%3Amerged+-user%3Akonstde00&type=pullrequests) in 16 projects, for example:

- [Pie](https://github.com/pie-project/pie/pull/1101) (LLM serving): any client could list, attach to or terminate other users' processes.
- [ZMap](https://github.com/zmap/zmap/pull/984): a single BACnet or DNS reply could end a scan.
- [SREGym](https://github.com/SREGym/SREGym/pulls?q=is%3Apr+author%3Akonstde00+is%3Amerged) (benchmark for SRE agents): three of its graders accepted wrong fixes.

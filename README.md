### Hi, I'm Kostiantyn

I study tenant isolation in shared systems: when one tenant can read or affect another's data, how to test for that, and what correct isolation costs. I've worked in backend and platform engineering since 2021.

[**Website**](https://konstde00.github.io/) | [**CV**](https://konstde00.github.io/data/CV_Dementiev.pdf) | [**ORCID**](https://orcid.org/0009-0001-0795-1306) | [**Email**](mailto:konstde00@gmail.com)

Papers (single-author):

- Accepted: [a verification protocol for silent tenant-isolation failures](https://doi.org/10.5281/zenodo.23859398) (Advances in Cyber-Physical Systems).
- Under review: [runtime tenant onboarding](https://doi.org/10.5281/zenodo.23859166) and [per-tenant connection pools as TTL caches](https://doi.org/10.5281/zenodo.23859309).
- In preparation: stale adapter state in LLM prefix caches. In vLLM 0.31.0, after a LoRA adapter update through the stock API, 771 of 780 test requests were served cached prefix tokens computed before the update. A crash I reported ([vLLM #64570](https://github.com/vllm-project/vllm/issues/64570)) is fixed upstream.

Merged upstream: [23 pull requests](https://github.com/search?q=author%3Akonstde00+is%3Apr+is%3Amerged+-user%3Akonstde00&type=pullrequests) in 16 projects, for example:

- [Pie](https://github.com/pie-project/pie/pull/1101): any client could list, attach to or terminate other users' processes.
- [ZMap](https://github.com/zmap/zmap/pull/984): a single BACnet or DNS reply could end a scan.

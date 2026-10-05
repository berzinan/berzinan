## Hi there 👋


---
I am a second year Computer Science & Mathematics Student at UofT interested in:
- Robotics
- Control Theory
- Optimization
- Distributed Systems

---
I am currently the path planning lead at [UTFR](https://fsaeutoronto.ca/), where I design trajectory optimization algorithms for an autonomous electric vehicle that competes in Formula Student tournaments worldwide. 

https://github.com/user-attachments/assets/74a00103-30ce-4545-875a-20c513a1045a

---

## Projects

#### Scrapecore
A distributed web-scraping framework in Python (asyncio, Redis). It separates scraping infrastructure from site-specific logic. The library handles queuing, scheduling, retries and failure recovery. You write a parser per site, and the framework runs it across any number of worker machines.

- **Coordinator / agent architecture:** a coordinator turns jobs into tasks and aggregates results. Agents on separate machines claim tasks, execute them and report back.
- **Fault tolerant:** an atomic Redis task queue with claim lease renewal, automatic recovery of tasks from crashed agents, per-task retries with backoff, and idempotent job completion.
- **Multi-stage pipelines:** a parser's output can spawn follow-up tasks, so flows like search → filter → fetch details are declared rather than hand-orchestrated.
- **Pluggable by contract:** `BaseParser`, `BaseAuth`, and swappable HTTP backends (aiohttp, or curl_cffi for browser TLS impersonation).
- **Per-stage rate limiting:** each endpoint is throttled independently, with a Redis sliding-window limiter for fleet-wide caps.
[Source](https://github.com/berzinan/scrapecore)

#### Pokerface


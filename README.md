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

### Scrapecore
A distributed web-scraping framework in Python (asyncio, Redis). It separates scraping infrastructure from site-specific logic. The library handles queuing, scheduling, retries and failure recovery. You write a parser per site, and the framework runs it across any number of worker machines.

- **Coordinator / agent architecture:** a coordinator turns jobs into tasks and aggregates results. Agents on separate machines claim tasks, execute them and report back.
- **Fault tolerant:** an atomic Redis task queue with claim lease renewal, automatic recovery of tasks from crashed agents, per-task retries with backoff, and idempotent job completion.
- **Multi-stage pipelines:** a parser's output can spawn follow-up tasks, so flows like search → filter → fetch details are declared rather than hand-orchestrated.
- **Pluggable by contract:** `BaseParser`, `BaseAuth`, and swappable HTTP backends (aiohttp, or curl_cffi for browser TLS impersonation).
- **Per-stage rate limiting:** each endpoint is throttled independently, with a Redis sliding-window limiter for fleet-wide caps.
  
[Source](https://github.com/berzinan/scrapecore)

### Pokerface
A no-limit Texas Hold'em engine in Java, built for writing poker bots and finding out how good they are. The engine owns dealing, betting, side pots and showdown, and hands each bot a restricted view of the table. You implement one method per bot, and the framework runs it — against other bots to rank them, or against a human at a tournament table.

- **Information-restricted agent interface:** a bot receives an immutable `PlayerView` holding its own cards, the board, stacks, bets and a deck count — never the deck itself, and never another player's hand.
- **Human play at the terminal:** sit down against any mix of bots and act with `fold`, `check`, `call`, `raise <amount>` or `allin`. Every turn prints the board, the pot, what you owe and each seat's stack and status. Illegal commands are rejected and re-prompted, and showdowns are narrated with each player's hole cards and their best hand named in full.
- **Per-decision move timer:** each decision runs against a wall-clock budget. An agent is told how long it has and sizes its own work to fit. Humans also get a move timer!
- **Two measurement pipelines:** fixed-stack ring batches report bb/100 with standard errors, which is what actually separates two bots. Escalating-blind tournaments report win rate under elimination, which is what a human would experience. Seat permutations are redrawn every N hands, and seed-driven bots are periodically rebuilt from a fresh seed to ensure statistical fairness.
- **Single-pass hand evaluation:** rank counts, flush suit and straight detection all fall out of one sweep over the cards, with straights found by shifting a rank bitmask and the ace mirrored low to fold the wheel into the ordinary case. Sustains ~4,500 hands/second single-threaded, six-handed, at 300 Monte Carlo rollouts per decision.
- **In development:** More bots, AI bots, and a GUI!

[Source](https://github.com/berzinan/pokerface)

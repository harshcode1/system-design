# System Design — Interview Prep, in Public

An interview-first journey through system design — Low-Level Design (LLD) and High-Level
Design (HLD) — learned the only way it sticks: **by building, not watching.** Every topic
here ends in runnable Java or a diagram + written tradeoff analysis I produced myself. This
repo is the proof-of-work.

**Stack:** Java · design patterns · distributed-systems primitives
**Approach:** build-first · just-in-time patterns · spaced revision · daily logging

---

## How this repo works

Two learning tracks, one hard rule: **a topic isn't "done" until it's proven with code I wrote and ran.**

- **BUILD track (LLD)** — full Java implementations of classic design problems (Parking Lot,
  Elevator, BookMyShow, Splitwise, …). Each lands with a README, a Mermaid class diagram, and
  the patterns/SOLID decisions behind it.
- **UNDERSTAND track (HLD / concepts)** — each primitive (caching, consistent hashing, rate
  limiting, load balancing, …) ends in a minimal runnable Java demo that proves the mechanism,
  plus a note in my own words and a diagram. Pure-architecture topics ship a diagram + tradeoff
  writeup instead of code.

Progress and revision are tracked in the open:

| File | Purpose |
|------|---------|
| [`ROADMAP.md`](ROADMAP.md) | The full tiered syllabus (what, and in what order). |
| [`PROGRESS.md`](PROGRESS.md) | Current state — where I am right now. |
| [`REVISION.md`](REVISION.md) | Spaced-recall ledger — confidence + last-revised per topic. |
| [`sessions/`](sessions/) | Daily dated log — full attendance history, zero-days included. |

---

## Roadmap at a glance

- **Tier 1 — Foundations & LLD (Java):** SOLID, then the core LLD problems, with design patterns
  learned just-in-time as each problem demands them.
- **Tier 2 — The HLD spine:** estimation, CAP, SQL vs NoSQL, load balancing, caching, consistent
  hashing, indexing, rate limiting, key-value stores, messaging queues, microservices, scaling.
- **Tier 3 — Depth:** distributed transactions, concurrency control, high availability, security
  (OAuth, JWT, encryption, web attacks), and more.

See [`ROADMAP.md`](ROADMAP.md) for the full breakdown.

---

## Repository structure

```
├── 01-foundations/      SOLID, OOP design principles
├── 02-patterns/         Design patterns (learned in context)
├── 03-lld/              Low-Level Design problems (runnable Java)
├── 04-estimation/       Back-of-the-envelope estimation
├── 05-building-blocks/  HLD primitives (caching, hashing, rate limiting, …)
├── 06-microservices/    Microservices patterns & architecture
├── 07-security/         OAuth, JWT, encryption, web attacks
└── sessions/            Daily learning log
```

---

*Learning in public — updated as I go.*

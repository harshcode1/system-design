# ROADMAP — Interview-First System Design Plan

**Context:** SDE-1 / SDE-2 target. Interviews in 4–6 weeks. ~18 hrs/week.
Work top-down: finish Tier 1 before Tier 2, Tier 2 before Tier 3.
BUILD track = runnable Java. UNDERSTAND track = note in own words + Mermaid diagram.

---

## TIER 1 — DO FIRST (weeks 1–2.5). Highest ROI. LLD round is near-certain.

### Foundations (fast, it's vocabulary)
- [ ] SOLID Principles (one sitting)
- [ ] Liskov Substitution Principle

### Core LLD — BUILD in Java (the priority of the whole repo)
- [ ] Parking Lot
- [ ] Tic-Tac-Toe (or Snake & Ladder)
- [ ] Elevator System
- [ ] BookMyShow
- [ ] Splitwise
- [ ] ATM

### Patterns — learn JUST-IN-TIME as the LLDs above demand them
(Do NOT batch these. Expect to hit: Strategy, Factory/Abstract Factory, Observer,
State, Decorator, Builder, Chain of Responsibility, Singleton.)
- [ ] Strategy
- [ ] Factory & Abstract Factory
- [ ] Observer
- [ ] State
- [ ] Decorator
- [ ] Builder
- [ ] Chain of Responsibility

---

## TIER 2 — THE HLD SPINE (weeks 3–4.5). Matters most for SDE-2.
Primitives every HLD answer is built from. UNDERSTAND track unless noted.

- [ ] Back-of-the-Envelope Estimation
- [ ] CAP Theorem
- [ ] SQL vs NoSQL
- [ ] Load Balancer & algorithms
- [ ] Caching strategies Part 1 (Cache-Aside, Read-Through)
- [ ] Caching strategies Part 2 (Write-Through, Write-Around, Write-Back)
- [ ] Consistent Hashing
- [ ] DB Indexing (B+ tree, clustered vs non-clustered)
- [ ] Design a Rate Limiter        ← BUILD a small Java version
- [ ] Design a Key-Value Store (Dynamo-style)
- [ ] Distributed Messaging Queue (Kafka/RabbitMQ-style)
- [ ] API Gateway & Microservices architecture
- [ ] Microservices patterns (SAGA, CQRS, Strangler, Decomposition)
- [ ] Scale from Zero to Million Users

---

## TIER 3 — DEPTH, IF TIME ALLOWS (or if the role signals it).
First thing to cut under time pressure. Real SDE-2 depth.

- [ ] Distributed Transactions: 2PC / 3PC / SAGA
- [ ] Two-Phase Locking (2PL) Parts 1–3
- [ ] Distributed Concurrency Control (isolation levels, optimistic vs pessimistic)
- [ ] Idempotent POST API / idempotency handler
- [ ] High Availability (Active-Passive vs Active-Active)
- [ ] Proxy vs Reverse Proxy
- [ ] How DNS works
- [ ] Service Mesh
- [ ] Thundering Herd problem
- [ ] Dual Write problem / event-driven patterns

### Security block — Tier 3 by default, PULL UP to Tier 2 for fintech/security roles
(Harsh has real 2FA/JWT/AES/RBAC experience from BetterMind — can speak to these from work.)
- [ ] OAuth 2.0
- [ ] JWT Parts 1–2
- [ ] Symmetric & Asymmetric Encryption (AES, Diffie-Hellman) Parts 1–2
- [ ] Web attacks: CSRF, XSS, CORS, SQL Injection

---

## Remaining patterns (Tier 3 completeness — only if going for pattern mastery)
Adapter, Bridge, Composite, Facade, Flyweight, Proxy, Command, Iterator, Mediator,
Memento, Template Method, Visitor, Interpreter, Null Object, Object Pool, MVC,
Composite, Prototype.

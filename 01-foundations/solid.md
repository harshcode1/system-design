Source: Claude-authored

# SOLID Principles

## Why this matters for interviews
LLD rounds don't ask "what is SRP." They hand you a vague problem (Parking Lot, ATM,
Splitwise), you produce a class design, and the interviewer probes it: "what if I add a new
payment type — how many classes change?" SOLID is the checklist you silently run against your
own design before you commit to it. Every LLD problem in this repo gets graded against these.

---

## S — Single Responsibility Principle
A class should have **one reason to change**, not "one method." Reason to change = one actor/
stakeholder whose requirement drives it.

Bad: `Invoice` class that computes totals AND formats a printable receipt AND saves to DB.
Three different stakeholders (finance logic, UI/presentation, persistence) can each force a
change to this one class → high coupling, easy to break unrelated things.

Fix: split into `Invoice` (data + totals), `InvoicePrinter` (formatting), `InvoiceRepository`
(persistence).

**Interview tell:** if you're about to write a method name with "and" in it, or a class doing
validation + business logic + I/O, stop.

## O — Open/Closed Principle
Classes should be **open for extension, closed for modification**. Adding new behavior should
mean adding new code, not editing tested existing code.

Bad: `PaymentProcessor` with `if (type == CARD) ... else if (type == UPI) ...`. Every new
payment type means editing this method again — risk of regressing existing payment types.

Fix: `PaymentStrategy` interface, one implementation per payment type, `PaymentProcessor` holds
a reference and calls `strategy.pay()`. New payment type = new class, zero edits to existing
code. This is literally the **Strategy pattern** — OCP is the principle, Strategy is often the
mechanism.

**Interview tell:** growing if/else or switch on a "type" field is OCP violation #1. It's the
single most common thing interviewers plant in the problem statement (e.g. "the elevator should
support different scheduling algorithms later").

## L — Liskov Substitution Principle
Subtypes must be substitutable for their base type **without breaking correctness**. If code
works with a `Bird b`, it must keep working when `b` is actually a `Penguin`, with no surprises.

Bad: `Bird` has `fly()`, `Penguin extends Bird` throws `UnsupportedOperationException` in
`fly()`. Any code that loops over `List<Bird>` and calls `fly()` now crashes on penguins even
though "a penguin is-a bird" sounds fine in English.

Fix: don't model it as inheritance at all if the child can't honor the full contract. Either
`Flyable` as a separate interface only flying birds implement, or restructure the hierarchy so
the base class only promises what every subtype can actually do.

**Interview tell:** if implementing an interface method as `throw new UnsupportedOperation
Exception()` or an empty no-op just to satisfy the compiler, LSP is broken. Fix the hierarchy,
don't hide the problem.

Full mechanics get a dedicated pass later — for now, know the definition and spot violations.

## I — Interface Segregation Principle
Don't force a class to implement methods it doesn't need. Many small, focused interfaces beat
one fat interface.

Bad: one `Worker` interface with `work()` and `eat()`. A `RobotWorker` is forced to implement
`eat()` with a no-op or exception — same smell as LSP above, root cause is a bloated interface.

Fix: split into `Workable` and `Eatable`. `RobotWorker implements Workable` only.

**Interview tell:** ISP violations are usually the *cause* of LSP violations. If you catch
yourself writing a no-op/throwing override, the real fix is usually splitting the interface
(ISP), which then also fixes LSP.

## D — Dependency Inversion Principle
High-level modules shouldn't depend on low-level modules — both should depend on abstractions.
Concretely: constructor/field types should be interfaces, not concrete classes, and the
concrete implementation gets **injected**, not `new`'d inside the class that uses it.

Bad: `OrderService` does `private MySqlOrderRepository repo = new MySqlOrderRepository();`
directly. `OrderService` (high-level policy) now hard-depends on a concrete DB choice
(low-level detail). Swapping to Postgres or mocking for a test means editing `OrderService`.

Fix: `OrderService` depends on `OrderRepository` interface, the concrete impl is passed in via
constructor (constructor injection). This is also **why Spring Boot's `@Autowired`/DI container
exists** — Spring is a framework built specifically to automate DIP at scale. You already use
DIP every time you inject a `@Service` or `@Repository` in Spring — SOLID just names the
principle explicitly.

**Interview tell:** if a class instantiates its own collaborators with `new` instead of
receiving them, DIP is violated — and it also means the class is hard to unit test in
isolation.

---

## How these interact (don't treat them as 5 isolated rules)
- OCP is usually *achieved* via DIP + Strategy/Factory patterns: depend on an interface (DIP),
  add new implementations without touching existing code (OCP).
- ISP violations cause LSP violations: a fat interface forces subclasses into throw/no-op
  overrides, which breaks substitutability.
- SRP is upstream of all of them: a class doing too much is more likely to be forced into
  ugly conditionals (OCP) and fat interfaces (ISP).

## Tradeoffs — SOLID isn't free
- **Rejected alternative:** just write the simplest thing that works (one class, if/else,
  concrete types) and refactor later if requirements actually change.
- **Why SOLID anyway, in an interview:** the interviewer is explicitly testing whether your
  design *anticipates* the kind of change they're about to ask for ("now add UPI", "now add a
  new elevator scheduling strategy"). Over-applying SOLID to a throwaway script is real
  over-engineering in production — but an LLD interview problem is *specifically designed* to
  have a "what if we add X" follow-up, so applying OCP/DIP up front is the correct read of the
  room, not premature abstraction.

## Quick check (answer out loud before moving on)
1. Your `NotificationService` has `if (channel == EMAIL) ... else if (channel == SMS) ...`.
   Which principle is violated, and what's the fix?
2. Why does using Spring's `@Autowired` constructor injection satisfy DIP automatically, but
   `new SomeRepoImpl()` inside a `@Service` class does not, even though both end up wired at
   runtime?
3. Give an LSP violation from your own past code (BetterMind, TaskForge, Phoenix OS) — did you
   have a subclass override a method to throw or no-op?

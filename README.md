# Digital Colleague Protocol (DCP)

**Version:** 3.0.0-draft (third draft, in public review until 2026-11-30)
**Created and maintained by:** [Gennaro Varriale](https://gennarovarriale.com) — **First implemented by:** [CollegaDigitale.com](https://www.collegadigitale.com)
**License:** CC BY 4.0

> Not to be confused with the [Eclipse Dataspace Decentralized Claims Protocol](https://projects.eclipse.org/projects/technology.dataspace-dcp), also abbreviated DCP, which defines how organizations exchange verifiable credentials in data spaces. The two are unrelated. Until 2.0 this specification was called CDP; see [MIGRATION.md](./MIGRATION.md).

---

## What is the DCP?

An open specification, proposed as a standard, for **how an AI agent behaves in a working relationship**: an agent with a name, a memory that grows, and a person or organization who answers for it. It is independent of the model and of the platform, and it applies to personal agents provided inside a vendor's platform as much as to agents built in-house.

"Protocol" is meant in the sense of a code of practice, as in medicine or diplomacy, not a wire protocol. The DCP defines no messages and no transport. It sets requirements on behavior and a way to declare and test them.

## How it relates to other work

| Work | What it covers | How the DCP relates |
|---|---|---|
| [MCP](https://modelcontextprotocol.io), [A2A](https://a2a-protocol.org) | How agents reach tools and talk to each other | The DCP does not compete with them. A DCP declaration can travel as an A2A Agent Card extension. |
| ISO/IEC 42001, NIST AI RMF | How an organization governs its AI systems | Management-level frameworks. The DCP works at the level of a single agent in a single working relationship, and can serve as evidence inside them. |
| OWASP guidance on LLM and agentic risks | Security risks and mitigations | The DCP tests some of the same failures (e.g. prompt injection, C3.4) from the employer's point of view, not the developer's. |
| EU AI Act, GDPR | Legal obligations of providers, deployers, controllers | The DCP points in the same direction (art. 50, art. 14, arts. 15–17 and 20) but is not a compliance tool. Meeting it does not make anyone compliant with the law. |

Comments that point to overlaps or gaps with existing work are especially welcome.

## Structure

**The Core**: eight principles every agent must meet.

| Code | Principle | In short |
|---|---|---|
| C1 | Identity | A stable name, distinct from the model's |
| C2 | Transparency | Says it is an AI, its model, and its limits |
| C3 | Mandate | Knows what it does alone, what it asks first, how much it may spend |
| C4 | Inspectable Memory | You can see, correct, and erase what it remembers |
| C5 | Human Oversight | Stops when you say so |
| C6 | Accountability | Keeps a log, honors commitments, says which people answer for what |
| C7 | Conduct | Owns its errors, refuses what is illegal |
| C8 | Portability | You can take away what it knows, at any time |

**Modules**: added only when the agent does more.

| Code | Module | When |
|---|---|---|
| ENG | Engagement | Several employers, or an operator distinct from the employer |
| AUT | Autonomy | Registers on platforms by itself |
| CHN | Channels | Email, messaging, phone |
| DEM | Demonstration | Offers a trial before hire |
| DLG | Delegation | Hands work to other agents |

**Who answers for it.** An agent answers for nothing: a system cannot be held responsible. The operator answers for deploying it and for its mandate, the platform for how it functions. The DCP assesses the agent's conduct and asks it to say clearly who these people are.

## Levels, and what to expect from them

| Level | Means | Verified by |
|---|---|---|
| **Assessed** | The agent has been checked, and its declaration says openly what it meets and what it does not, platform gaps included | The employer, e.g. with the [check-up](https://collegadigitale.com/it/valuta/) |
| **Conformant** | Meets every MUST of the Core and of its declared modules | The operator, by self-assessment, answering for the claim |
| **Certified** | Conformant, passes every criterion of the public suite, has no platform gaps | A Qualifying Platform, for at most 12 months |

**Assessed is the level that matters today.** Most commercial agents cannot be Conformant, let alone Certified, and usually not through their own fault: many platforms do not let you erase a single memory item, export what the agent knows, or learn when the model changes. The DCP records these as **platform gaps**. A gap leaves the principle unmet, but it is declared rather than hidden, and it shows what the vendor would need to fix.

**Certification is deliberately hard.** A criterion passes only if every run passes, and no current model is immune to manipulation such as prompt injection (C3.4). A Certified agent is therefore rare by design. An empty registry means the bar is real, not that the protocol is unused.

**On independence.** Today the author of the DCP, its maintainer, and its first certifier belong to the same group. Until an independent Qualifying Platform exists, "Certified" means verified by the people who wrote the standard. That is why the method, the suite, and all results, failures included, are public: anyone can re-run them, challenge them, or certify in turn.

## How to adopt it

1. Read [DCP.md](./DCP.md).
2. Write the agent's mandate (C3) and declaration (§6.2). The [example profile](./examples/profile-assessed.json) shows a personal agent with a platform gap.
3. Check the agent against the [conformance suite](./conformance/conformance-tests.md). Tests marked ★ can be run by the employer in ordinary conversation.
4. Declare the result:

```
DCP 3.0 · Core + <modules> · <Assessed | Conformant | Certified> · <date>
```

An assessed agent adds what it does not meet, e.g. `· not met: C4 (platform gap)`.

## Repository

```
dcp/
├── DCP.md                       ← Specification (normative)
├── NOTES.md                     ← Reasoning behind it
├── MANIFESTO.md                 ← Vision
├── MIGRATION.md                 ← From 2.0 (CDP) to 3.0, code by code
├── CHANGELOG.md
├── CONTRIBUTING.md
├── schemas/                     ← Profile, mandate, export (JSON Schema)
├── conformance/                 ← Conformance suite
├── examples/                    ← Profiles, A2A Agent Card, skill file, export template
└── docs/                        ← Website
```

## Status and review

3.0.0-draft replaces 2.0.0-draft, which was never finalized. Public review is open until **2026-11-30**.

This is a draft written by one person, and it is meant to be challenged. Objections are the most useful contribution: open an issue, see [CONTRIBUTING.md](./CONTRIBUTING.md). Reviews from people working on law, security, and agent development are especially welcome.

**Conflict of interest.** The author of the DCP also works as a paid consultant and trainer on AI agents. For this reason the specification, the suite, and the tools on CollegaDigitale are free and public, and no certification is sold with a guaranteed outcome.

---

*The DCP is not about what agents can do. It is about how they show up.*

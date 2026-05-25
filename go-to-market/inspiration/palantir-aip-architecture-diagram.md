# Inspiration: Palantir AIP Architecture Diagram

Owner: Ashley Odom
Last updated: 2026-05-25

**Idea:** Create a Keywell-branded public architecture overview diagram similar to Palantir's AIP Architecture page. This would be a technical marketing asset for the website, proposals, and sales conversations — showing the full platform at a glance.

**Source:** https://www.palantir.com/docs/foundry/architecture-center/aip-architecture

---

## What Makes the Palantir Diagram Work

The diagram presents 12 numbered architectural components in a single, readable visual with clean spatial organization:

| # | Component | What it communicates |
|---|---|---|
| 1 | Secure LLM Integration & Access | Entry point; commercial + open-source models, BYOM, PII obfuscation |
| 2 | End-to-end Observability | Model catalog, full traceability |
| 3 | Context Engineering | Contextual data, logic, and systems of action — the "brain" layer |
| 4 | The Ontology System | Semantic/kinetic/dynamic models; Human+AI decision model |
| 5 | Vector, Compute, Tool Services | Media, vector, multimodal compute |
| 6 | Security & Governance | Role, marking, purpose-based controls; branching, approvals, checkpoints |
| 7 | Agent Lifecycle | Agent building, orchestration, evaluation suites |
| 8 | Operational Automation | Scheduled, event-driven, API-driven automation |
| 9 | Development Environments | VS Code, Jupyter, MCP, IDE extensions |
| 10 | Human+AI Applications | No/low-code app building, object-oriented analytics, real-time analytics |
| 11 | Package, Release & Deploy | Packaging, dependency management, release channels |
| 12 | Enterprise Automation | AIP Assist, Code Assist, AI-enabled pipelining |

**User types called out on the right:** Operational Teams, Developer Teams, Analyst Teams, Governance Teams — also Automations as a consumer category.

**Design observations:**
- Numbered callouts make it easy to reference in conversation ("see section 6 — governance")
- Arrows show data flow, not just components in isolation
- Three distinct columns (left = inputs, center = platform core, right = consumers/outputs)
- Companion docs page gives every section a written explanation — the diagram is the nav
- Clean gray/white boxes with blue accents; icons keep it approachable

---

## Proposed Keywell Version

A Keywell architecture overview would cover the same conceptual territory but grounded in Keywell's stack and healthcare-specific positioning. Suggested sections:

| # | Keywell Component | Analogous to Palantir |
|---|---|---|
| 1 | Secure LLM Integration | Commercial (OpenAI, Gemini) + Open-source (Llama, Mistral) + BYOM; PII protection; no data leaves your environment |
| 2 | Healthcare Data & Ontologies | Built-in claims, EHR, and price transparency ontologies; Tuva integration |
| 3 | Structured + Unstructured Data Layer | EDW/SQL + document stores in one query surface |
| 4 | HIPAA-Compliant Governance | User-level data access controls; dataset, document, and model permissions |
| 5 | Audit & Observability | Full audit log: prompts, responses, queries, model access, risk flags |
| 6 | Agent Building | Custom agents trained on your data and documents |
| 7 | Agent Orchestration | Multi-agent workflows; event-driven and scheduled automation |
| 8 | AI BI (Integrated Analytics) | Natural language querying of structured data alongside documents |
| 9 | Platform Infrastructure | Databricks-native; predictable spend; reduced TCO |
| 10 | Front-End & API Layer | Retool-based UI; REST API for custom integrations |
| 11 | Human+AI Applications | Purpose-built apps per use case (claims analysis, prior auth, pop health) |
| 12 | Deployment & Packaging | Customer-owned deployment; no vendor lock-in |

**User types to show:** Clinical / Operations Teams, Data & Analytics Teams, Compliance & Governance Teams, Developer Teams

---

## Next Steps

- [ ] Create a draft in Canva or Figma using the Keywell design system
- [ ] Start with the architecture concept graphic already in ClickUp/Canva (the "door/key" metaphor) and evolve it toward this more detailed view
- [ ] Consider a companion docs page on keywell.ai that mirrors this structure
- [ ] Use numbered callouts so sales reps can reference specific sections in conversations

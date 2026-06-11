# Healthcare AI Risk Matrix — Framework Document

Last updated: 2026-06-06
Owner: Ashley Odom

---

## Overview

The Healthcare AI Risk Matrix is Keywell's internal framework for evaluating and communicating the risk profile of AI use cases in healthcare settings. It provides a structured, visual way to assess where a given use case sits on two critical dimensions — the severity of potential harm and the degree of operational dependency on the AI outcome — and to determine what level of governance, oversight, and auditability is required before deployment.

This framework is derived from Keywell's Trustworthy AI methodology and maps directly to the regulatory and liability landscape governing AI in healthcare: HIPAA, FDA guidance on clinical decision support, state AI laws, and emerging federal frameworks around patient safety and algorithmic accountability.

**When to use this framework:**

- **Sales conversations** — To help prospects understand where their use case sits relative to the risk landscape and why governed AI infrastructure (rather than an off-the-shelf SaaS tool) is the right fit.
- **Use case qualification** — To prioritize which use cases Keywell is best positioned to implement and where the risk-value tradeoff justifies the engagement.
- **Risk advisory discussions** — To facilitate internal conversations with legal, compliance, and clinical leadership at prospect or client organizations before committing to a deployment path.
- **Roadmap planning** — To sequence use case development from lower-risk to higher-risk zones as governance matures.

---

## How to Read the Matrix

The matrix is a 2×2 grid with dotted concentric curves that divide the space into risk zones.

### X-Axis: Severity of Risk / Harm (Low → High)

This axis captures the **worst-case consequence** if the AI system produces an incorrect, biased, or harmful output. At the low end, a bad output causes administrative friction — a billing error, a scheduling inconvenience. At the high end, a bad output could contribute to patient injury or death. This axis is grounded in the clinical stakes of the domain, independent of how often errors actually occur.

Key questions for calibrating severity:
- If this AI is wrong, what happens to the patient or organization?
- Is the downstream consequence reversible or irreversible?
- Does the use case touch clinical decision-making directly or only indirectly?

### Y-Axis: Dependency on the Outcome (Low → High)

This axis captures **how much the organization or clinician relies on the AI output** to act. Low dependency means a human expert reviews, filters, or overrides the AI before anything happens — the AI is an efficiency tool, not a decision-maker. High dependency means the AI output directly triggers action with little or no human review in the loop.

Key questions for calibrating dependency:
- Does a human review and validate this output before it affects a patient or workflow?
- Is there a meaningful feedback loop or override mechanism?
- Would the organization act differently if the AI output changed by a small margin?

---

## Risk Zones

The concentric curves create four operationally meaningful zones. Think of them as bands that radiate outward from the low-low origin (safest) toward the high-high corner (most critical).

| Zone | Matrix Position | Operational Meaning |
|---|---|---|
| **Low** | Near the origin — low severity, low dependency | Standard software deployment practices apply. Monitoring and basic logging are sufficient. Human oversight is incidental, not structural. |
| **Medium** | Mid-range on one or both axes | Formal QA and validation processes required. Outputs should be reviewed before actioning. Bias and drift monitoring should be in place. Documentation of model behavior and limitations is required. |
| **High** | High on one axis, moderate-to-high on the other | Governance framework required: model cards, audit logs, defined override processes, stakeholder sign-off, and a clear escalation path. Regulatory counsel should review. Change management for clinical and operational staff is non-negotiable. |
| **Critical** | High severity and high dependency | Full clinical validation and regulatory alignment required before deployment. May require FDA clearance review. Liability analysis, informed consent considerations, and malpractice implications must be resolved. Not a Keywell sweet spot for initial deployment; these use cases require mature governance infrastructure already in place. |

---

## Use Case Breakdown

### 1. Automated Billing Code
**Position:** Low dependency / Low severity — safest quadrant.

Billing code automation produces revenue cycle recommendations that are reviewed by human coders before submission. Errors result in claim rejections or minor financial adjustments — neither outcome affects patient health. Governance requirements are minimal: basic accuracy tracking, audit logging, and a human-in-the-loop review step are sufficient for compliant deployment.

### 2. Patient Scheduling
**Position:** High dependency / Low-to-medium severity.

Scheduling automation is operationally embedded — patients act directly on the system's output (appointment confirmations, reminders, slot assignments) with limited staff intervention for routine cases. However, a scheduling error rarely produces irreversible harm. The primary risks are access delays, patient dissatisfaction, and no-show rates. Governance should include monitoring for demographic bias in slot allocation and exception handling for high-acuity appointment types.

### 3. Clinician Support LLM *(Keywell sweet spot)*
**Position:** Low-to-medium dependency / Medium-to-high severity.

A clinical LLM that surfaces documentation suggestions, prior auth language, or care gap insights is used by a trained clinician who retains full authority over the final decision. The severity is meaningful — clinical context is being shaped — but the dependency is deliberately kept low through workflow design. This is the governance model Keywell is built to enable: the AI operates as an auditable, observable assistant inside a governed workflow, not as an autonomous decision-maker. Keywell's scaffolding layer enforces explainability, logging, and override controls by design.

### 4. Off-Hours Chatbot *(Keywell sweet spot)*
**Position:** Medium dependency / Medium-to-high severity.

An off-hours triage or navigation chatbot handles patient inquiries without immediate clinical oversight. Severity is real — patients may act on guidance they receive at 2 a.m. without a follow-up call. Dependency is moderate: most chatbot interactions involve routing, not treatment decisions, but the lack of real-time human review raises the stakes. This use case sits precisely in the zone where ad hoc AI deployment is genuinely dangerous and governed AI scaffolding provides meaningful risk reduction. Keywell's approach — defined guardrails, escalation paths, and full conversation logging — directly addresses the liability profile of this zone.

### 5. Emergency Alerts *(Keywell sweet spot)*
**Position:** Low dependency / High severity.

An AI system that generates emergency alerts — deterioration warnings, sepsis flags, rapid response triggers — produces outputs with high potential consequences, but in a well-designed implementation, a clinical human acts as the final decision point before the alert is acted upon. Severity is high because the cost of a missed alert or a false alert cascade is significant. Dependency is managed low by design. This is a use case where Keywell's governance infrastructure (alert threshold documentation, model performance dashboards, audit trails for regulatory review) provides direct value without requiring Keywell to assume clinical liability.

### 6. Sepsis Alert
**Position:** High dependency / High severity — upper-right zone.

Sepsis alerts are time-sensitive enough that clinical staff often act immediately on a triggered alert, driving dependency high. Combined with the life-or-death stakes of sepsis recognition, this use case sits in or near the critical zone. Deployment requires clinical validation studies, integration with physician workflow, defined false positive management, and likely regulatory review. This is not an initial deployment target for Keywell; it is a use case that requires mature governance infrastructure already in place.

### 7. AI Clinical Diagnosis
**Position:** High dependency / High severity — highest risk position on the matrix.

Autonomous clinical diagnosis is the most risk-laden position in the matrix. Outcomes are directly life-affecting, the AI output carries high operational weight in clinical decision-making, and the regulatory and liability landscape is complex (FDA, state medical practice laws, malpractice exposure). Keywell does not currently target this use case. When it appears in a sales conversation, the appropriate response is to acknowledge the use case's importance and redirect toward the governance infrastructure work that must precede any deployment at this risk level.

---

## Keywell's Positioning: The Governed Middle

The three use cases marked with the Keywell logo — Clinician Support LLM, Off-Hours Chatbot, and Emergency Alerts — define Keywell's strategic sweet spot in the risk matrix. They share a critical characteristic: **they sit in the zone where the consequences of ungovernrd AI are real, but the right governance architecture can bring risk to an acceptable level.**

This positioning is not accidental. Use cases in the lower-left quadrant (billing codes) don't require Keywell's governance infrastructure — a lightweight SaaS tool is often sufficient, and the risk doesn't justify the investment. Use cases in the upper-right quadrant (AI clinical diagnosis, sepsis alerts at high dependency) carry liability exposure that requires extensive clinical validation and regulatory engagement beyond Keywell's current scope.

The Keywell-marked use cases sit in the band where:

1. **Severity is high enough that governance is not optional.** A clinician support LLM without audit logs, a chatbot without escalation protocols, or an emergency alert system without threshold documentation are genuine organizational liabilities. The pain of under-governance is real and demonstrable.

2. **Dependency is calibrated — not zero, but not so high that a governance layer alone is insufficient.** Keywell's scaffolding works because it enforces a workflow design principle: the AI informs, a human confirms. When that principle holds, governance infrastructure is sufficient to manage risk. When dependency climbs to the sepsis-alert level, governance alone is not enough.

3. **The risk-value tradeoff justifies investment.** These use cases deliver enough operational value — reduced documentation burden, extended access hours, faster response to clinical deterioration — that healthcare organizations are motivated to invest in governed deployment rather than skipping AI or deploying it recklessly.

This is the message for the field: Keywell is not for the easy use cases (SaaS handles those) and not for the highest-risk cases (those require a different kind of engagement). Keywell is for the use cases that are consequential enough to demand real governance and that become deployable — safely and quickly — when the right scaffolding is in place.

---

## Using This Framework in Sales Conversations

### When to introduce it

Bring this matrix into a conversation when a prospect has named specific use cases but hasn't yet connected the dots between AI capability and AI governance. It works especially well when:

- A prospect is evaluating multiple AI use cases and hasn't prioritized them
- A legal, compliance, or CMO stakeholder is in the room and the conversation is turning toward risk
- A prospect has had a previous AI initiative stall or fail and is trying to understand why

### How to run the conversation

1. **Start with their use case, not the matrix.** Ask the prospect to describe what they are trying to automate or improve. Listen for the dependency and severity signals in their description.

2. **Place their use case on the matrix.** Walk through the two axes out loud: "How much does your team rely on this output before acting? And if the AI is wrong, what's the worst-case consequence?" Let the prospect do most of the placing — they know their workflows.

3. **Name the zone.** Once the use case is placed, describe what that zone requires operationally. For medium and high zones, the requirements (audit logs, override workflows, bias monitoring, escalation protocols) are exactly what Keywell's scaffolding layer delivers by default.

4. **Connect to the Keywell sweet spot.** If the use case is in the Keywell zone, make the connection explicit: this is the kind of use case that stalls or gets shut down by legal when it's built on a SaaS tool, and succeeds when it's built on governed infrastructure. Keywell is the infrastructure that makes this use case deployable.

5. **Use the critical zone as a contrast.** If the prospect mentions a use case in the upper-right (diagnosis, high-dependency sepsis), don't dismiss it — acknowledge its importance and explain that those use cases require the governance foundation Keywell builds before they can be responsibly deployed. That's often a longer engagement, and it starts with the governed middle.

### Key message to leave behind

> The question is not whether to use AI for this use case. The question is whether your organization has the governance infrastructure to deploy it responsibly. In the medium and high risk zones, that infrastructure is what separates a successful AI program from a liability.

---

*Related docs: [Core Messaging Stack](../messaging/core-messaging-stack.md) | [Company Fundamentals](../messaging/company-fundamentals.md) | [Trustworthy AI Showcase NYC 2026](../applications/trustworthy-ai-showcase-nyc-2026.md)*

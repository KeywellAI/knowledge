# Keywell's AI Governance Approach

Last updated: 2026-06-10
Owner: Ashley Cairns

> This is Keywell's own governance philosophy — distinct from the CHAI framework and other external standards. See [External Frameworks](external-frameworks/chai-playbooks.md) for background on industry frameworks. Keywell's approach is shaped by its role as an AI **vendor and developer**, not a healthcare delivery organization.

---

## Keywell's Governance Position

Keywell operates at the intersection of two governance roles:

1. **As a vendor** — Keywell is subject to the governance requirements that client HDOs place on AI vendors (model disclosure, monitoring reporting, data use restrictions, BAA provisions). Understanding and exceeding these expectations is a competitive advantage.

2. **As a governance enabler** — Keywell's platform provides the technical infrastructure that helps clients implement their own governance programs: model cards, audit logging, lineage tracking, drift monitoring, evaluation sandboxes, NIST AI RMF alignment.

The CHAI framework was written for HDOs. Keywell's governance approach adapts what's relevant to the vendor/developer context and translates the rest into how Keywell helps clients meet their obligations.

---

## Core Governance Principles

### 1. Governance as a product feature, not a checkbox

Keywell's governance infrastructure is built into the platform, not bolted on. MLflow model registry, Unity Catalog lineage, SHAP explainability, evaluation sandbox — these are not compliance artifacts, they are how Keywell builds trust with clients and delivers accountable AI.

### 2. Client data sovereignty

Keywell's deployment model keeps client data in the client's environment. PHI does not leave the client cloud. This is both a security posture and a governance commitment — clients own their data, outputs, and configurations.

### 3. Perpetual licensing = ongoing governance

Keywell's perpetual license model means Keywell has a sustained relationship with clients and their deployed models. This creates an obligation (and opportunity) for ongoing model monitoring, update notifications, and performance reporting — the things CHAI contracts should require from vendors.

### 4. Transparency and disclosure

Keywell should proactively provide model cards for all deployed solutions, disclose training data sources and limitations, communicate material model changes in advance, and support clients in their own governance documentation.

### 5. Human-in-the-loop by design

Keywell's Quickstart workflows are structured with human review as part of the workflow. AI outputs are inputs to human decisions, not autonomous actions. This aligns with the CHAI principle that governance enables faster and safer adoption — not slower.

---

## Keywell's Governance Infrastructure (Platform Capabilities)

| CHAI Requirement | Keywell Capability |
|---|---|
| Model cards | MLflow model registry; documentation layer |
| AI inventory registry | Unity Catalog; model registry |
| Data lineage | Databricks Unity Catalog end-to-end lineage |
| Audit logging | Immutable audit logs at user and model level |
| Model monitoring / drift detection | Databricks monitoring; alert thresholds |
| Validation and testing | Keywell Evaluation Sandbox |
| Risk-proportionate governance | Configurable per use case |
| Explainability | SHAP-based feature importance |
| NIST AI RMF alignment | GOVERN, MAP, MEASURE, MANAGE mapped to platform |
| PHI controls | Field-level masking, RBAC, encryption at rest/in transit |
| Role-based access | Unity Catalog; SSO integration |

---

## What Keywell Needs to Define (To-Do)

The following governance elements are less formalized and should be developed:

- [ ] **Internal AI use policy** — What rules govern Keywell employees' use of AI tools (shadow AI, PHI in prompts, approved tools list)
- [ ] **Standard BAA / AI addendum** — Template language for client contracts that proactively addresses CHAI vendor expectations (model disclosure, training restrictions, monitoring obligations, change notification)
- [ ] **Model card standard** — Keywell's own model card format for solutions deployed to clients
- [ ] **Incident response procedure** — Internal process for when a deployed model produces unexpected or harmful outputs
- [ ] **Data governance policy** — How Keywell handles client data internally (access controls, retention, de-identification for development use)
- [ ] **Responsible AI principles statement** — Formal articulation of Keywell's RAI principles (for external use in proposals and client governance programs)

---

## Keywell Governance as a Sales Asset

Clients implementing CHAI-aligned governance programs need vendors who:
- Provide model cards and technical documentation
- Notify clients of material model changes in advance
- Support monitoring and performance reporting
- Keep client data in the client environment
- Have explicit BAA provisions covering AI training restrictions

Keywell's architecture and deployment model directly satisfies these requirements. The governance section of the Central Health RFQ proposal articulated many of these points — that content should be maintained and reused.

See also [go-to-market/messaging/](../go-to-market/messaging/) for governance-related positioning.

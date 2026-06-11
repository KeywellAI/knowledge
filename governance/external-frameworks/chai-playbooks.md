# CHAI AI Governance Framework — Digest

Last updated: 2026-06-10

**Source:** Coalition for Health AI (CHAI) AI Governance Playbooks (2025–2026)
**Source documents:** [Google Drive folder](https://drive.google.com/drive/folders/1uve-o3n-gRdBfiT60dDqJH6uqCYUr7xt)
**License:** CC BY-NC-ND 4.0 — shareable with attribution, noncommercial, no derivatives

> **Read first:** See [governance/index.md](../index.md) for important notes on how Keywell should use this material. Do not adopt this framework wholesale — it was written for healthcare delivery organizations, not AI vendors.

---

## What CHAI Is

The Coalition for Health AI (CHAI) is a multi-stakeholder collaborative of 150+ healthcare organizations. Their AI Governance Playbook series provides consensus-defined baseline operational controls for how HDOs should govern AI across its lifecycle. The playbooks are the closest thing to an industry standard that currently exists for health AI governance.

The framework covers **4 Domains** and **5 Subdomains**:

| Domain/Subdomain | Topic |
|---|---|
| Domain 1 | AI Policy |
| Domain 2 | Organizational Structure |
| Domain 3 | Organizational Resources |
| Subdomain 4.1 | Responsible AI Lifecycle Management and Use |
| Subdomain 4.2 | Risk and Impact Assessments |
| Subdomain 4.3 | Responsible Data Management and Use |
| Subdomain 4.4 | Third Party Management |
| Subdomain 4.5 | Education, Training, and Feedback |

---

## Core Principles Across the Framework

**Risk-based approach.** Every playbook emphasizes calibrating governance rigor to the risk level of the AI solution. Not every AI tool needs the same depth of review.

**Build on what you have.** Adapt existing processes (vendor management, patient safety reporting, HR policies, data governance) to include AI-specific elements rather than building parallel infrastructure from scratch.

**Risk tiers.** Solutions are classified Low, Medium, or High risk based on: proximity to patient care, severity of potential harm, PHI involvement, level of human oversight, and whether it makes recommendations vs. takes autonomous actions.

**Responsible AI principles.** Across all domains: **usefulness, fairness, safety, transparency, privacy, security.** These six principles should be operationalized at each lifecycle stage.

---

## Domain 1: AI Policy

**Purpose:** Establish a formal, organization-wide AI policy that standardizes how AI is evaluated, approved, used, and monitored.

**Baseline controls:**
- Develop a formal AI Policy document, approved by leadership, accessible to all relevant staff
- Define key concepts (definition of AI, scope, approval process)
- Designate someone with oversight for policy changes

**Minimum policy components:** Introduction & purpose, scope & applicability, definitions, governance structure, responsible AI lifecycle management.

**Shadow AI.** A major concern: staff using AI tools outside the formal approval process (ChatGPT to summarize notes, a vendor activating an EHR AI feature without review, local ML models, Copilot for work tasks). Organizations need easy intake pathways and usage request forms to surface shadow AI.

**AI definition variability.** FDA, NIST AI RMF, WHO, ISO all define AI differently. Anchor to an established external standard and acknowledge definitions will evolve.

**Key challenges organizations face:**
- Rapidly evolving landscape makes policies go stale
- Balancing scope (all AI vs. GenAI only) and granularity (high-level vs. detailed)
- Getting executive buy-in — frame governance as enabling faster/safer adoption, not creating drag

---

## Domain 2: Organizational Structure

**Purpose:** Define governance committee structure, roles, and accountability for AI oversight.

Key elements: AI Governance Committee (cross-functional: clinical, IT, legal, compliance, ethics, operations), named roles (inventory owner, security lead, clinical AI champions), RACI matrices, connection to board/executive oversight.

---

## Domain 3: Organizational Resources

**Purpose:** Ensure security infrastructure, tooling, documentation, and human expertise support AI governance.

**Key controls:**

| Control | What It Requires |
|---|---|
| 3.1 Security infrastructure | HITRUST, SOC 2, NIST CSF compliance; encryption at rest/in transit |
| 3.2 Security assessments | Vulnerability scanning; gap analysis per AI system |
| 3.3 Asset records | Comprehensive records of datasets, models, tools — for traceability |
| 3.4 Cybersecurity evaluation | Penetration testing, adversarial robustness, API security |
| 3.5 Model cards + AI inventory | Adopt CHAI Applied Model Card; integrate with registry |
| 3.6 AI inventory registry | Track all internal and third-party AI solutions |
| 3.7 Validation and monitoring | Tools and process to validate performance and monitor drift |
| 3.8 Computing infrastructure | Audit rights over AI infrastructure; HIPAA and BCDR alignment |
| 3.9 Workforce competency | Define roles, responsibilities, qualifications for AI governance personnel |
| 3.10 Clinician training | Identify which solutions require pre-implementation training |

**Model Cards.** CHAI's Applied Model Card (AMC) documents: intended use, out-of-scope uses, training data, performance metrics, known biases, monitoring plans, vendor contact. Completion should be a prerequisite for deployment approval — no model card = no deployment clearance.

**AI inventory registry minimum fields:** system name/ID, vendor/developer, intended use, deployment status, primary end users, data inputs (PHI sensitivity), risk tier, contract renewal date, link to model card, governance approval status, last review date.

**AI-specific security risks (beyond traditional IT security):**
- Re-identification risk from de-identified training data
- Data poisoning by adversarial actors
- Model inversion attacks (extracting training data via repeated queries)
- Indirect prompt injection (adversarial content embedded in clinical text influences AI behavior — especially serious for agentic AI)

**Stale application example (real):** An AI solution for ECG interpretation stopped working after an ECG machine was replaced because the model triggered on hardware metadata. No one noticed for 6 months. Software license continued to be paid for a silently inactive system.

---

## Subdomain 4.1: Responsible AI Lifecycle Management and Use

**Purpose:** Govern AI solutions across their full lifecycle.

**Four ingestion modalities** (how AI enters an HDO):

| Modality | Description | Key challenge |
|---|---|---|
| Research models | IRB-scoped, controlled settings | Define onramp into production |
| In-house developed | Internal data science teams | Variable processes |
| Vendor/co-developed | Commercially licensed | Accountability gaps, contractual constraints |
| AI-enhanced in existing systems | EHR/platform updates activating AI | Often bypasses procurement gates entirely |

**The embedded AI problem.** The fastest-growing and least-governed modality. AI features arrive via routine software updates from EHR vendors. No new contract is executed when the feature is enabled. Organizations should default to "off" for newly released AI features pending governance review.

**Responsible AI Lifecycle Steps:**
1. Define the Problem & Plan — Start with the problem statement, not the technology
2. Intake/Procurement — Structured two-part intake (light-touch triage → deep review for higher risk)
3. Risk categorization — Low/Medium/High based on use case and context
4. Pre-deployment — Readiness assessment; if contract signed before assessment, include conditional right-to-terminate
5. Piloting — Limited-scale; pre-define success/failure criteria; pre-defined go/no-go authority
6. Deployment — With monitoring activated, clear accountability, communication to stakeholders
7. Monitoring — Ongoing; performance, safety signals, subgroup performance, drift, user behavior
8. Termination — Pre-define criteria; data disposition sign-off; lessons-learned review

**Decision gates.** At each lifecycle step, document: approval status, evidence reviewed, next review trigger date.

**Agentic AI note.** Governance must extend beyond model outputs to bound the agent's autonomy: allowed tool inventory, decision-delegation rules, human-on-the-loop checkpoints, reversibility of actions. Monitoring must extend to action drift (tool-call success/failure rates, hallucinated tool invocations, unexpected action sequences).

**Monitoring maturity pathway:**
- Foundational: Named owner + defined review cadence + documented escalation triggers
- Structured: Standardized checklist + tracking log + formal escalation to governance committee
- Advanced: Automated dashboards + alert-based escalation + vendor-enabled data access

**Real-world examples cited:** Memorial Sloan Kettering (iLEAP: G1–G5 decision gates, "Express Pass" for low-risk, "algorithmovigilance"), Stanford Health Care (RAIL), five-pillar framework at unnamed regional health system.

---

## Subdomain 4.2: Risk and Impact Assessments

**Purpose:** Categorize, assess, mitigate, and monitor AI-related risks.

**Four-phase risk management:**
1. Risk Categorization (pre-deployment) — Low/Medium/High triage for all solutions
2. Risk Assessment (higher-risk only) — Deep-dive on hazards, harms, mitigations
3. Risk Mitigation — Implement and document controls
4. Risk Monitoring — Continuously monitor over time

**Risk categorization guiding questions:**
- How close is the AI output to the patient? (back-office vs. bedside)
- What is the human oversight level and ability to override?
- What is the potential severity if wrong? (morbidity/mortality)
- Does it involve sensitive populations or underrepresented groups in training data?
- Does it touch PHI?
- How difficult is it to detect errors or model drift?

**Agentic AI risk domains (emerging):** Autonomy, Irreversibility, Agent-to-Agent handoffs.

**Three distinct assessment types:**

| Type | Scope | When |
|---|---|---|
| Risk Categorization | High-level triage; assigns Low/Medium/High | All solutions pre-deployment |
| Risk Assessment | Deep-dive: hazards, harms, mitigations | Higher-risk solutions |
| AI System Impact Assessment | Broader system-level consequences; risk + benefit across stakeholders | Higher-risk solutions |

**Conditions where deployment should not proceed:**
- Unmitigated high-severity harm potential
- Vendor refuses to provide model cards or documentation
- Residual risk exceeds organizational tolerance thresholds
- Self-calibrating AI where vendor cannot explain governance procedures for calibration events

**Real-world example — Tampa General Hospital:** 3-tier review (Full Product Review with discussion and vote / Expedited Review via consent agenda / Exempt — no vote). Six-domain assessment team: Cybersecurity, Utility & Validity, Compliance, Risk, Ethics, Educational Impact.

**Key external tools:** CHAI Risk Categorization Tool v2 (maps to NIST AI RMF and EU AI Act), NIST AI RMF, ISO 14971:2019 (medical device risk), IMDRF SaMD framework.

---

## Subdomain 4.3: Responsible Data Management and Use

**Purpose:** Govern how data is documented, used, de-identified, and prepared for AI systems.

**Three data classifications:**

| Type | Description | Legal requirement |
|---|---|---|
| PHI | Individually identifiable health information | Business Associate Agreement (BAA) |
| Limited Data Set (LDS) | Partially de-identified; geographic/date data may remain | Data Use Agreement (DUA) |
| De-identified Data | All 18 HIPAA identifiers removed | DUA strongly recommended for AI contexts |

**Five baseline controls:**
1. Data acquisition register — Document all data used in AI systems
2. Data Use Agreements — AI-specific DUA provisions (training restrictions, re-identification prohibition, data minimization, audit rights)
3. De-identification policies — Written HIPAA-compliant policies; validate before AI training use
4. Data quality and bias — Recurring evaluation; named owner; document known bias sources
5. Data preparation SOP — Standardized procedures for cleaning, encoding, normalization, train/test splits

**AI-specific de-identification risks:**
- LLMs can reproduce verbatim PHI from training data (memorization)
- Synthetic data retains statistical properties enabling re-identification for rare conditions
- Agentic AI cross-context aggregation can assemble re-identifying profiles even from de-identified sources
- Safe Harbor was not designed for LLM/RAG/agentic architectures

**Common bias types in healthcare AI:**

| Bias Type | Description |
|---|---|
| Representation bias | Training data overrepresents insured, English-speaking, urban patients |
| Label bias | Proxies for health need (e.g., cost) inherit historical inequities in care access |
| Temporal bias | Models trained on historical data reinforce outdated care patterns |
| Survivorship/selection bias | Patients who disengage from care are underrepresented |
| Measurement bias | Proxy variables (zip code for SES, insurance type for income) compound systematic error |

**For GenAI/agentic AI, additional SOP elements:**
- Prompt and context window management — define what patient data is permitted in prompts
- Retrieval corpus preparation for RAG systems — governance of what's indexed and update cadence
- Fine-tuning data curation — consent/authorization, memorization risk, data mix ratios
- Agentic tool and data access — least-privilege access, logging all tool calls, escalation procedures

**Key principle:** Data sharing is a decision, not a default. Before negotiating a DUA, ask: what is the minimum data the vendor actually needs?

---

## Subdomain 4.4: Third Party Management

**Purpose:** Define how HDOs manage vendor relationships for AI — intake, risk, contracts, and operational controls.

**Four-phase vendor management workflow:**
1. AI Intake — Structured questionnaire; gather model cards, validation evidence, security certs
2. Risk Assessment — Apply organization's risk tolerance to intake evidence
3. Contracting — AI addendum to BAA/DUA with specific provisions
4. Operational Controls — Workflow safeguards for risks contracting couldn't fully resolve

**AI vendor contract addendum — key components:**
- What counts as AI under the agreement
- Notice/approval before AI is used or materially modified
- Data use restrictions — explicit training restriction (vendor cannot train on client data without permission)
- Ownership of outputs and derivative data rights
- Representations and warranties
- Monitoring obligations and performance reporting
- Change management: advance notice for material changes (30–90 days)
- Subcontractor and foundation model disclosure
- Audit and reporting rights
- Lifecycle management responsibilities across parties
- Disclosure of known model limitations
- Termination and sunsetting provisions

**Post-deployment monitoring as contractual requirement:**
- What metrics the vendor will track and report
- Frequency and format of reports
- Obligations when performance degrades
- Consequences for missed reporting — service credits, fee withholding, expanded audit rights, and a direct link to contract renewal

**Tiered enforcement ladder:**
1. Notice and Cure
2. Remediation Plan
3. Access Suspension
4. Termination for Cause

**Vendor failure planning:** contracts should address bankruptcy, acquisition, product sunset — source code/model escrow, data return/destruction, change-of-control provisions.

**Agentic AI: additional disclosure requirements:**
- Scope of autonomy (what can the agent do without human confirmation?)
- Tool and integration access (which systems can it read/write/invoke?)
- Action reversibility
- Escalation and circuit breakers
- Memory and context boundaries
- Multi-agent considerations

**Real-world contract examples included verbatim in the CHAI playbook:**
- Mercy — AI Terms Short Form and Long Form
- Kaiser Permanente — AI Requirements for Vendors, Contractors and Suppliers (v09/3/2025)

**CHAI AI Intake Questionnaire domains (11):** Clinical Safety & Effectiveness, Data Integrity & Lineage, Fairness & Non-discrimination, Governance Structure & Oversight, Legal & Regulatory Compliance, Model Validation & Performance Monitoring, Security & Access Control, System Reliability & Resilience, Transparency & Traceability, User Experience & Workflow Integration, Impact Measurement & ROI.

---

## Subdomain 4.5: Education, Training, and Feedback

**Purpose:** Train staff and patients, establish feedback channels for AI incidents.

**Seven types of training:**
1. General AI literacy — All staff; what AI is, limitations, organizational policies
2. Use case-specific — For staff who interact with a particular AI system
3. New hire onboarding — AI orientation before first encounter with AI systems
4. Leadership and governance — Strategic oversight focus for executives, board, AI committee
5. Vendor-delivered — From the AI vendor on their specific system
6. Incident response — Scenario-based: what to do when AI produces unexpected/harmful outputs
7. Patient and community — Build patient capacity to engage with AI in their care

**Three AI incident categories:**
- **People** — Human behavior incidents: automation bias, failure to escalate, misinterpretation
- **Data** — Data problems: population shift, biased training data, data corruption
- **AI** — Model/system incidents: model drift, software defects, edge case failures

**Patient transparency vs. consent:**
- Most AI use requires transparency (clear disclosure), not formal consent
- Formal consent is reserved for: AI that materially changes standard of care, introduces new clinical risk, requires new category of patient data, is investigational, or is required by state regulation
- HIPAA NPP must be updated to describe AI-related data use

**Whistleblower protections — four components:**
- **Anonymity** — Identity never collected or knowable
- **Confidentiality** — Identity known to narrow group; shielded from vendor during root-cause analysis
- **Non-retaliation** — Formal written commitment; covers termination, demotion, reassignment
- **Data retention disclosure** — Plain-language explanation of what is collected, stored, how long

**Real-world training examples:**
- KPNC — Two-week mandatory shadowing period before each hospital's go-live; daily debriefs post-launch; formal readiness gate before activation
- Parkland Health — Safety-net; narrow training to users who actually touch the model; existing patient safety reporting + AI tag
- UC San Diego Health — COMPOSER sepsis model; role-differentiated training; silent mode pilot before activation; structured clinician feedback loop

---

## Key External Resources Referenced

| Resource | Description |
|---|---|
| CHAI Applied Model Card (AMC) | Healthcare-specific model card template |
| CHAI Risk Categorization Tool v2 | Pre-deployment risk triage; maps to NIST AI RMF and EU AI Act |
| CHAI AI Intake Questionnaire | 11-domain vendor intake (draft as of May 2026) |
| NIST AI RMF | Comprehensive risk framework; GOVERN, MAP, MEASURE, MANAGE |
| ISO 14971:2019 | Medical device risk management |
| ISO/IEC 42005:2025 | AI system impact assessment |
| IMDRF SaMD Clinical Risk Categorization | For AI classified as Software as a Medical Device |
| HHS HIPAA NPP template | Model Notice of Privacy Practices |
| Mercy AI Terms (Short + Long Form) | Real-world vendor contract language |
| Kaiser Permanente AI Requirements | Real-world vendor AI requirements (v09/3/2025) |

---

## Notable Real-World Examples Cited

- **Tampa General Hospital** — 3-tier risk review with 6-domain assessment team
- **Intermountain Health** — 300+ AI solutions in centralized inventory; Center of Excellence
- **Michigan Medicine** — 24-model card library; completion required before clinical approval
- **Memorial Sloan Kettering** — iLEAP: 5 decision gates, Express Pass, algorithmovigilance
- **Stanford Health Care** — RAIL; risk-tiered; integrated with DevOps release cycles
- **KPNC** — Early warning AI scaled from 2 to 19 hospitals; shadowing-based training model
- **Parkland Health** — Safety-net; lean governance; existing infrastructure + AI tags
- **UC San Diego** — COMPOSER sepsis model; role-differentiated; silent mode pre-deployment

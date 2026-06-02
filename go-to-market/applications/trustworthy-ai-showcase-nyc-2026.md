# Application: Trustworthy AI Showcase & Matchmaking NYC — 2026

Owner: Ashley Odom
Last updated: 2026-06-02

Application Q&A and presentation transcript for the Product Advisory Collective Trustworthy AI Showcase & Matchmaking event in NYC.

Event URL: https://www.productadvisorycollective.com/trustworthy-ai/showcase-and-matchmaking-nyc

---

## Q: Briefly, what is your mission or vision?

Our mission is to improve lives and impact outcomes with AI. Our vision is to become the known playbook and scaffolding that enterprise healthcare organizations leverage to deploy governed, compliant enterprise AI automation.

---

## Q: Explain what your AI product, tool or solution does and its value proposition.

For healthcare organizations who need to eliminate expensive, complex, manual processes, Keywell.ai is AI scaffolding that automates workflows on top of the customer's own data and cloud environment. Unlike SaaS platforms and point solutions, Keywell provides compounding value on a unified foundation.

**Target customers:** Mid-market regional health plans, TPAs, MCOs

**Key functionality:**

- **AI Scaffolding** — Architecture and governance in a box: infrastructure, single sign-on, enterprise control panel, guardrail settings, monitoring and incident flagging
- **Quickstarts** — Healthcare point solution applications ready to deploy on a unified foundation:
  1. Population Health Analytics Quickstart
  2. CMS-0057-F Prior Auth API Quickstart
  3. Intelligent Appeals Document Processing and Monitoring Quickstart
  4. HCC Continuous Audit Defensibility Quickstart
- **AI Sandbox** — Application for human testing and evaluation of AI workflows with real data prior to production

---

## Q: How is AI part of your solution?

We are an AI enablement solution. Configured AI agents enter various points in the workflow, such as:

1. **Population Health Analytics Quickstart** — AI agents translate user natural language queries into data analysis results, leveraging ontologies and our documented domain expertise
2. **CMS-0057-F Prior Auth API Quickstart** — AI agents translate unstructured plan coverage and utilization management policies into API responses
3. **HCC Audit Quickstart** — AI agents interpret clinical records and evaluate diagnosis code defensibility
4. **Appeals Intelligent Document Processing** — AI parses documentation, translates it to structured data, and disambiguates routing

"AI" — in the form of AI agents configured on our platform with guardrails — is one building block for workflow automation.

---

## Q: How does your solution differ from competitors' solutions or other existing alternatives?

Keywell is the only solution that delivers perpetual license ownership of the deployed platform and data, combined with a subscription to ongoing advancement (i.e., Quickstarts) — rather than locking customers into today's feature set.

**Status Quo (Existing EHR & SaaS Vendors)** — Waiting on vendor roadmaps means data silos persist and AI scope stays locked within each point solution, never spanning the enterprise. Keywell creates urgency with exact solutions to high-ROI pain points — acting now rather than waiting.

**Homegrown Build (Databricks AgentBricks, AWS Bedrock)** — Internal builds carry high risk, long timelines, and require rebuilding infrastructure Keywell already provides. We accelerate the build and skip the hard infrastructure work.

**Healthcare AI SaaS Platforms (Qualified Health, Hippocratic AI, Serelora)** — SaaS lock-in just trades one vendor dependency for another, and today's feature set will need to be reprocured as the landscape shifts. Keywell extends the existing infrastructure and lets customers own the capability.

**Non-Healthcare Enterprise AI (Claude/Anthropic, Salesforce Agentforce)** — Minimal healthcare-specific governance, auditability, or support for deterministic clinical workflows. Keywell offers model-agnostic architecture, zero-trust frameworks, and works complementary to these platforms.

**Healthcare AI Hybrid Platforms (101GenAI, Boost Health AI)** — Varied infrastructure sophistication and limited Databricks-native integration. Keywell provides deeper platform integration, SSO, and customer environment isolation.

---

## Q: Why does AI trustworthiness matter to your customers and users?

Healthcare is a high-impact, high-risk, highly-litigious industry. Trustworthiness is table stakes. So far, this is why trustworthiness matters to the customers in our pipeline:

1. **Patient privacy and HIPAA compliance**
2. **Auditability (interpretability / transparency)** — ensuring retracing and defensibility of AI-augmented or AI-automated decisions or processes
3. **Bias and equity** — ensuring that built-in racial or demographic biases do not cause harm
4. **Accountability** — ensuring that a human is responsible and accountable in the AI chain
5. **Automation bias** — ensuring that humans in the loop aren't just checking boxes

---

## Presentation — Live Showcase (2026-06-02)

**Slides:** https://docs.google.com/presentation/d/1_FMuz1rbbK9ZTdXxlxnRuZgfGHLm-cqVVZJBAA5eaLw/edit?usp=sharing

### Event Context

Hosted by Mary Beth Snodgrass, Managing Director/Founder at Product Advisory Collective. Two healthcare AI startups presented; Keywell was Startup #1. Audience included early-stage founders, tech founders, healthcare industry professionals, and AI judges. Judges: Professor Dimitriano (Boston University, AI trustworthiness research), Helen Lo Tempari (Morgan & Colby Paris / Data & AI Governance Intelligence), Claudia (EU AI Act researcher / EU statistician committee expert), Rod Siraj (AI governance advisor, former CIO/CTO in regulated financial services, ex-Mass Mutual / Amazon), Jamil (VP AI, State Street), Rio Yoshike (Trustee Program Lead, Autodesk), Mary Beth Snodgrass.

Trustworthiness characteristics evaluated by audience: accountability, privacy & security, explainability, fairness, robustness.

### Ashley's Presentation Transcript

Hi, I'm Ashley Cairns, founder and CEO of Keywell.ai.

The industry problem that we're addressing is that health plans are currently managing $200 billion in complex, expensive operational workflows like prior authorization, appeals, and audits across a patchwork of complex and expensive point solutions.

Our unique insight about this is that many healthcare point solutions are built on the same underlying data sources and logic controls and application patterns, and once those building blocks are deployed as reusable scaffolding, AI can be applied across these use cases in a way that makes each new workflow faster, cheaper, and safer to implement, so value compounds inside the customer's environment instead of fragmenting across disconnected systems.

Our team knows this, because we've built the industry systems that we're replacing. We've been in the industry trenches from the payer, provider, and public sector perspectives.

So, here's how we address the problem. Keywell deploys a foundation — we call it healthcare AI scaffolding — inside our customer environment with governance and security. We build in HIPAA compliance, PHI masking, private LLM models, and AI guardrails. So governance is operationalized inside the solution instead of in PDFs.

We deploy quickstart solutions for operational pain points — things like HCC chart validation, prior authorization, appeals management. These are all built on the scaffolding, and then they're configured to our customer-specific data sets and workflows, so using these quickstarts de-risks the implementation and accelerates value for our customers.

As I heard earlier, Trustworthy AI is table stakes for healthcare AI, and I'm going to show you eight ways that Keywell enables trustworthy AI. Our focus is in the areas of the operational layers that take imperfect LLMs and sometimes unpredictable LLM responses, and adds the operational layer and constraints on top of that to make it trustworthy.

**Trustworthy aspect #1 — Ownership model:** We deploy in the customer data environment on High Trust certified cloud platforms. The open framework we provide means that customers can use and extend their data and AI platform without data and system silos.

**Trustworthy aspect #2 — Governance control panel:** With our control panel, you can view and configure agents that power operational workflows. You can swap out models, so you don't have required loyalty to any given LLM foundation model. These agents can also be deployed into legacy systems via API, while still being controlled and managed internally.

**Trustworthy aspect #3 — Complete audit trails:** We have complete audit trails and monitoring dashboards. We're able to recreate reasoning breakdowns and reconstruct point-in-time decisions, so we can see each step in an LLM decision audit.

**Trustworthy aspect #4 — Guardrail agents:** Agents are given a limited scope of practice — back to the foot surgery versus GI doctor analogy — so you can set limited scopes and monitor any attempted violations of the limitations.

**Trustworthy aspect #5 — Evaluation sandbox:** Workflows and agents can be tested in our evaluation sandbox, allowing reviewers and subject matter experts to review LLM responses on real-world data before going into production.

**Trustworthy aspect #6 — Granular permissions and accountability:** We have granular permissions at the row, column, document source, and agent level. It's a zero trust system. The user must have access to the agent, the data source, and all of the resources in the chain in order to access information.

**Trustworthy aspect #7 — Limited degrees of freedom:** To limit bias and compliance risk due to verbose LLM responses, outputs are constrained to validated criteria which can then be used by humans or agents to make decisions — structuring the information in a validated set of data elements.

**Trustworthy aspect #8 — Human in the loop:** The workflows allow human in the loop with meaningful input at high impact decision points, like in prior authorization or HCC validation.

Our approach to customer success is to start with one high-value workflow, and then map the reusable scaffolding underneath it — things like the data governance, guardrails, and workflow logic. The blueprint we provide shows how a first deployment can become the foundation for a broader, trustworthy AI roadmap.

### Judge Q&A (partial transcript)

**Claudia (EU AI Act researcher):** *[Kudos on taking governance into account compared to many startups.]* Two questions: (1) On autonomy containment — how do you know what are your explicit containment boundaries that prevent your system from initiating actions, chaining tasks, or escalating autonomy beyond what the organization has formally approved, especially when integrating with third-party tools or APIs? (2) [Decision integrity controls — transcript cut off]

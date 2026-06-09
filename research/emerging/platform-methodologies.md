# Emerging Platform Methodologies

Ideas, standards, and research findings worth tracking for potential application to the Keywell platform. Not current roadmap — exploratory.

---

## Model Interoperability

### MEDS — Medical Event Data Standard

**Source:** [NEJM AI, 2025 — AIra2501253](https://ai.nejm.org/doi/full/10.1056/AIra2501253) *(paywalled — read full article for details)*

**What it is:** MEDS is an emerging open data standard designed to represent patient data as sequences of timestamped medical events in a consistent, dataset-agnostic format. It was developed to address the core interoperability problem in health AI: models trained on one EHR system or claims dataset rarely transfer cleanly to another because underlying data structures differ across institutions and vendors.

**The problem it solves:** Healthcare ML researchers and teams rebuilding the same preprocessing pipelines repeatedly for each new data source — Epic vs. Cerner vs. claims vs. ADT feeds all look different. MEDS proposes a shared schema so that a model trained on one population can be evaluated or fine-tuned on another without re-engineering the data layer.

**Core concept:** Patient data is expressed as a flat, ordered sequence of `(patient_id, timestamp, event_type, value)` tuples. This event-based representation is intentionally simple — designed to be lossy enough to be broadly applicable, but expressive enough to support supervised learning, risk modeling, and foundation model pretraining.

**Ecosystem:** Companion tooling includes MEDS-Transforms (ETL to convert raw EHR/claims data into MEDS format) and MEDS-Evaluation (standardized benchmarking across MEDS-formatted datasets).

**Relevance to Keywell:**
- Directly relevant to our multi-source data integration work (Epic, Cerner, claims, ADT, TEFCA)
- Could inform how we structure longitudinal patient models in Unity Catalog for cross-client reusability
- Potential alignment with Keywell's healthcare data ontologies — MEDS could serve as a normalization target or complement to Tuva/AHRQ ontologies
- Worth evaluating as a foundation model pretraining format if Keywell pursues proprietary health AI model development
- May be relevant to proposals where clients want model portability or the ability to benchmark against external datasets

**Status:** Exploratory — monitor adoption in the research community. NEJM AI publication signals academic credibility; watch for payer/provider adoption signals before building to the standard.

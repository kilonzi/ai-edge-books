# The 5 AI Models You Should Know

From the book: The AI Edge for Real Estate

---

## Executive Summary

AI is no longer a back-office experiment. It’s leaping into leasing desks, asset management workflows, development sites, and tenant experiences. But you don’t need to master every neural network to drive results. You need a mental model—five, in fact. Think of AI capabilities as five distinct model families that map cleanly to real estate business outcomes:

- Large Language Models (LLMs): read, write, reason over language and documents.
- Computer Vision (CV): see and interpret images and video.
- Predictive Analytics: forecast what will happen next.
- Recommendation Engines: suggest the next best property, product, or action.
- Process Automation: orchestrate tasks and decisions end‑to‑end.

Each of these model types is practical today. In this chapter, you’ll learn what they are, where they fit, the tools to use, and the pitfalls to avoid—so you can sponsor projects with confidence and hold your teams to measurable, commercial outcomes.

---

## A Simple Mental Model: Read • See • Predict • Suggest • Do

Use this framework to anchor conversations with your team.

- Read (LLMs): “We need to understand and generate language.”
- See (Computer Vision): “We need to interpret imagery or video.”
- Predict (Predictive Analytics): “We need to forecast a number or a probability.”
- Suggest (Recommendation Engines): “We need to rank the best options for a person or context.”
- Do (Process Automation): “We need to automate the workflow reliably.”

> Soundbite for your next leadership meeting: “If it’s language, use LLMs. If it’s imagery, use computer vision. If it’s a future number, use predictive analytics. If it’s about choices, use recommendations. If it’s a repeatable workflow, automate it.”

### Model Families at a Glance

| Model Type | What It Does | Typical Real Estate Data | Core Business Questions | Representative Tools |
|---|---|---|---|---|
| Large Language Models (LLMs) | Reads/writes natural language; reasons over text and structured data; chat and copilots | Leases, addenda, LOIs, emails, policies, RFIs, RFPs, maintenance tickets, marketing copy | What’s in this lease? Draft a response. Summarize due diligence. Answer tenant questions. | OpenAI GPT-4o, Azure OpenAI, Anthropic Claude, Google Gemini; LangChain, LlamaIndex; Pinecone/Weaviate (RAG) |
| Computer Vision | Detects objects, classifies, measures, and segments images/video | Drone images, roof scans, unit photos, site CCTV, parking lot cameras | What’s damaged? How many vacant spots? Are safety risks present? | YOLOv8, Detectron2, Segment Anything, OpenCV; Roboflow; AWS Rekognition; Google Vertex AI Vision |
| Predictive Analytics | Forecasts values and probabilities (time-series and tabular) | Rents, occupancy, leads, maintenance logs, comps, economic indicators | What will rent be next quarter? Which lead will convert? Which unit will churn? | scikit-learn, XGBoost/LightGBM, Prophet, H2O.ai, DataRobot, BigQuery ML, Azure AutoML |
| Recommendation Engines | Ranks items for users; personalizes content or actions | Listings, amenities, user clicks, searches, tours, conversions | Which properties to show? Which amenities to upsell? What’s the next best action? | LightFM, implicit, NVIDIA Merlin, Amazon Personalize, Vertex AI Matching; Redis/FAISS for ANN |
| Process Automation | Executes workflows with rules and AI; integrates systems | PDFs, forms, inboxes, PMS/CRM/ERP data, billing, compliance docs | Can we automate lease intake? AP invoices? Lead routing? Compliance checks? | UiPath, Automation Anywhere, Microsoft Power Automate; AWS Textract, Google Document AI, Azure Form Recognizer |

---

## 1) Large Language Models (LLMs): Your Portfolio’s Language Copilot

### What LLMs Are (In Plain English)

Large Language Models are software that can read, write, and reason across natural language. Feed them a lease, an email thread, a policy manual, or a maintenance ticket—they can summarize, extract key terms, answer questions, and draft responses. LLMs are best when the problem involves language comprehension or generation. With retrieval-augmented generation (RAG), they can also ground answers in your own documents to improve accuracy and reduce hallucinations.

### Where LLMs Fit in Real Estate

- Lease abstraction and comparison at scale
- Due diligence Q&A across data rooms
- Tenant and resident support chat (self-service and agent-copilot)
- Marketing copy, listing descriptions, and localization
- Policy and compliance assistants (e.g., Fair Housing safe phrasing)
- Vendor and RFP response drafting
- Maintenance triage and instruction generation

### Two Real-World Examples

1) Lease Abstraction Copilot for Asset Managers

- Problem: Teams manually review hundreds of leases to answer questions like “Who pays the roof?” “Is there a co-tenancy clause?” “What are escalation triggers?”
- Solution: An LLM with RAG ingests leases, addenda, and amendments; exposes a chat interface with citations; exports structured fields to your asset management system.
- Impact: Weeks reduced to hours; fewer missed obligations; standardized outputs for underwriting.

2) Resident Support Assistant for Multifamily

- Problem: Repetitive questions (“How do I reset my fob?” “Pet policy?” “What’s my balance?”) swamp staff.
- Solution: An LLM grounded on your building handbook, policy PDFs, and knowledge base; authenticated for account-specific info through APIs; integrated into web/app chat.
- Impact: 40–70% deflection of Tier 1 tickets; faster response times; measurable CSAT lift.

Additional niche uses: drafting broker opinion of value (BOV) summaries; translating construction RFIs; summarizing inspector notes; generating unit turn checklists.

### What “Good” Looks Like (Metrics and Operating Model)

- Accuracy: percent of extracted fields correct; citation coverage in answers; “hallucination rate” under a defined threshold.
- Productivity: time-to-first-draft and end-to-end cycle time; cases handled per FTE.
- Compliance: redline sensitivity to prohibited terms; adherence to style and policy templates.
- Experience: CSAT, resolution time, deflection rate for support scenarios.

Operate with human-in-the-loop, especially for high‑risk outputs (lease terms, compliance notices). Use approval queues and structured prompts (templates) to keep outputs consistent.

### Implementation Blueprint

1) Scope and Data

- Prioritize a single document family first (e.g., retail leases or multifamily leases—not both).
- Gather 50–500 representative documents including edge cases (amendments, scanned copies, addenda).
- Label 30–50 ground-truth examples (key fields, clause types) for evaluation.

2) Architecture

- RAG: index documents in a vector database (Pinecone, Weaviate, FAISS). Chunk by logical sections (clauses, exhibits) with metadata (tenant, year, property, doc type).
- Model: start with GPT‑4o, Claude, or Gemini for quality; consider smaller open-source LLMs for on‑prem/security needs.
- Orchestration: LangChain/LlamaIndex to handle retrieval, prompt construction, and tool calls (e.g., calculators for escalations).
- Guardrails: use content filters, prompt injection defenses, and citation requirements.

3) Controls and Governance

- Data privacy: redact PII where not needed; ensure SOC2/ISO/tenant contract alignment.
- Legal: adopt “AI assistance” disclaimers internally; require human review for high‑dollar outputs.
- Auditability: store prompts, answers, citations, and document version hashes.

4) Rollout

- Pilot with 5–10 users and 200–2,000 documents.
- Compare to manual baselines; track error types; iterate prompt templates.
- Expand to neighboring document types (SNDA, estoppels) once stable.

### Relevant Tools and Platforms

- Foundation models/APIs: OpenAI (GPT‑4o family), Azure OpenAI Service, Anthropic Claude, Google Gemini.
- Retrieval and indexes: Pinecone, Weaviate, Qdrant, FAISS; Elasticsearch with vector support.
- Orchestration: LangChain, LlamaIndex.
- Document AI: AWS Textract, Google Document AI, Azure Form Recognizer for OCR and form parsing.
- Guardrails and safety: Azure AI Content Safety, OpenAI moderation, Guardrails.ai, Honeytoken patterns for prompt injection detection.

### Implementation Checklist: LLMs

- [ ] Clear business owner and risk owner identified.
- [ ] Gold‑standard evaluation set defined (n≥30 cases) with pass/fail criteria.
- [ ] Retrieval index built with citations; hallucination guardrails in place.
- [ ] Authentication and data access reviewed with security.
- [ ] Human‑in‑the‑loop approval for high‑impact decisions.
- [ ] Monitoring dashboards for accuracy and usage.

---

## 2) Computer Vision: From Photos and Video to Decisions

### What Computer Vision Is (In Plain English)

Computer Vision teaches machines to interpret images and video: detect objects, measure damage, segment areas, count people or cars, and flag anomalies. The models range from simple classifiers (“is there mold?”) to detectors (“where is the mold?”) to segmenters (“how much area is affected?”). In real estate, imagery is abundant—unit turns, inspections, drone flights, parking lots, lobbies, construction sites.

### Where Computer Vision Fits in Real Estate

- Property inspections: damage detection (mold, leaks, cracked tiles, missing outlet covers)
- Capital planning: roof condition from drone imagery; facade cracks; pavement deterioration
- Operations: parking utilization, amenity usage, line length monitoring, safety PPE compliance on job sites
- Security and safety: hazard detection (blocked egress, fallen objects); perimeter anomalies
- Marketing operations: photo quality scoring, de-duplication, room type classification

### Three Real-World Examples

1) Turnover Inspection Assistant (Multifamily)

- Problem: Unit turn inspections are inconsistent; photos live in emails; estimates vary by tech.
- Solution: A mobile app that uploads photos/video to a vision service. The model detects common issues (paint scuffs, appliance rust, missing smoke detector batteries), estimates severity/area, and suggests SKU-level repair items with standard labor hours.
- Impact: 25–40% cycle-time reduction; tighter variance between estimated and actual turn costs; better vendor negotiations with standardized scope data.

2) Roof and Facade Assessment from Drones (Commercial/Industrial)

- Problem: Manual roof walks are slow and hazardous; missed early-stage issues become costly.
- Solution: Drone images stitched into orthomosaics; vision models segment roof membranes, identify ponding, seam failures, and vegetation; generate geo-tagged remediation punch lists.
- Impact: Preventive maintenance savings; safer inspections; evidence for insurance and CapEx planning.

3) Parking and Amenity Utilization (Mixed-Use)

- Problem: Underused amenities and misaligned parking allocations erode NOI.
- Solution: Edge cameras count vehicles and people; models calculate peak usage by time/day; data feeds into dynamic signage or access policies.
- Impact: Reallocate space, adjust leasing packages, and price amenities based on demand.

### What “Good” Looks Like

- Model quality: mAP (mean average precision), IoU (intersection over union), and per-class precision/recall.
- Operational reliability: edge failures per 1,000 hours; latency for real-time alerts; offline buffering.
- Business outcomes: reduction in inspection time, cost avoidance, safety incidents prevented.

### Implementation Blueprint

1) Data Sourcing and Labeling

- Start with your existing inspection photo archives and drone image sets.
- Label 1,000–5,000 images per class for a strong baseline; use a labeling service or tools like Label Studio or Roboflow Annotate.
- Define a taxonomy: what counts as minor/major? What classes are in scope now vs later?

2) Models and Deployment

- Object detection: YOLOv8, Detectron2 for on‑device/edge capability. Segment Anything + task-specific heads for damage areas.
- Cloud vision: AWS Rekognition Custom Labels, Google Vertex AI Vision for managed training/inference.
- Edge hardware: NVIDIA Jetson for onsite processing where connectivity is limited.

3) Privacy, Policy, and Risk

- Avoid facial identification; mask faces automatically where possible.
- Signage and consent policies for CCTV; align with local regulations.
- Retention: store derived events vs raw video when feasible.

4) Integration to Workflows

- Push detections to CMMS/maintenance systems as tickets with photos and bounding boxes.
- For roof/facade maps, export GIS layers into your asset management platform.
- Build QA loops: allow techs to confirm/correct model suggestions to improve accuracy over time.

### Relevant Tools and Platforms

- Open-source CV: OpenCV, YOLOv8, Detectron2, Segment Anything (SAM), Mask R‑CNN.
- Labeling: Label Studio, Roboflow, CVAT.
- Cloud: AWS Rekognition, Google Vertex AI Vision, Azure Custom Vision.
- Edge and MLOps: NVIDIA Jetson, Triton Inference Server; MLflow for experiments.

### Implementation Checklist: Computer Vision

- [ ] Clear safety and privacy policy documented; signage and retention reviewed.
- [ ] Data labeling guidelines, with inter‑rater agreement checks.
- [ ] Edge/camera hardware plan with network resilience.
- [ ] Integration to ticketing/CMMS; feedback loop for corrections.
- [ ] Bias/accuracy monitored by location/lighting/season.

---

## 3) Predictive Analytics: Forecasting Rents, Tenants, and Risk

### What Predictive Analytics Is (In Plain English)

Predictive analytics estimates what will happen next: a future value (rent, demand, days on market) or the likelihood of an event (a lead converts, a tenant churns, a pump fails). Most solutions rely on classical machine learning—gradient boosting, random forests, logistic regression—or time‑series models, often enhanced with external signals.

### Where Predictive Analytics Fits in Real Estate

- Revenue: rent and occupancy forecasting; dynamic pricing support; renewal probability
- Leasing: lead scoring and conversion probability; show/no‑show prediction
- Operations: preventive maintenance (failure probability); work order duration; vendor performance
- Investment: market selection and comp analysis; hold/sell signals; cost-to-complete risk on projects
- Marketing: channel performance; budget allocation; seasonality adjustments

### Three Real-World Examples

1) Rent and Occupancy Forecasting (Multifamily)

- Problem: Budget forecasts are manual; miss turning points in seasonal demand.
- Solution: A hybrid time‑series model combines internal data (floor plan, unit features, historical rent/occupancy, concessions) with external signals (job growth, inventory, school calendars, local events).
- Impact: Improved pricing decisions; better staffing and marketing timing; lower vacancy loss.

2) Renewal and Churn Prediction (Multifamily/Student Housing)

- Problem: Late recognition of churn risk leads to last‑minute concessions and vacancies.
- Solution: A classification model scores residents by renewal probability using features like work order history, on‑time payments, amenity usage, tenure, noise complaints, and market rent deltas.
- Impact: Targeted outreach and renewal offers; cross‑sell of storage/parking to at‑risk segments; measurable uplift in renewals.

3) Preventive Maintenance for Critical Assets (Commercial/Industrial)

- Problem: HVAC and pumps fail unexpectedly; parts and labor delays exacerbate downtime.
- Solution: A survival model or gradient boosting classifier predicts failure windows based on sensor readings, run hours, ambient conditions, and maintenance logs.
- Impact: Fewer outages; lower emergency callouts; optimized inventory and scheduling.

### What “Good” Looks Like

- Model quality: for regression, MAE/RMSE; for classification, AUC/PR‑AUC, precision/recall at business thresholds.
- Decision quality: lift over baseline strategies (e.g., targeted retention vs blanket offers); calibration curves to ensure predicted probabilities match observed outcomes.
- Financial impact: revenue lift, cost avoidance, and cash flow stability; measured through A/B tests or phased rollouts.

### Implementation Blueprint

1) Data and Features

- Start with 12–36 months of historicals; the more cycles, the better.
- Feature engineering: unit attributes, amenity sets, floor, view, distance to transit; marketing touches; economic indicators (unemployment, new supply, permits).
- Treat data leakage: ensure features available at prediction time; avoid peeking into the future.

2) Modeling and Validation

- Baselines: linear models and decision trees for interpretability.
- Winners: gradient boosting (XGBoost/LightGBM/CatBoost) often deliver top performance on tabular data.
- Time series: Prophet for simple seasonal patterns; gradient-boosted or deep temporal models for complex signals; hierarchical reconciliation for portfolio/market rollups.
- Validation: time‑based cross‑validation; backtesting to mimic live deployment.

3) Deployment and MLOps

- Batch scoring (daily/weekly) for forecasts; real‑time scoring for lead routing.
- Monitor drift: feature distributions, stability index, and outcome drift; retrain schedules.
- Explainability: SHAP values for feature importance; provide reason codes for actions (useful for governance and sales scripts).

4) Human in the Loop

- Provide override controls with reason capture.
- Build playbooks: what marketing offer or pricing change to make at each risk or demand tier.

### Relevant Tools and Platforms

- Libraries: scikit‑learn, XGBoost, LightGBM, CatBoost, Prophet.
- AutoML: H2O.ai, DataRobot, BigQuery ML, Azure AutoML, Dataiku.
- Data engineering: dbt, Fivetran/Stitch, Airflow; cloud warehouses (Snowflake, BigQuery, Redshift, Databricks).
- Monitoring: Evidently AI, WhyLabs, MLflow, Arize AI.

### Implementation Checklist: Predictive Analytics

- [ ] Business hypothesis and decision map (what will change as scores change?).
- [ ] Data readiness: at least 12 months history; leakage checked; external signals identified.
- [ ] Backtest and champion‑challenger comparison documented.
- [ ] Action playbooks approved; experiment design for uplift measured.
- [ ] Monitoring for drift and recalibration.

---

## 4) Recommendation Engines: Matchmaking for Properties, Amenities, and Actions

### What Recommendation Engines Are (In Plain English)

Recommendation engines personalize choices: they rank items (properties, floor plans, amenities, content) for each user or context. They learn from behavior—clicks, saves, tours, messages—and from item attributes—location, price, bedrooms, amenities. There are three approaches:

- Content‑based: match user preferences to item attributes.
- Collaborative filtering: “people like you liked these properties.”
- Hybrid: blend both and re‑rank in real time using context (device, time of day, location, channel).

### Where Recommendations Fit in Real Estate

- Property discovery: personalize search results, email listings, and on‑site modules
- Amenity/upgrade bundles: parking, storage, pet packages, smart locks, furnished options
- Agent/broker tools: next‑best actions (who to call, which comp to cite)
- Marketing: dynamic content blocks; retargeting creatives chosen per user

### Two Real-World Examples

1) Property-to-Buyer Recommendation (Residential Brokerage)

- Problem: Portals and broker sites show the same generic results; high bounce rates; agents waste time curating manually.
- Solution: A hybrid recommender learns from a buyer’s clicks, saves, and viewing history; incorporates constraints (budget, commute time, school ratings); re‑ranks listings daily as inventory changes.
- Impact: Higher lead engagement and agent productivity; lower time‑to‑tour; improved conversion from inquiry to offer.

2) Amenity Bundle Uplift (Multifamily)

- Problem: Parking/storage/pet add‑ons are under‑adopted; blanket offers leave money on the table.
- Solution: A recommender predicts the amenity bundle most likely to be accepted at offer time, considering unit type, household, pet ownership signals, and building demand.
- Impact: Increased ancillary revenue and resident satisfaction; reduced churn from better fit.

### What “Good” Looks Like

- Relevance: click‑through rate (CTR), save rate, tour request rate, conversion at top‑N.
- Fairness and compliance: avoid discriminatory steering; provide transparent filters and explainability.
- Diversity and serendipity: avoid narrow loops by injecting diversity; measure coverage across inventory and neighborhoods.

### Implementation Blueprint

1) Data and Cold Start

- Start with catalog quality: complete and standardized attributes across listings and amenities.
- Collect behavioral signals ethically (consent, privacy compliance).
- Solve cold start: use content‑based ranking at first interaction; then blend in collaborative filtering as data accrues.

2) Modeling and Serving

- Baselines: popularity and simple rules (new, nearby, price‑fit) for control.
- Models: matrix factorization (implicit ALS), LightFM (hybrid), gradient boosted rankers (XGBoost rank), or deep learning with two‑tower architectures (NVIDIA Merlin).

3) Re‑ranking and Business Rules

- Re‑rank based on constraints (availability, price, compliance) and context (channel, time of day).
- Guardrails: enforce Fair Housing policies; allow users to adjust preferences explicitly.

4) Measurement and Optimization

- Run A/B tests; track online metrics (CTR, conversion) and offline quality (relevance labels from agents).
- Balance multiple objectives: engagement, revenue, fairness, inventory coverage.

### Relevant Tools and Platforms

- Libraries: implicit, LightFM, Surprise; ranking with XGBoost/LightGBM; TensorFlow Recommenders, PyTorch, NVIDIA Merlin.

- Managed: Amazon Personalize, Google Vertex AI Matching Engine, Azure AI Personalizer alternatives and custom rankers.

- Real‑time infra: Redis for feature caching; approximate nearest neighbor (ANN) search with FAISS or ScaNN.

### Implementation Checklist: Recommendations

- [ ] Inventory data quality audit; missing attributes filled.
- [ ] Privacy and Fair Housing guardrails documented; explainability UX.
- [ ] Baseline/rule‑based control in place for A/B comparison.
- [ ] Offline and online metrics defined; A/B platform ready.
- [ ] Feedback loops from agents/residents captured.

---

## 5) Process Automation: AI That Gets Work Done

### What Process Automation Is (In Plain English)

Process automation orchestrates tasks and decisions across systems, people, and documents. Think of it as end‑to‑end glue that uses rules and AI components (LLMs, vision, predictive scores) to move work forward. Robotic Process Automation (RPA) excels at structured, repetitive tasks; Intelligent Document Processing (IDP) reads PDFs and forms; decision engines route cases; and copilot interfaces keep humans in control.

### Where Automation Fits in Real Estate

- Lease intake: ingest PDFs, extract fields, route for legal review, push to PMS/ERP
- Accounts payable: read invoices; 3‑way match; route exceptions; post to GL
- Lead management: de‑duplicate, score, route to agents; auto‑schedule tours
- Compliance: collect certificates of insurance, W‑9s; validate; chase expirations
- Turn management: auto‑create work orders based on inspection outputs; schedule vendors; update residents

### Two Real-World Examples

1) End-to-End Lease Intake and Abstraction

- Problem: New leases arrive in varied formats; data entry is error‑prone and slow; downstream systems are out of sync.
- Solution: An automation that watches an intake mailbox and data room folders. IDP extracts parties, term, rent schedule, option clauses. An LLM validates and highlights ambiguous terms for legal review. Approved data flows into PMS and the deal system. Exceptions spawn tasks with links to exact clauses.
- Impact: Faster revenue recognition; fewer data errors; audit trail for compliance.

2) Accounts Payable with Exception Handling

- Problem: AP spends time on low‑value tasks (coding, matching) and misses fraud signals.
- Solution: IDP reads invoices; predictive model flags anomalies; rules engine performs 3‑way match; RPA posts approved vouchers; LLM drafts vendor emails for exceptions.
- Impact: Shorter cycle times; early‑pay discounts; reduced leakage; happier vendors.

### What “Good” Looks Like

- Throughput and SLA: average handle time; percent straight‑through processing (STP).
- Quality: exception rate; rework; accuracy of extracted fields.
- Control: audit logs; role‑based access; segregation of duties.
- Experience: fewer handoffs; clear visibility of work queues.

### Implementation Blueprint

1) Discover and Map

- Map the current state with swimlanes, systems, and handoffs.
- Identify top exceptions and decision points; prioritize for automation.

2) Design the Target State

- Break into micro‑flows: intake, classify, extract, validate, route, post, notify.
- Insert AI at the right spots: LLM for triage and draft responses; IDP for fields; predictive models for risk scoring.

3) Build and Pilot

- Use low‑code workflow tools (UiPath, Automation Anywhere, Microsoft Power Automate) integrated with your systems via APIs.
- Include human approval steps for high‑risk actions.

4) Operate and Improve

- Monitor STP, exceptions, and business outcomes (DPO, revenue time-to-post, etc.).
- Add automations incrementally; retire manual steps.

### Relevant Tools and Platforms

- RPA/Workflow: UiPath, Automation Anywhere, Microsoft Power Automate, Zapier/n8n for lighter use.
- IDP/OCR: AWS Textract, Google Document AI, Azure Form Recognizer.
- Orchestration: Airflow, Temporal for complex backend flows.
- Observability: process mining (Celonis, UiPath Process Mining).

### Implementation Checklist: Process Automation

- [ ] Process map with happy path and exception paths.
- [ ] Business rules codified; decision tables reviewed with finance/legal.
- [ ] AI components sandboxed with metrics and fallback logic.
- [ ] Role‑based approvals and audit logging.
- [ ] SLA dashboard and continuous improvement cadence.

---

## Choosing the Right Model: A Decision Playbook

Use this matrix to pick a model family quickly.

| If your problem is… | Ask this question | Likely model | Example |
|---|---|---|---|
| Text-heavy documents and Q&A | “Do we need to understand or generate language?” | LLM (with RAG) | Lease abstraction; policy assistant |
| Images/videos to interpret | “Do we need to detect or measure visual features?” | Computer Vision | Turn inspections; roof assessment |
| Forecasting a number or probability | “Do we need to predict a future value or risk?” | Predictive Analytics | Rent forecast; churn risk |
| Personalizing choices | “Do we need to rank items for a person/context?” | Recommendation Engine | Property matching; amenity bundles |
| End-to-end workflow execution | “Do we need to orchestrate tasks reliably?” | Process Automation | Lease intake; AP |

> Rule of thumb: Many real outcomes need more than one model. For example, automated lease intake typically combines IDP + LLM (for clauses) + Process Automation (for routing). Start with the core capability, then add complementary models.

---

## The Five-Point Readiness Checklist (RSPSD Framework)

Before green‑lighting any AI initiative, run this checklist:

1) Real Problem

- Can you state the business outcome in one sentence? (e.g., “Reduce turn time by 30%.”)
- Is there a willing process owner? A budget? A deadline?

2) Suitable Data

- Do you have representative, labeled examples? Are there gaps (e.g., missing unit attributes)?
- Can you legally use the data for this purpose? Are tenants or vendors impacted?

3) Practical Solution

- Is there a simpler rule‑based baseline? Can we beat it?
- Does the model type match the problem (Read/See/Predict/Suggest/Do)?

4) Safe and Compliant

- Have you defined guardrails (e.g., Fair Housing, privacy, surveillance policies)?
- Do high‑impact decisions require human approval and audit logs?

5) Deliverable ROI

- What is the quantifiable value (revenue, cost, risk) and timeframe?
- How will we measure uplift? Is there an A/B or phased rollout plan?

---

## Build vs Buy: A Practical Matrix

| Factor | Buy (SaaS/Managed) | Build (Custom/Internal) |
|---|---|---|
| Speed to value | Fast; pre‑built integrations | Slower; discovery and engineering needed |
| Differentiation | Commodity features | Tailored to your process; competitive edge |
| Data sensitivity | Vendor access; contractual controls | Keep data in your VPC/on‑prem |
| Flexibility | Feature roadmap set by vendor | Full control; integrate any model |
| Talent required | Moderate (admins, analysts) | Higher (data engineers, ML, DevOps) |
| Cost profile | Subscription + usage | Fixed + variable engineering; infra |
| Risk | Lower operational risk | Higher delivery risk; more control |

Decision guide:

- Buy when… the capability is not strategic (e.g., general IDP for invoices), or when time-to-value trumps uniqueness.
- Build when… it touches your core differentiation (e.g., proprietary pricing signals, broker copilot with your secret sauce), or when data sensitivity is high.

Hybrid is common: buy the foundation (models/tools), customize the last mile (prompts, retrieval, business rules, UI).

---

## Data Architecture for the Five Models

- Source systems: PMS, CRM, ERP, ticketing, marketing, access control, IoT sensors.
- Data lake/warehouse: stage and curate historical data; enforce master data for properties/units/tenants.
- Feature store: share features across predictive and recommendation models.
- Vector database: index documents and images for LLM/CV retrieval (Pinecone, Weaviate).
- Event streaming: capture behavioral signals (clicks, tours) for recommendations; Kafka/Kinesis or equivalent.
- Governance: data catalog (lineage, ownership), access policies, retention schedules.

Integration patterns:

- Batch: nightly or hourly scoring for forecasts and inventory feeds.
- Real‑time: APIs and webhooks for lead routing, recommender re‑ranking, and chatbots.
- Edge: on‑prem inference for camera feeds and low‑latency safety alerts.

---

## Governance, Ethics, and Risk: The Non‑Negotiables

- Privacy and consent: Respect privacy laws (e.g., data protection regulations) and lease agreements; avoid capturing unnecessary PII; anonymize where possible.
- Fair Housing and non‑discrimination: Ensure recommenders and pricing support do not steer protected classes; document acceptable features and provide explainability.
- Surveillance and safety: If using cameras, disclose and limit usage to legitimate interests (safety, asset protection); minimize retention and access.
- Human accountability: Keep humans responsible for material decisions; document who approves and why.
- Documentation: Maintain model cards (purpose, data, limitations), evaluation logs, and change history.
- Incident response: Playbooks for model failure, data breach, or erroneous automated decisions.

---

## Metrics That Matter: A Cross‑Model Scorecard

| Model Type | Technical Metrics | Business Metrics |
|---|---|---|
| LLMs | Extraction F1, grounded citation rate, hallucination rate, response latency | Time‑to‑first‑draft, deflection rate, accuracy of critical fields |
| Computer Vision | mAP, IoU, false positive/negative rates, edge uptime | Inspection cycle time, cost avoidance, safety incidents |
| Predictive Analytics | RMSE/MAE (regression), AUC/PR‑AUC (classification), calibration | Revenue lift, churn reduction, maintenance savings |
| Recommendation Engines | CTR, conversion@K, coverage/diversity, latency | Lead engagement, tours scheduled, ancillary revenue |
| Process Automation | STP rate, exception rate, AHT, SLA adherence | DPO, time‑to-post, staff capacity, error reduction |

Use both technical and business metrics. The model isn’t “done” until it reliably moves a business KPI.

---

## 90-Day Roadmaps: Quick Wins for Each Model Type

Use these templates to accelerate pilots and avoid scope creep.

### LLMs (Lease Abstraction Pilot)

- Days 1–15: Curate 200 leases; define fields; label 30 gold examples; set acceptance criteria.
- Days 16–45: Build RAG index; integrate GPT‑4o/Claude; implement citation‑required prompts; human review UI.
- Days 46–75: Evaluate on gold set; tune prompts; add edge cases (amendments); connect to asset system.
- Days 76–90: Pilot with 5 users; measure accuracy and cycle time; document ROI and go/no‑go for scale.

### Computer Vision (Turn Inspection Pilot)

- Days 1–15: Gather 5,000 labeled images (top 10 defect classes); standardize photo capture.
- Days 16–45: Train YOLOv8 baseline; test on new units; build feedback capture in field app.
- Days 46–75: Integrate with CMMS; add severity scoring; define SLA for auto‑created tickets.
- Days 76–90: Run in 3 properties; compare cycle time and variance vs control properties.

### Predictive Analytics (Renewal Risk Pilot)

- Days 1–15: Assemble 24 months data; define churn label; check leakage.
- Days 16–45: Train gradient boosting models; calibrate; backtest; define intervention tiers.
- Days 46–75: Integrate scores into CRM; agent playbooks; launch controlled test.
- Days 76–90: Measure uplift; refine features; set retrain cadence.

### Recommendation Engines (Property Personalization Pilot)

- Days 1–15: Audit listing attributes; instrument click/save events; define evaluation metrics.
- Days 16–45: Build hybrid baseline (content + popularity); stand up ANN search; launch A/B harness.
- Days 46–75: Train collaborative model; add re‑ranking rules; fairness checks.
- Days 76–90: Run A/B test; measure CTR and tours; iterate.

### Process Automation (AP Automation Pilot)

- Days 1–15: Map process; select top 3 vendor types; define exception rules.
- Days 16–45: Configure IDP; build RPA flows; integrate with ERP test environment.
- Days 46–75: Pilot with 1–2 properties; tune rules; train exception handlers; add LLM email drafts.
- Days 76–90: Expand to 5 properties; measure STP and DPO; finalize scale plan.

---

## Common Pitfalls and How to Avoid Them

- Starting with the fanciest model: Begin with the simplest baseline that can move the KPI. Prove lift, then iterate.
- Fuzzy success criteria: Define pass/fail and business metrics before you start. No goalposts on wheels.
- Data blind spots: You cannot fix missing unit attributes or inconsistent lease terms with modeling magic. Clean the data.
- Model without workflow: A great prediction with nowhere to go is shelfware. Design the decision and action path up front.
- Ignoring governance: Fair Housing, privacy, and surveillance risks are real. Involve legal and compliance early.
- One‑time projects: Treat models as products. Monitor, retrain, support, and improve them.

---

## Tooling Map by Persona

- Executives and Asset Owners
  - Dashboards tying models to NOI and risk.
  - Approval checkpoints for high‑impact automations.
- Operations and Property Managers
  - Copilots embedded in daily tools; clear exceptions queues.
  - Mobile capture apps for inspections.
- Leasing and Marketing
  - Lead scoring and next‑best action in CRM; content assistants for listings.
- Data/IT
  - Central data lakehouse; feature store; vector DB for RAG; CI/CD for models; observability.

---

## Real Estate Case Vignettes (Putting It All Together)

1) The Automated Turn

- Inputs: Move‑out notice triggers workflow; photos/video captured by maintenance; CV detects defects; LLM drafts resident charges letter with citations from the lease; predictive model estimates time-to-ready; automation schedules vendors and updates PMS.
- Outcome: 30% faster turns; fewer disputes; consistent standards across properties.

2) The Intelligent Brokerage Pipeline

- Inputs: Web/app activity feeds into recommender; predictive model scores leads; LLM drafts outreach; automation schedules tours and updates CRM; agent copilot suggests comps.
- Outcome: Higher lead-to-close conversion; improved agent productivity; better client experience.

3) The Portfolio QBR Copilot

- Inputs: LLM reads leases, budget vs actuals, maintenance logs; predictive models forecast occupancy and capital needs; automation assembles a QBR deck with charts and risk highlights.
- Outcome: Faster, deeper quarterly reviews; better capital allocation decisions.

---

## A Glossary You Can Use in Meetings

- RAG (Retrieval‑Augmented Generation): A method to ground LLMs in your documents for accuracy and citations.
- Vector Database: Specialized store for similarity search over embeddings—used in RAG and some recommenders.
- Embeddings: Numeric representations of text or images capturing semantic meaning.
- mAP/IoU: Measures of CV detection/segmentation quality.
- AUC/PR‑AUC: Classification metrics for ranking positive cases.
- Calibration: Ensuring predicted probabilities match reality.
- Cold Start: When a recommender has too little behavior data to personalize; use content‑based methods first.
- STP (Straight‑Through Processing): Percent of cases handled with no human touch.

---

## Final Guidance: Sponsoring with Confidence

You do not need a PhD to lead high‑impact AI programs. You do need clarity: on the business problem, the model family, the data, the guardrails, and the measurement plan. Use the Read‑See‑Predict‑Suggest‑Do lens. Start small, deliver visible wins in 90 days, and scale what works. And remember: the model is the middle; the workflow is the product.

---

## Key Takeaways

- Five model types cover 90% of real estate AI needs: LLMs (Read), Computer Vision (See), Predictive Analytics (Predict), Recommendation Engines (Suggest), and Process Automation (Do).
- Pick the model family by asking a single focusing question: language, imagery, future number, choice ranking, or workflow automation?
- Real wins come from combinations: e.g., IDP + LLM + Automation for lease intake; CV + Automation for turns; Predict + Recommender for revenue.
- Ground LLMs with your documents (RAG), deploy vision models where imagery is abundant, and always tie predictions to actions.
- Governance is non‑negotiable: privacy, Fair Housing, surveillance, and auditability—baked in from day one.
- Measure outcomes that matter: business KPIs alongside technical metrics. The project isn’t done until the KPI moves.
- Use 90‑day pilots with clear baselines and A/Bs. Treat models as products with monitoring and retraining.
- Buy foundations to move fast; build the last mile to differentiate.

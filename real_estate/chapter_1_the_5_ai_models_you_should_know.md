# Chapter 1: The 5 AI Models You Should Know

> From underwriting to tenant experience, five model families do most of the heavy lifting. Learn what they are, what they’re good at, and where to deploy them first.

## Why These Five Models Matter in Real Estate

Real estate is a data business disguised as a physical one. Leases, plans, photos, sensor feeds, CRM trails, rent rolls, and market comps all sit in silos—often trapped as PDFs or scattered in spreadsheets. AI turns this messy haystack into decisions and actions. In practice, a small set of model types covers 80% of high‑value use cases:

- Large Language Models (LLMs) — understand and generate text; they converse, summarize, and extract data from documents.
- Computer Vision — turn images and video into structured observations; they spot roofs, rooms, cracks, cars, and code violations.
- Predictive Analytics — forecast outcomes and numeric values; they estimate rents, churn, downtime, and CapEx.
- Recommendation Engines — match people to properties and options; they rank units, amenities, listings, and prospects.
- Process Automation — orchestrate tasks across systems; they combine models with workflow to complete work.

Think of these five as the LEASE Framework for AI in real estate:

- L — Large Language Models: Understand your language and documents.
- E — Eyes (Computer Vision): See your assets and jobsites.
- A — Anticipate (Predictive Analytics): Forecast what happens next.
- S — Suggest (Recommendation Engines): Personalize choices for each stakeholder.
- E — Execute (Process Automation): Tie it all together to get work done.

Each family answers different business questions and depends on different data. You don’t need to be a data scientist to lead; you do need to know what to ask for and what good looks like.

## A One‑Page Map of the Five Model Types

| Model Type | Plain‑English Definition | Typical Questions It Answers | Data Required | Real Estate Sweet Spots | Representative Tools |
|---|---|---|---|---|---|
| Large Language Models (LLMs) | Systems that read and write text, and can reason over documents when paired with your data | “What’s in this lease? Summarize the rent steps.” “Draft a response to this RFP.” “Explain tenant obligations.” | Unstructured text (leases, emails, RFPs), knowledge bases, policies; vector database for retrieval | Lease abstraction, due diligence Q&A, policy assistants, listing copy, tenant communications | OpenAI GPT‑4o/4.1, Anthropic Claude 3.5, Google Gemini 1.5, Meta Llama 3, Azure OpenAI; Retrieval: Pinecone, Weaviate, Milvus, Azure AI Search; Orchestration: LangChain, LlamaIndex |
| Computer Vision | Models that detect, segment, and classify objects in images/video | “Is the roof damaged?” “How many parking spaces are occupied?” “Extract this floor plan.” | Images, drone/aerial footage, walkthrough videos, floor plans; labeled examples | Condition assessment, construction progress, occupancy counts, code compliance, floor plan extraction | YOLOv8, Detectron2, Segment Anything (SAM), OpenCV, Roboflow, Label Studio; Cloud: AWS Rekognition, Azure Vision, Google Vertex AI Vision, Matterport |
| Predictive Analytics | Models that estimate numbers or probabilities from historical data | “What will effective rent be?” “Which tenants will churn?” “What’s the likely downtime?” | Structured records: CRM, rent rolls, market data, work orders, footfall, macro indicators | Rent/NOI forecasts, delinquency and move‑out risk, lease‑up velocity, maintenance risk | XGBoost, LightGBM, CatBoost, scikit‑learn, Prophet; Platforms: Databricks AutoML, DataRobot, H2O.ai, BigQuery ML, Amazon Forecast |
| Recommendation Engines | Systems that rank items for a user/context | “Which unit will this prospect most likely sign?” “Which amenity to upsell?” “Which agent should handle this lead?” | User‑item interactions (views, tours), listing attributes, constraints, outcomes | Unit‑to‑prospect matching, amenity bundling, lead routing, investor‑deal matching | TensorFlow Recommenders, implicit, LightFM, Amazon Personalize, Google Recommendations AI, Elasticsearch kNN |
| Process Automation | Workflows that coordinate models, rules, and RPA to complete tasks | “Take this lease PDF, extract the data, validate it, enter it into the PMS, and notify the leasing team.” | APIs across PMS/CRM/AP, forms, documents, model outputs, SLAs | Lease onboarding, AP invoice processing, move‑in/out checklists, compliance packages | UiPath, Automation Anywhere, Microsoft Power Automate, Zapier, Make, n8n; Agent orchestration: LangGraph, OpenAI Assistants API, CrewAI; Scheduling: Airflow, Prefect, Dagster |


## How to Choose: The LEASE Decision Checklist

Use this quick checklist to match your problem to the right model family:

1) What is your input data?
   - Mostly text/PDFs/emails? Start with LLMs (+ Retrieval Augmented Generation).
   - Images, video, floor plans, drone or satellite? Use Computer Vision.
   - Tables in your DWH/CRM/ERP? Use Predictive Analytics.
   - You’re matching people to options? Reach for a Recommendation Engine.
   - You need to move data between systems and complete tasks? Orchestrate with Process Automation.

2) What answer type do you need?
   - Narrative/summary/explanation → LLMs
   - Counts, detection, measurement → Computer Vision
   - Numbers/yes‑no probabilities → Predictive Analytics
   - Ranked shortlist → Recommendation Engines
   - Completed workflow → Process Automation

3) What is the decision horizon?
   - Real‑time (seconds) → Vision, Recommenders, some LLMs
   - Near‑term (days/weeks) → LLMs, Predictive Analytics
   - Operational cadence (monthly/quarterly) → Predictive Analytics, Automations

4) What is the tolerance for error and explainability?
   - High scrutiny/regulatory → Predictive models with clear features; human‑in‑the‑loop for LLMs
   - Low‑risk content/assistive → LLMs and automation with guardrails

5) Do you have enough labeled data?
   - If not, prefer pre‑trained LLMs/vision models with retrieval or few‑shot learning. Use synthetic data carefully and augment over time.


---

## 1) Large Language Models (LLMs)

### What They Are
LLMs are general‑purpose text engines trained on vast corpora. With retrieval, they can anchor answers in your private documents and systems. Think of them as a policy‑savvy analyst who reads everything quickly, speaks in plain English, and never gets tired.

Key capabilities:
- Summarize, compare, and explain documents
- Extract structured data from unstructured text (key terms, dates, clauses)
- Generate drafts (emails, memos, listing copy) in your tone
- Answer questions using your own knowledge base (via Retrieval Augmented Generation, “RAG”)
- Chain steps to reason across multiple sources

### Where They Fit in Real Estate
- Lease and contract analysis at scale
- Due diligence Q&A across data rooms
- Policy assistants for compliance, ESG, brand tone
- Resident/tenant communications and support
- Listing and marketing content generation

### Niche, Real‑World Examples
1) Portfolio‑wide Lease Abstraction in Days
   - Situation: A multifamily operator acquires 37 assets with 9,800 resident leases across 12 templates and countless handwritten addenda. Manual abstraction would take 6–8 weeks.
   - Approach: An LLM with RAG, powered by a vector database (e.g., Pinecone or Azure AI Search), extracts 200+ fields per lease (rent steps, concessions, renewal options, pets, parking). A small, labeled set (~300 leases) is used to validate and calibrate prompts. A human reviewer handles flagged low‑confidence fields.
   - Payoff: 95%+ field‑level accuracy on standard clauses; 6,500 staff hours avoided; earlier roll‑up of occupancy risk and cashflow scenarios.

2) Investor RFP and DD Question Assistant
   - Situation: A core‑plus fund juggles RFPs and investor diligence questions. Data lives across SharePoint, email threads, and PDFs.
   - Approach: A firm‑tuned LLM with retrieval over policies, historical responses, fund docs, and case studies. The assistant drafts 80%‑ready answers with citations to source docs and flags gaps.
   - Payoff: 60% faster turnaround; consistent tone and compliance; fewer back‑and‑forth cycles with legal.

### Strengths and Limitations
- Strengths: Fast to start; works with messy text; flexible drafting and Q&A; improves with retrieval; multilingual.
- Watch‑outs: Hallucinations if not grounded; sensitive data handling; need for prompt and evaluation discipline; variable costs if ungoverned.

### Data and Architecture Quick Sketch
- Inputs: PDFs, DOCX, emails, web pages, intranet policies, past deals
- Retrieval layer: Vector DB (Pinecone, Weaviate, Milvus) or Azure AI Search; chunking and embeddings
- Model: GPT‑4o/4.1, Claude 3.5, Gemini 1.5, or self‑hosted Llama 3 for sensitive use
- Orchestration: LangChain/LlamaIndex; tools/functions for API calls (e.g., look up unit availability)
- Guardrails: Content filters (Azure AI Content Safety, AWS Bedrock Guardrails), PII redaction, rate limits, human‑in‑the‑loop

### Tools to Know
- Foundation models: OpenAI GPT‑4o/4.1, Anthropic Claude 3.5 Sonnet, Google Gemini 1.5 Pro, Meta Llama 3
- Enterprise endpoints: Azure OpenAI Service, Amazon Bedrock
- Retrieval: Pinecone, Weaviate, Milvus, Elasticsearch kNN, Azure AI Search
- Orchestration and evaluation: LangChain, LlamaIndex, Promptflow, TruEra, Arize Phoenix
- Document AI: Microsoft Document Intelligence (Form Recognizer), Google Document AI, AWS Textract

### Implementation Checklist (LLMs)
- Define the questions and outputs (fields, summaries, tone) and the acceptable error rate
- Curate your corpus: deduplicate, redact PII, split into semantic chunks, and tag by entity/date
- Start with RAG; resort to fine‑tuning only if needed
- Implement citations and confidence scores; route low‑confidence cases to humans
- Track cost per task; cap tokens; cache results for repeated queries
- Establish evaluation sets (golden questions) and measure factuality, coverage, and time saved

### KPIs
- Field‑level accuracy (%) and coverage (%)
- Turnaround time reduction (hours per document)
- Human review rate (%) and first‑pass acceptance (%)
- Cost per document and total cost avoided

### Compliance and Risk Notes
- Respect Fair Housing and lending‑related constraints in generated copy; use policy prompts and pre‑approved templates
- Redact PII where not necessary; segregate training/retrieval data by region and role
- Log every prompt and response for audit; enable deletion and source tracking

---

## 2) Computer Vision

### What It Is
Computer Vision models identify what’s in an image or video and where. They can detect objects (e.g., HVAC units), segment regions (roofs vs. parking), and classify conditions (water staining vs. clean drywall). Combine with drones or walkthrough video and you obtain portfolio‑wide eyes at a fraction of the cost.

### Where It Fits in Real Estate
- Condition assessment at acquisition and during operations
- Progress tracking for construction and unit turns
- Parking occupancy and circulation analysis
- Floor plan extraction and measurement
- Code compliance checks (e.g., exit signage, fire extinguishers)

### Niche, Real‑World Examples
1) Automated Roof Condition Index from Drone Photos
   - Situation: A REIT manages 420 buildings across suburban office and industrial. Roof condition drives CapEx and insurance.
   - Approach: Quarterly drone flights capture orthomosaics. A segmentation model (SAM + YOLOv8) detects ponding, patch repairs, membrane tears, and HVAC curb flashing issues. Outputs a 0–100 roof health score per building with geo‑tagged defect heatmaps.
   - Payoff: 30% reduction in emergency leaks; better vendor scoping; insurance negotiations grounded in evidence.

2) Walkthrough Video to Turn‑Ready Punchlist
   - Situation: A multifamily operator needs faster unit turns between tenants.
   - Approach: Leasing agents capture a 60‑second smartphone walkthrough. Vision models detect appliances, flooring, paint scuffs, smoke detectors, and missing blinds; estimate materials (gallons of paint, sqft of carpet); auto‑create work orders in the PMS.
   - Payoff: Turn time reduced by 2.5 days; more accurate vendor bids; fewer callbacks.

### Strengths and Limitations
- Strengths: Objective and scalable; sees what humans miss; good for repetitive inspections; works offline with edge devices.
- Watch‑outs: Requires labeled data for custom objects; variations in lighting/angle; privacy in public spaces; change management for field teams.

### Data and Architecture Quick Sketch
- Inputs: Photos (drone, mobile), videos, floor plans, street imagery
- Annotation: Label Studio or Roboflow for custom datasets; augment with synthetic images
- Models: YOLOv8/YOLOv10 for detection, Detectron2 for instance segmentation, Segment Anything for masks; OCR with Tesseract or Microsoft Document Intelligence for plan text
- Deployment: Cloud inference (Vertex AI, AWS Rekognition Custom Labels, Azure Custom Vision) or on‑edge (Jetson, iOS CoreML)
- Integration: Push structured defects and measurements into CMMS/PMS; proof reports for vendors and insurers

### Tools to Know
- Open‑source: OpenCV, YOLOv8, Detectron2, Segment Anything (SAM), Grounding DINO
- Labeling: Label Studio, Roboflow
- Cloud services: AWS Rekognition, Google Vertex AI Vision, Azure AI Vision, Matterport for 3D capture
- Hardware: DJI drones, iPhones/iPads with LiDAR, Nvidia Jetson for edge inference

### Implementation Checklist (Vision)
- Define the “unit of output” (e.g., roof health score, count of stalls occupied, square footage of water damage)
- Standardize capture protocols: angle, height, lighting, privacy signage
- Start with pre‑trained models; only custom‑train when business value demands
- Validate with side‑by‑side field inspections; calibrate thresholds and costs
- Plan for storage and governance of imagery; define retention policies

### KPIs
- Detection precision/recall (F1 score) for key classes
- Reduction in inspection time and travel costs
- Avoided CapEx or emergency repair spend
- Vendor bid variance vs. actuals, pre‑ and post‑deployment

### Compliance and Risk Notes
- Respect local laws on aerial footage; avoid capturing PII (faces, license plates) or blur them
- Secure storage for images; restrict access by asset/region
- Communicate to tenants and staff what you capture and why

---

## 3) Predictive Analytics

### What It Is
Predictive Analytics estimates a number or a probability from historical, structured data. It answers questions like “What will effective rent be next quarter?” or “Which tenant is likely to give notice?” These are supervised learning models—trained on examples of input features and known outcomes.

Common approaches include gradient boosted trees (XGBoost/LightGBM/CatBoost), regularized regression, time‑series models (Prophet, ARIMA), and survival models for time‑to‑event problems.

### Where It Fits in Real Estate
- Market and rent forecasting (by unit plan, submarket, channel)
- Delinquency and move‑out risk scoring
- Lease‑up velocity and concession optimization
- Predictive maintenance and work order prioritization
- CapEx planning and scenario analysis

### Niche, Real‑World Examples
1) Early Move‑Out Risk for Class B Multifamily
   - Situation: Occupancy is acceptable, but unwanted churn is rising at certain properties.
   - Approach: Using 24 months of unit‑level history (rent, concessions, service tickets, payment timeliness, commute time changes, amenity usage), a gradient boosted tree predicts 90‑day non‑renewal risk. Marketing nudges and service recovery are targeted to top‑decile at‑risk residents.
   - Payoff: 2.1 percentage‑point improvement in renewals; reduced make‑ready costs; better staffing of renewal specialists.

2) Industrial NOI Forecasting for Refinancing
   - Situation: A private owner needs to refinance a 7‑building industrial portfolio and wants defensible NOI projections.
   - Approach: A multivariate time‑series model blends lease roll, market rent indices, vacancy, labor cost, and truck traffic data. Scenarios test downside (recession) and upside (expansion) cases with embedded sensitivity to tenant mix.
   - Payoff: Data‑defensible projections for lenders; tighter DSCR coverage and better terms.

### Strengths and Limitations
- Strengths: Explainable features; consistent decision‑making at scale; measurable uplift; integrates well with existing BI.
- Watch‑outs: Garbage in, garbage out; risk of bias if features correlate with protected classes; data leakage if future info bleeds into training; need for ongoing monitoring.

### Data and Architecture Quick Sketch
- Inputs: PMS/CRM extracts, rent rolls, work orders, tour data, digital marketing events, market comps, macro indicators (CPI, employment), mobility/footfall
- Feature store: Centralized definitions of variables (e.g., “days since last ticket”) via Databricks Feature Store, Feast, or Tecton
- Models: XGBoost/LightGBM/CatBoost for tabular; Prophet/ARIMA for time‑series; survival models for time‑to‑vacancy
- MLOps: Versioning (MLflow), pipelines (Airflow/Prefect), monitoring (Evidently, Arize), model registry
- Integration: Score nightly/weekly; push to CRM/PMS to trigger campaigns or work queues

### Tools to Know
- Libraries: scikit‑learn, XGBoost, LightGBM, CatBoost, Prophet
- Platforms: Databricks AutoML, H2O.ai, DataRobot, BigQuery ML, Amazon Forecast, Snowflake Cortex ML
- Monitoring: MLflow, Weights & Biases, Evidently AI, Fiddler, Arize

### Implementation Checklist (Predictive)
- Define the decision you will change (e.g., “Escalate retention outreach for top 20% risk”)
- Establish a clean training set; split by time to mimic real deployment; avoid data leakage
- Pick simple, explainable models first; codify feature definitions in a feature store
- Calibrate thresholds to business capacity (e.g., retention team can handle 300 calls per week)
- Run an A/B or phased rollout; measure incremental uplift vs. control
- Monitor drift and re‑train cadence (monthly/quarterly)

### KPIs
- AUC/precision‑recall; calibration of probabilities
- Uplift in the business metric (renewals, NOI, downtime)
- Adoption (are teams acting on the scores?)
- Cost to serve (time per scored case)

### Compliance and Risk Notes
- Screen features for proxies of protected classes; document exclusions
- Provide reason codes when making adverse decisions (e.g., lead deprioritization)
- Maintain model cards and change logs for audits

---

## 4) Recommendation Engines

### What They Are
Recommendation Engines rank options for a user and context. They learn 
from historical interactions and content to predict “next best” choices. There are three patterns:

- Content‑based: Match item attributes to user preferences (e.g., floor plan and budget).
- Collaborative filtering: “People like you signed here” based on interaction patterns.
- Hybrid: Blend both, often with real‑time context and business rules.

### Where They Fit in Real Estate
- Unit‑to‑prospect matching on property sites and ILS portals
- Amenity and add‑on bundling (parking, storage, pets, smart home)
- Lead routing to the right agent by expertise and performance
- Investor‑deal matching for capital placement

### Niche, Real‑World Examples
1) Right Unit, Right Now on a Multifamily Site
   - Situation: Prospects browse many units and bounce. Marketing spends rise without conversion gains.
   - Approach: A hybrid recommender ingests on‑site behavior (views, time on page, filters), unit attributes (plan, floor, noise exposure), and real‑time availability. It produces a ranked shortlist and “why this unit” explanations; nudges to schedule a tour.
   - Payoff: +14% tour bookings; fewer low‑fit leads; faster lease‑ups.

2) Industrial Tenant‑to‑Bay Matcher for Mid‑Market Brokers
   - Situation: A brokerage juggles hundreds of small‑bay requirements with nuanced needs (clear height, loading, power, trailer parking).
   - Approach: Content‑based ranking using coded requirements vs. inventory attributes, augmented with collaborative signals from closed deals. Includes penalties for known deal‑breakers and routing to agents who closed similar deals.
   - Payoff: Shortlists in minutes; improved agent win rate; higher tenant satisfaction.

### Strengths and Limitations
- Strengths: Personalization at scale; measurable uplift; supports explainable “why this” messages.
- Watch‑outs: Cold‑start for new units/tenants; sparse feedback; need for business rules (e.g., fair pricing, inventory constraints); feedback loops if not monitored.

### Data and Architecture Quick Sketch
- Inputs: Interaction logs (views, tours, emails), item attributes (unit specs), user attributes and stated preferences
- Models: Matrix factorization (implicit), deep learning (TensorFlow Recommenders), gradient boosting with features; re‑ranking layer to apply business constraints
- Infrastructure: Real‑time feature store, low‑latency inference (Redis, Vertex AI, SageMaker), A/B testing platform
- Integration: Website widgets, CRM lead routers, pricing/availability systems

### Tools to Know
- Open‑source: implicit, LightFM, TensorFlow Recommenders, RecBole
- Managed: Amazon Personalize, Google Recommendations AI, Azure Personalizer (deprecated for new users; consider alternatives)
- Retrieval layer: Elasticsearch, OpenSearch, Pinecone with vector search for semantic matching

### Implementation Checklist (Recommenders)
- Define objective function (tours booked, leases signed, net revenue)
- Create a feedback loop: capture clicks, tours, applications, and leases
- Start with content‑based to avoid cold‑start; layer collaborative as data grows
- Add “why this” explanations; enforce constraints (budget, move‑in date, accessibility)
- Continuously A/B test ranking changes; monitor for popularity bias and fairness

### KPIs
- Conversion rates at each funnel step (view → tour → lease)
- Average days‑to‑lease and occupancy lift
- Incremental revenue from upsells (parking, storage)
- Distribution equity across inventory (avoid starving certain units)

### Compliance and Risk Notes
- Avoid discriminatory targeting; document excluded features
- Provide alternative suggestions for accessibility needs
- Monitor for feedback loops that disadvantage new inventory or protected groups

---

## 5) Process Automation

### What It Is
Process Automation coordinates models, rules, and systems to complete work. In practice, this includes robotic process automation (RPA) to click and type in legacy apps, API‑based integrations to modern systems, and—more recently—LLM‑powered “agents” that can read emails, decide next steps, and call tools.

### Where It Fits in Real Estate
- Lease onboarding: ingest and validate data, set up billing, escrow, notifications
- AP invoice processing: capture, code, approve, post, and pay
- Move‑in/move‑out workflows: inspections, utilities, access, compliance packets
- Compliance and reporting: ESG data pulls, lender covenants, quarterly packs

### Niche, Real‑World Examples
1) End‑to‑End Lease Onboarding
   - Situation: After a retail lease is signed, operations teams re‑key the same data into PMS, CRM, and insurance portals.
   - Approach: An automation listens to a “fully executed” email; uses Document AI + LLM extraction to capture key terms; validates against deal sheet; posts to the PMS via API; creates tasks for certificates of insurance; emails tenants with onboarding instructions; schedules reminders.
   - Payoff: Onboarding time cut from 10 days to 3; fewer errors; happier tenants and property managers.

2) AP Invoice Touchless Processing
   - Situation: Vendors email thousands of invoices monthly; AP staff struggle with coding and approvals.
   - Approach: Ingestion + OCR + LLM line‑item understanding; matching to POs; auto‑coding recurring spend; exception routing to approvers; payment initiation.
   - Payoff: 60–80% touchless rate; faster close; early‑pay discounts captured.

### Strengths and Limitations
- Strengths: Tangible hours saved; immediate cycle‑time gains; stitches multiple AI models into real business outcomes.
- Watch‑outs: Brittle RPA for UI changes; need for exception handling; security and access controls; audit trails.

### Data and Architecture Quick Sketch
- Triggers: Emails, signed DocuSign envelopes, folder drops, webhooks from PMS/CRM
- Steps: Extract (OCR/LLM) → Validate (rules/predictive scores) → Post (APIs/RPA) → Notify (email/chat) → Monitor (dashboards)
- Orchestration: Power Automate, UiPath, Automation Anywhere; or low‑code iPaaS (Zapier, Make, n8n)
- Agents: LLM‑driven tools via OpenAI Assistants API, LangGraph, CrewAI; retrieval for policy and SOPs

### Tools to Know
- RPA/iPaaS: UiPath, Automation Anywhere, Microsoft Power Automate, Zapier, Make, n8n
- Document processing: Microsoft Document Intelligence, Google Document AI, AWS Textract
- Agent frameworks and orchestration: OpenAI Assistants API, LangChain, LangGraph, CrewAI, Airflow, Prefect, Dagster

### Implementation Checklist (Automation)
- Start with a swimlane map: clarify handoffs and systems; identify “golden records”
- Define SLAs and exception categories before you automate
- Instrument every step for observability; create an operations dashboard
- Keep a human‑in‑the‑loop for low‑confidence cases; design retry and fallback paths
- Harden access control and secrets management; log actions for audit

### KPIs
- Touchless rate (% without human intervention)
- Cycle time and queue time reduction
- Exceptions per 1,000 transactions and resolution time
- Hours saved and redeployed; error rate pre/post

### Compliance and Risk Notes
- Enforce least privilege for bots; rotate credentials and use vaults
- Maintain immutable logs for auditors; capture evidence attachments
- Validate data lineage from source to sink for financial postings

---

## Putting It Together: An End‑to‑End Example

Consider a common, cross‑functional process—acquiring a multifamily portfolio and integrating it into operations.

1) Intake and Triage (Process Automation + LLM)
   - Automation ingests data room artifacts; LLM tags and routes files (leases, SNDA, estoppels, drawings) and checks completeness.

2) Lease Abstraction (LLM + Document AI)
   - LLM extracts key data with citations and confidence scores; humans review exceptions.

3) Physical Due Diligence (Computer Vision)
   - Drone and walkthrough capture; vision models score roofs, parking, and unit conditions; generate CapEx punchlists with unit‑level estimates.

4) Forecasting and Scenarios (Predictive Analytics)
   - Predict churn and lease‑up velocity; forecast rent growth; stress‑test rates and concessions; prioritize renovations by predicted uplift.

5) Investor and Lender Packs (LLM)
   - Draft memos, risk summaries, and Q&A; link to sources; maintain consistent tone and policy.

6) Day‑1 Operations (Process Automation + Recommenders)
   - Automate onboarding in PMS/CRM and vendor portals; activate resident portals.
   - Recommender offers the right amenity bundles and upgrades to new residents.

The outcome: faster close, cleaner data, defensible forecasts, and smoother onboarding—with a paper trail auditors and lenders accept.

---

## Operating Model: Who Does What

- Product Owner (Business): Owns outcomes, backlog, and change management
- Data Lead: Owns data contracts, quality, and feature definitions
- ML Engineer: Builds and deploys models; MLOps and monitoring
- Automation Engineer: Builds workflows; ensures auditability
- Domain SMEs: Leasing, AP, Facilities—provide acceptance tests and labels
- Risk & Compliance: Reviews features, prompts, and logs; ensures policy alignment

Establish a cadence: monthly model review, quarterly roadmap, and a minimal “model card” for each deployment (owner, data, metrics, risks, last retrain).

---

## Common Pitfalls—and How to Avoid Them

- Boiling the ocean: Start with one property type and one market; ship in 90 days
- Letting models sprawl: Centralize prompts, datasets, and model registries; reuse components
- Ignoring evaluation: Maintain golden datasets and A/B frameworks; publish win/loss reports
- Forgetting the last mile: Budget time to integrate into PMS/CRM and staff workflows
- Under‑communicating: Tell teams what the model does, what it doesn’t, and how to escalate exceptions

---

## Real‑Estate‑Specific Data Readiness Checklist

- Documents
  - Lease templates and executed leases in digital, searchable form
  - Addenda and amendments organized and linked to master agreements
  - Vendor contracts, COIs, estoppels, and SNDAs centralized
- Images and Video
  - Standardized capture protocols; consent signage; storage with metadata
- Structured Systems
  - Clean rent rolls, unit attributes, and availability; historical CRM events unified
  - Work order and maintenance history standardized across properties
- External Data
  - Market comp feeds, mobility/footfall, macro indicators, weather
- Access and Governance
  - API access to PMS/CRM/AP; service accounts created; logging enabled
  - Data catalog entries with owners and refresh cadences

---

## Tooling Selection Matrix (Quick Reference)

| Goal | Start Here | When to Upgrade |
|---|---|---|
| Lease abstraction from PDFs | Microsoft Document Intelligence + GPT‑4o with RAG | Fine‑tune extraction on your templates; integrate with PMS via API |
| Drone roof assessment | YOLOv8 + SAM on Vertex AI Vision | Custom labels for your roof types; edge inference for onsite feedback |
| Churn risk scoring | XGBoost on Databricks AutoML | Add survival analysis; feature store; nightly scoring integrated to CRM |
| Unit recommendations on website | Content‑based model + Elasticsearch | Hybrid with TensorFlow Recommenders; real‑time re‑ranking and A/B testing |
| Touchless AP | UiPath + AWS Textract | LLM line‑item understanding; vendor behavior prediction; exception analytics |

---

## Governance, Ethics, and Controls in Real Estate Context

- Fairness: Exclude protected attributes and close proxies; audit recommender outcomes for disparate impact
- Privacy: Minimize PII in prompts; tokenize or redact; set data retention windows for images and logs
- Transparency: Provide explanations for scores and recommendations where they influence customer decisions
- Security: Enforce tenant‑by‑tenant data isolation; vault secrets; require SSO and role‑based access
- Resilience: Define manual fallbacks for outages; keep human override switches; monitor SLAs

---

## 90‑Day Adoption Plan (Practical)

- Days 1–15: Choose one use case per model family with clear sponsors and KPIs; procure minimal tooling
- Days 16–45: Stand up data pipelines; build thin vertical slices; instrument metrics
- Days 46–75: Pilot with front‑line users; refine prompts, thresholds, and UI; address exceptions
- Days 76–90: A/B test; document model cards; train staff; move to limited production; publish results

---

## FAQs Leaders Ask (and Short Answers)

- How accurate do these need to be? Enough to improve decisions and outcomes with controls. Target 90–95% for extraction; optimize precision for high‑cost errors.
- Build or buy? Start with managed services and adapters; invest in custom models where you have scale and differentiation.
- How do we budget? Treat as product lines: initial build, data prep, integration, ongoing tuning. Expect operating expense for inference and maintenance.
- Where do we find talent? Upskill internal analysts; partner with vendors; hire 1–2 senior ML/platform engineers to anchor capabilities.

---

## Key Takeaways

- Five model families—LLMs, Computer Vision, Predictive Analytics, Recommendation Engines, and Process Automation—cover most of the value in real estate AI.
- Use the LEASE framework to map problems to model types: Learn (LLMs), Eyes (Vision), Anticipate (Predict), Suggest (Recommend), Execute (Automate).
- Start with document and workflow wins: lease abstraction, AP automation, and unit recommendations deliver fast ROI.
- Ground LLMs with your data (RAG), measure rigorously, and route low‑confidence cases to humans.
- Capture images and structured data consistently; your model quality is only as good as capture quality.
- Treat predictive models as living products: monitor drift, retrain on a cadence, and measure uplift—not just AUC.
- Build explainability and fairness in from day one; document exclusions and provide reason codes.
- Focus on last‑mile integration; the business impact comes when models change workflows in PMS/CRM and vendor systems.
- Start small, ship, and iterate within 90 days; publish results to build organizational trust and momentum.

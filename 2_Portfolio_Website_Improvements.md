# Doc 2 — Portfolio Website Improvements
**utsav-vaghani.github.io and github.com/utsav-vaghani · reviewed 25 Aug 2026**

The site's job is narrow: when a recruiter or interviewer opens it between reading your resume and deciding on a call, it should confirm you're a serious backend engineer in fintech + GenAI, show three systems in enough depth that a deep-dive round has something to anchor on, and never contradict the resume. Right now it does the first only partially and the third not at all.

---

## 1. Audit — ranked by damage

| # | Finding | Why it matters | Fix time |
|---|---|---|---|
| 1 | **Skills section renders `{{ sk }}`** in all three blocks (Languages, Infrastructure, Foundations) | Unrendered template variables on an engineer's own site; reviewers close the tab | 30 min (see §6.1) |
| 2 | **Dates disagree with the resume**: smallcase shown Jul 2022 – Jul 2023 (resume: Mar 2022 – Sep 2024); Zopsmart Jul 2021 – Jun 2022 (resume: Jan 2021 – Feb 2022); Glabbr internship on site, not on resume | Creates a fake 14-month gap; bank BGV vendors flag public-profile discrepancies | 10 min once the canonical timeline is fixed |
| 3 | **Title mismatch**: site says "Software Engineer" at Keenai; resume says "Senior Associate Product Engineering" | Same BGV issue; also reads as a demotion after "Senior Software Engineer" at Razorpay | 5 min |
| 4 | **Copy errors** in the most-read sentences: "Prior work spans an GenAI-based at Razorpay" (missing noun); "Built an GenAI-based GenAI based products"; "PAAS"/"PaaS"; "Sept"; "Wealth management" | First-impression quality signal | 20 min |
| 5 | **No numbers anywhere** — no volumes, users, latency, cost, adoption | The resume has them; the site should show the same headline numbers | 1 hr |
| 6 | **No case studies** — nothing an interviewer can read before a deep-dive round | The biggest missed opportunity; the site is a brochure, not evidence | 4–6 hrs across two weekends |
| 7 | Resume link goes to Google Drive | Drive previews are slow, need sign-in on some networks, and can't be fetched by tools; host `/resume.pdf` on the site | 10 min |
| 8 | GitHub: pinned repos are student-era (ContestReminder, Book-Rentals); README says "currently working on GoLang"; repo description "Personal Protfolio" | Reads like 2021 | 1 hr now, more with new repos (§7) |
| 9 | Instagram in "Elsewhere" | Not wrong, but off-tone for bank/big-tech reviewers | 1 min |
| 10 | No meta description / Open Graph tags (LinkedIn and WhatsApp previews will be bare) | Every referral message you send links here | 15 min |

---

## 2. Positioning (the sentence the whole site should support)

> Backend engineer who has built payments infrastructure and production GenAI systems in fintech — and can show the numbers.

Everything on the page either supports that sentence or gets cut.

---

## 3. Structure (top to bottom)

1. **Hero** — name, one-line positioning, three proof numbers, two buttons (Resume PDF, Email)
2. **Selected systems** — 3–4 case-study cards (the core of the site)
3. **Experience** — same dates/titles as the resume; 2–3 bullets each with numbers
4. **Skills** — fixed, grouped, honest
5. **Writing / notes** (optional, later) — 2–3 short technical posts; even one good post on "idempotency in payment retries" or "evals for a support agent" is worth more than a skills grid
6. **Education + certification** — one line each
7. **Contact** — email, LinkedIn, GitHub; nothing else

---

## 4. Copy — ready to paste (replace `[N]` with real numbers)

### 4.1 Hero
**Utsav Vaghani**
Senior Backend Engineer — payments, wealth platforms, production GenAI.
Go · Node.js · Python · Bangalore

Proof strip (three items, large numbers, small captions):
- **5M users** — investment alerting platform I built at smallcase
- **4 gateways** — payments PaaS from scratch (Razorpay, Juspay, Apple IAP, Zerodha)
- **₹50L / month** — support cost removed by the GenAI ticket-resolution system I led at Razorpay

Buttons: `Resume (PDF)` → `/resume.pdf` · `Email` → `mailto:utsav.r.vaghani@gmail.com`

### 4.2 About (replace the broken paragraph)
I build backend systems where correctness and scale both matter. At smallcase I built the payments Platform-as-a-Service that handles one-time, subscription and token-based recurring payments across four gateways, and an alerting platform serving 5M users. At Razorpay I led "Yogi", a GenAI system that auto-resolves merchant support tickets — 85–100 a day, ₹50L/month in cost removed — and a RAG-based onboarding assistant with 70% containment. At Keenai I own order management and portfolio services for a private-wealth platform spanning [N] markets. I work mostly in Go, Node.js and Python on AWS, and I care about the unglamorous parts: idempotency, reconciliation, observability, and evals.

### 4.3 Experience (dates must match the resume — fill from offer letters)
**Keenai Global** — Senior Associate, Product Engineering (Backend) · Aug 2025 – Present
- Order-management service for stock and ETF orders across US, Singapore and [N] other exchanges — [N orders/day], [N]% placement success
- Price-hierarchy engine for valuation; cut reconciliation breaks by 20%
- Portfolio versioning over 100K+ transactions per family office; org-wide domain-events service ([N events/day])

**Razorpay** — Senior Software Engineer · Sep 2024 – Aug 2025
- Led "Yogi": GenAI ticket resolution, 85–100 resolutions/day, ₹50L/month cost reduction, team of five
- RAG + LLM onboarding assistant, 70% containment across [N] use cases
- Python (FastAPI, Celery), OpenAI APIs, RAG, MCP, n8n

**smallcase** — SDE II · Mar 2022 – Sep 2024 *(confirm start month)*
- Payments PaaS from scratch across Razorpay, Juspay, Apple IAP, Zerodha — [N transactions/year], [N]% success
- Investment alerting for 5M users / 1M active: pre-market, intraday, end-of-day
- Go, NestJS, MongoDB, AWS

**Zopsmart** — SDE I (Intern → SDE I) · Jan 2021 – Feb 2022 *(confirm)*
- Go application framework with generic pub/sub, metrics and AWS abstractions; adopted by [N] services
- CSP inter-service authentication

*(Glabbr: keep only if it stays on the resume; one line.)*

### 4.4 Skills (replace the broken blocks; three groups, no "etc.")
**Languages:** Go · TypeScript/Node.js · Python
**Backend & data:** gRPC · REST · Kafka · SNS/SQS · NestJS · FastAPI · MongoDB · MySQL · Redis
**Infra & GenAI:** AWS (EC2, S3, Lambda, SNS/SQS) · Docker · Prometheus · OpenAI APIs · RAG · MCP · n8n [· LangGraph]

### 4.5 Contact
"Email is the fastest way to reach me." — `utsav.r.vaghani@gmail.com` · LinkedIn · GitHub. Drop "One conversation. No agenda…" (sales-page tone) and drop Instagram.

---

## 5. Selected systems — four case studies, drafted

Format per card: 150–250 words + one diagram (draw in Excalidraw or Mermaid; export PNG/SVG). Each has the same six headings so interviewers can skim. Placeholders are for numbers only you have.

### 5.1 Yogi — GenAI ticket resolution at Razorpay
**Problem.** Merchant support handled [N] tickets/month; a large share were repetitive (KYC status, settlement timing, refund state) but required pulling data from several internal systems, so human agents spent minutes per ticket on lookups.
**Constraints.** Correctness on money-related answers (no hallucinated balances), p95 under [N] s, cost under ₹[N]/ticket, auditable actions, gradual rollout by use case.
**Architecture.** Ticket intake → classifier (intent, use case, confidence) → retrieval over SOPs and policy docs (RAG) → tool calls into [order/settlement/KYC] systems via MCP-style tool contracts → response drafted with structured output → guardrails (PII, policy, confidence threshold) → auto-resolve or hand to agent with a pre-filled summary. Async pipeline on Celery; metrics on containment, accuracy, latency, cost per ticket.
*Diagram: intake → classifier → [RAG | tools] → draft → guardrails → {auto-resolve | agent} with metrics tap.*
**Key decisions.** (1) The model never asserts financial facts — every number comes from a tool call to the source of truth; the LLM formats and explains. (2) Use cases onboarded one at a time behind a confidence threshold, with shadow mode before auto-resolution. (3) [Eval approach: N golden tickets, pass/fail criteria per use case, judge–human agreement N%.]
**Outcome.** 85–100 auto-resolutions/day across [N] use cases; ₹50L/month human-agent cost removed; CSAT [N]; team of five onboarding new use cases.
**What I'd change.** [e.g., build the eval harness before the second use case, not after; move orchestration to a durable graph with per-step checkpoints; tighter cost budgets per tenant.]

### 5.2 Payments Platform-as-a-Service — smallcase
**Problem.** Multiple products (digital gold, platform membership, [N] others) each integrated payment gateways separately; recurring and token-based flows were inconsistent and reconciliation was manual.
**Constraints.** Four gateways with different semantics (Razorpay, Juspay, Apple In-App Purchase, Zerodha), three payment types (one-time, subscription, token-based recurring), idempotency under retries, daily reconciliation, PCI-scope minimisation.
**Architecture.** Gateway adapters behind one interface → payment orchestration service with an explicit payment state machine → idempotency keys on every write → webhook ingestion with signature verification, dedupe and replay → reconciliation job against gateway settlement reports → events to product services. Go services, NestJS for [component], MongoDB, AWS (SQS/SNS).
*Diagram: products → PaaS API → orchestrator/state machine → adapters → gateways; webhooks → ingestion → recon → events.*
**Key decisions.** (1) One state machine for all gateways with gateway-specific adapters — adding Zerodha's legacy flow became an adapter, not a rewrite. (2) Token-based mandates modelled as first-class entities with their own lifecycle. (3) Reconciliation as a product feature, not an ops script.
**Outcome.** [N transactions/year, ₹N volume], [N]% success rate, [N] products onboarded, [N]% fewer reconciliation mismatches, digital-gold recurring purchases enabled.
**What I'd change.** [e.g., double-entry ledger from day one; outbox pattern for events; Postgres over MongoDB for the state machine.]

### 5.3 Order management and portfolio platform — Keenai Global
**Problem.** A private-wealth platform for family offices and institutions needs orders across [N] exchanges, accurate valuations, and point-in-time portfolio views over 100K+ transactions per client.
**Constraints.** Multi-market (US, Singapore, [N] more), multiple price sources with different quality and timing, audit and compliance, reconciliation with custodians.
**Architecture.** Order-management service (validation, routing per exchange, state machine, [N] orders/day) → domain-events service (org-wide, at-least-once, idempotent consumers, [N event types]) → portfolio service with versioning (immutable transaction log + point-in-time snapshots) → price-hierarchy engine that ranks sources per instrument and applies fallbacks → reports/metrics/allocations. Go, Node.js, Python, MongoDB.
*Diagram: OMS → events → portfolio/versioning ← price hierarchy ← price sources; reports on top.*
**Key decisions.** (1) Price selection as a declarative hierarchy rather than code paths — reduced reconciliation breaks by 20%. (2) Versioning via append-only transactions and snapshots so any historical view is reproducible. (3) Events as the integration boundary between teams.
**Outcome.** 20% fewer recon breaks; [N] family offices across [N] markets; [N] services consuming the events platform.
**What I'd change.** [fill]

### 5.4 Go application framework — Zopsmart
**Problem.** Every new Go service re-implemented config, HTTP/CLI bootstrap, pub/sub, metrics and AWS clients.
**Constraints.** Must not lock teams into one style; must be adoptable incrementally; must expose metrics uniformly.
**Architecture.** Small interfaces for pub/sub (SNS), metrics (Prometheus), storage and AWS clients; functional-options constructors; middleware chain; CSP for inter-service auth.
**Key decisions.** Interfaces at the edges, no global state, escape hatches everywhere.
**Outcome.** Adopted by [N] services; time-to-first-service from [N] to [N].
**What I'd change.** [fill — this is a great "what would you do differently" answer for design-judgement rounds.]

---

## 6. Technical fixes

### 6.1 The `{{ sk }}` bug
Symptom: the page ships the literal `{{ sk }}` text, so the template engine never ran over that block. Likely causes, in order:
1. **GitHub Pages + Jekyll:** the loop is `{% for sk in site.data.skills.languages %}{{ sk }}{% endfor %}` but the data file (`_data/skills.yml`) is missing, misnamed, or the key path is wrong — Liquid renders the loop zero times only if the collection is empty, so if you're seeing `{{ sk }}` verbatim the file is probably not being processed by Jekyll at all (no front matter `---` at the top of the HTML file, or the file is in a folder Jekyll excludes, or `.nojekyll` exists in the repo root).
2. **Static HTML with a client-side template lib** (Handlebars/Nunjucks/Mustache) that isn't loaded or runs before the data is available.
3. **Framework build** (Astro/Vite/Next) deployed from the wrong branch/dir so unbuilt source is served.
Fix path: check the repo for `_config.yml`/front matter vs a `dist/` build; run the build locally; if it's not worth debugging today, hardcode the skills block from §4.4 and remove the loop. Verify in an incognito window on mobile and desktop.

### 6.2 Head and metadata
`<title>Utsav Vaghani — Senior Backend Engineer (Payments, GenAI)</title>` · `<meta name="description" content="Backend engineer in fintech: payments PaaS across four gateways, alerting for 5M users, production GenAI at Razorpay. Go · Node.js · Python.">` · Open Graph `og:title`, `og:description`, `og:image` (1200×630 PNG with your name and positioning), `og:url` · Twitter card tags · favicon (SVG + PNG) · canonical URL · `robots.txt` and `sitemap.xml` (Jekyll can generate) · `lang="en"` on `<html>`.

### 6.3 Resume hosting
Put `resume.pdf` in the repo root (Jekyll copies it), link it from the hero, and show "Updated Mon YYYY" next to the link. Keep the Drive link only as a private backup.

### 6.4 Performance, accessibility, hygiene
System font stack or one self-hosted font; compress diagrams (SVG or ≤ 150 KB PNG); no third-party scripts except analytics; colour contrast ≥ 4.5:1 (check the dark theme); alt text on diagrams; keyboard-navigable links; a 404 page; Lighthouse ≥ 90 on all four; test on a phone. Analytics: Plausible or GA4 so you can see which referral messages convert to visits.

### 6.5 Optional
Custom domain (e.g., `utsavvaghani.dev`) with HTTPS enforced — small polish, not required. A `/now` or `/writing` page only if you'll actually publish.

---

## 7. GitHub

### 7.1 Profile README (replace "currently working on GoLang")
> Backend engineer in fintech — payments infrastructure and production GenAI. Go · Node.js · Python · AWS. Currently building order-management and portfolio services for a private-wealth platform at Keenai Global; previously led GenAI support automation at Razorpay and built smallcase's payments PaaS. Pinned repos below are small, runnable reference implementations of things I've built at work. Resume: utsav-vaghani.github.io/resume.pdf

### 7.2 Pinned repositories — plan (four, in this order)
1. **yogi-lite** — LangGraph router → specialist support agent over a public ticket dataset; Postgres checkpointer; three tools including one side-effecting tool with an idempotency key and an approval interrupt; promptfoo eval suite with a 60-case golden set and judge–human agreement reported in the README. *(This is the repo AI-platform interviewers will read.)*
2. **go-llm-gateway** — multi-provider routing, per-tenant token budgets and rate limits, exact + semantic cache, fallback, streaming, OpenTelemetry spans; table-driven tests; `docker compose up`.
3. **idempotent-webhook-worker** — Go: signature verification, dedupe store, at-least-once consumer with outbox, retries with jitter, DLQ; a README that explains the exactly-once myth.
4. **ledger-go** — minimal double-entry ledger library with `NUMERIC`-safe money, journal + balance snapshots, property tests for invariants.
Each: README with a diagram, a "why this exists" paragraph, a 30-second run command, CI badge, MIT licence. Archive or unpin ContestReminder and Book-Rentals; fix "Personal Protfolio"; add repo topics (`golang`, `payments`, `langgraph`, `llm-evals`).

### 7.3 Green squares don't matter; runnable READMEs do
Interviewers open one repo for two minutes. Make the README carry the design decisions; make `make run` work.

---

## 8. Consistency checklist (site ↔ resume ↔ LinkedIn ↔ Naukri)
- [ ] Company names, titles, and start/end months identical across all four
- [ ] Same three headline numbers (5M users · 4 gateways · ₹50L/month) everywhere
- [ ] Same positioning line (LinkedIn headline = site hero line)
- [ ] Resume PDF on the site is the same file you upload to portals
- [ ] Glabbr appears on all or none
- [ ] Skills lists agree (no tool on the site that isn't on the resume)

---

## 9. Priority and time plan
**Today (1 hr):** fix `{{ sk }}` (or hardcode), correct dates/title, fix the four copy errors, remove Instagram, host `/resume.pdf`.
**This week (3 hrs):** new hero + proof strip, About paragraph, Experience bullets with numbers, meta/OG tags, GitHub README and repo descriptions.
**Weekend 1 (4 hrs):** case studies 5.1 and 5.2 with diagrams.
**Weekend 2 (4 hrs):** case studies 5.3 and 5.4; Lighthouse pass; mobile check.
**Weeks 3–4:** yogi-lite and go-llm-gateway repos (these double as GenAI interview prep — see Doc 3 §6.4).

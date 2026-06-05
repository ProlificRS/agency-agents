# PROLIFIC NEXUS — ProlificWebCraft Agency Orchestration Playbook

> **Version**: 1.0.0 | **Status**: Production | **Maintainer**: Project Shepherd Agent

---

## Table of Contents

1. [What PROLIFIC NEXUS Is](#1-what-prolific-nexus-is)
2. [The 7-Phase Pipeline](#2-the-7-phase-pipeline)
3. [Agent Activation Prompts](#3-agent-activation-prompts)
4. [Quality Gates](#4-quality-gates)
5. [Handoff Contracts](#5-handoff-contracts)
6. [Passive Income Automation](#6-passive-income-automation)
7. [Quick-Start Modes](#7-quick-start-modes)

---

## 1. What PROLIFIC NEXUS Is

**PROLIFIC NEXUS** is the master orchestration layer that transforms ProlificWebCraft's roster of specialized AI agents into a unified, end-to-end delivery pipeline. Rather than running agents in isolation, NEXUS coordinates every agent in sequence and in parallel — passing context, enforcing quality gates, automating handoffs, and generating recurring revenue with minimal human intervention.

NEXUS is not a tool. It is the **operating system** of ProlificWebCraft.

### The 4 Service Types NEXUS Delivers

| Service Type | Description | Typical Timeline | Primary Revenue Path |
|---|---|---|---|
| **Website** | Brochure sites, portfolios, landing pages, multi-page business sites | 1–3 weeks | Hosting + SEO retainer |
| **SaaS** | Full-stack web applications with auth, billing, multi-tenancy, dashboards | 4–12 weeks | Platform management retainer |
| **E-Commerce** | Product stores with payments, inventory, order management, checkout | 2–6 weeks | Content + SEO retainer |
| **dApp** | Decentralized application frontends with wallet integration, smart contract UI | 3–8 weeks | Hosting + content retainer |

Every project passes through the same 7-phase pipeline, with phase depth scaled by service type and NEXUS mode (Full / Sprint / Micro).

### Core Design Principles

1. **No Agent Works Alone** — Every phase requires explicit handoff from the previous phase. Agents receive a structured context packet, not a freeform prompt.
2. **Quality Gates Are Non-Negotiable** — Phases do not advance without documented sign-off artifacts.
3. **Automation First** — Any task performable by the agent swarm without human input is automated by default.
4. **Revenue Embedded** — Phase 6 is not optional. Every project exits into a revenue-generating operate phase.

---

## 2. The 7-Phase Pipeline

### Pipeline Overview Table

| Phase | Name | Primary Agents | Key Output | Gate Before Advance |
|---|---|---|---|---|
| **0** | Client Discovery | Onboarding Agent, SEO Agent, Project Shepherd | Discovery Brief, SEO Baseline Report | Client approval of brief |
| **1** | Architecture & Strategy | Software Architect, UX Architect, Backend Architect, Brand Guardian | Tech Stack Decision, Wireframes, Brand Kit | Internal review sign-off |
| **2** | Foundation & Scaffolding | DevOps Automator, Frontend Developer, Backend Architect | Repo, CI/CD pipeline, deployed skeleton | Staging environment live |
| **3** | Build & Iterate | All Builder Agents, Evidence Collector, Reality Checker | Feature-complete product | All QA loops passed |
| **4** | Visual Builder Integration | Visual Builder Agent | Client-editable platform | Client editor training complete |
| **5** | SEO & Launch | SEO Growth Agent, Growth Hacker, Social Media Strategist, DevOps Automator | Live production deploy, indexed, announced | Google index confirmed |
| **6** | Operate & Earn | Revenue Manager, Infrastructure Maintainer, Support Responder, Analytics Reporter | Monthly MRR, uptime SLA, reports | Recurring subscription active |

---

### Phase 0 — Client Discovery

**Duration**: 1–3 days  
**Agents**: Onboarding Agent, SEO Agent, Project Shepherd

The first contact phase. The goal is to transform a raw client inquiry into a structured, actionable Discovery Brief that every downstream agent can consume without ambiguity.

**Activities**:
- Onboarding Agent collects: business name, industry, goals, target audience, competitors, budget, timeline, content assets
- SEO Agent runs baseline audit: current domain authority, existing rankings, target keyword landscape, competitor keyword gaps
- Project Shepherd synthesizes inputs into Discovery Brief and selects NEXUS mode (Full / Sprint / Micro)

**Artifacts Produced**:
- `discovery-brief.md` — structured client context document
- `seo-baseline-report.md` — current SEO state + target keyword list (50–200 keywords)
- `project-manifest.json` — machine-readable project spec for agent consumption
- `timeline-estimate.md` — phase-by-phase schedule with milestones

---

### Phase 1 — Architecture & Strategy

**Duration**: 2–5 days  
**Agents**: Software Architect, UX Architect, Backend Architect, Brand Guardian

Converts the Discovery Brief into technical and visual blueprints. No code is written in this phase — only decisions documented.

**Activities**:
- Software Architect selects tech stack (Next.js / Nuxt / Remix for frontend; Node/Go/Python for backend; Postgres/MySQL/MongoDB for database; Vercel/Hostinger/AWS for hosting)
- UX Architect produces wireframes (Figma or annotated markdown) for all primary user flows
- Backend Architect designs the data model (ERD), API contract (OpenAPI spec), and authentication strategy
- Brand Guardian defines color palette, typography system, logo usage rules, tone-of-voice guidelines

**Artifacts Produced**:
- `tech-stack-decision.md` — rationale for every major technology choice
- `wireframes/` — screen-by-screen wireframe set
- `data-model.md` — ERD + table definitions
- `api-contract.yaml` — OpenAPI 3.0 specification
- `brand-kit/` — colors, fonts, logo files, tone guidelines

---

### Phase 2 — Foundation & Scaffolding

**Duration**: 2–5 days  
**Agents**: DevOps Automator, Frontend Developer, Backend Architect

The repository, CI/CD pipeline, and deployed skeleton environment are stood up. By end of phase, a live staging URL exists.

**Activities**:
- DevOps Automator: provisions GitHub repo, configures GitHub Actions workflows, sets up staging server on Hostinger VPS, configures domain DNS
- Frontend Developer: scaffolds frontend project (Next.js with Tailwind, component library, routing structure)
- Backend Architect: scaffolds backend API (Express/Fastify/Hono), database migrations, environment variable management, auth middleware stub

**Artifacts Produced**:
- GitHub repository (public or private per client agreement)
- `.github/workflows/` — CI (lint + test) and CD (deploy to staging) pipelines
- `staging-url.txt` — confirmed live staging environment URL
- `env-template.md` — all required environment variables documented (values excluded)

---

### Phase 3 — Build & Iterate

**Duration**: 1–6 weeks (scales with service type)  
**Agents**: All Builder Agents, Evidence Collector, Reality Checker

The core development phase. Runs in dev↔QA loops with structured iteration cycles. Each loop produces shippable increments.

**Loop Structure**:

```
┌─────────────────────────────────────────────────────────────┐
│  ITERATION LOOP (repeat until feature-complete)              │
│                                                               │
│  1. Builder Agents implement feature batch                    │
│  2. Evidence Collector documents: screenshots, test results,  │
│     API response samples, Lighthouse scores                   │
│  3. Reality Checker audits: does it match wireframes?         │
│     Does it match API contract? Does it pass QA criteria?     │
│  4. If FAIL → back to step 1 with specific failure notes     │
│  5. If PASS → mark feature batch complete, next batch         │
└─────────────────────────────────────────────────────────────┘
```

**QA Criteria Per Service Type**:

| Check | Website | SaaS | E-Com | dApp |
|---|---|---|---|---|
| Lighthouse Performance ≥ 90 | ✓ | ✓ | ✓ | ✓ |
| Lighthouse Accessibility ≥ 90 | ✓ | ✓ | ✓ | ✓ |
| Mobile responsive (320px–1440px) | ✓ | ✓ | ✓ | ✓ |
| Auth flows tested | — | ✓ | ✓ | ✓ |
| Payment flow tested (sandbox) | — | ✓ | ✓ | — |
| Wallet connect tested | — | — | — | ✓ |
| All forms validated | ✓ | ✓ | ✓ | ✓ |
| 404/error pages exist | ✓ | ✓ | ✓ | ✓ |
| Environment variables externalized | ✓ | ✓ | ✓ | ✓ |
| No console errors in production build | ✓ | ✓ | ✓ | ✓ |

---

### Phase 4 — Visual Builder Integration

**Duration**: 1–3 days  
**Agents**: Visual Builder Agent

The platform is wrapped with ProlificWebCraft's no-code visual editing layer, enabling the client to self-manage their platform post-handoff.

**Activities**:
- Visual Builder Agent integrates GrapesJS for drag-and-drop page editing
- CMS integration (TinaCMS or Sanity) configured for content types
- SEO Control Panel deployed for per-page SEO editing
- Permissions matrix enforced (admin / editor / viewer roles)
- Client training session conducted (5-minute onboarding checklist completed)

**Artifacts Produced**:
- `visual-editor/` — integrated GrapesJS implementation
- `cms-config/` — TinaCMS or Sanity schema definitions
- `seo-panel/` — per-page SEO editing UI
- `editor-training-checklist.md` — client sign-off document

---

### Phase 5 — SEO & Launch

**Duration**: 3–7 days  
**Agents**: SEO Growth Agent, Growth Hacker, Social Media Strategist, DevOps Automator

The platform goes live. Search engines are notified. The launch is announced across channels.

**Activities**:
- DevOps Automator promotes staging to production (zero-downtime deploy), configures SSL, sets up CDN (Cloudflare)
- SEO Growth Agent: submits XML sitemap to Google Search Console + Bing Webmaster Tools, verifies indexation of all pages, implements schema markup
- Growth Hacker: sets up Google Analytics 4, Hotjar, goal funnels, UTM tracking
- Social Media Strategist: drafts and schedules launch announcement posts for client's social channels

**Artifacts Produced**:
- `production-url.txt` — confirmed live URL
- `google-search-console-verification.md` — verified property screenshot
- `launch-announcement-posts.md` — social media content (3–5 platforms)
- `analytics-setup.md` — GA4 + heatmap configuration

---

### Phase 6 — Operate & Earn

**Duration**: Ongoing (months → years)  
**Agents**: Revenue Manager Agent, Infrastructure Maintainer, Support Responder, Analytics Reporter

The revenue engine. Every project that exits Phase 5 enters Phase 6 automatically. This phase pays ProlificWebCraft indefinitely.

**Recurring Activities (Monthly)**:
- Infrastructure Maintainer: security patch checks, dependency updates, uptime monitoring, backup verification
- Support Responder: handles client tickets, answers platform questions, escalates bugs to builder agents
- Analytics Reporter: produces monthly performance report (traffic, conversions, SEO ranking changes, search volume)
- Revenue Manager Agent: generates and sends Stripe invoices, monitors subscription status, flags churn risk, upsell opportunities

**Revenue Generated Per Client Per Month**: `$99` (minimum) → `$2,500+` (full stack retainer)

---

## 3. Agent Activation Prompts

Use these prompts to initialize NEXUS for a new project. Paste into the Project Shepherd Agent to kick off Phase 0.

---

### Website Project Activation

```
NEXUS ACTIVATE — SERVICE TYPE: WEBSITE
Mode: [NEXUS-Full | NEXUS-Sprint | NEXUS-Micro]

Client: [CLIENT_NAME]
Industry: [INDUSTRY]
Goal: [PRIMARY_GOAL — e.g. "generate leads for local plumbing business"]
Pages Required: [LIST — e.g. Home, About, Services, Contact, Blog]
Has Content: [YES/NO — if NO, Content Creator Agent will draft all copy]
Budget: [RANGE]
Timeline: [DEADLINE or WEEKS]
Domain: [DOMAIN or "not yet purchased"]
Competitors: [LIST 3 COMPETITORS]

Phase 0 agents: Onboarding Agent, SEO Agent, Project Shepherd
Produce: discovery-brief.md, seo-baseline-report.md, project-manifest.json
Proceed when: Client approves Discovery Brief
```

---

### SaaS Project Activation

```
NEXUS ACTIVATE — SERVICE TYPE: SAAS
Mode: [NEXUS-Full | NEXUS-Sprint | NEXUS-Micro]

Client: [CLIENT_NAME]
App Name: [APP_NAME]
Problem Solved: [ONE SENTENCE]
Target Users: [USER PERSONA]
Key Features (MVP): [LIST 5–10 FEATURES]
Auth Method: [Email/password | OAuth | Magic Link | SSO]
Billing: [Stripe | Paddle | No billing]
Multi-tenant: [YES/NO]
Integrations Required: [LIST APIs, webhooks, etc.]
Hosting Budget: [$/mo server budget]
Timeline: [DEADLINE or WEEKS]

Phase 0 agents: Onboarding Agent, SEO Agent, Project Shepherd
Produce: discovery-brief.md, seo-baseline-report.md, project-manifest.json, feature-priority-matrix.md
Proceed when: Feature list signed off, tech stack approved
```

---

### E-Commerce Project Activation

```
NEXUS ACTIVATE — SERVICE TYPE: E-COMMERCE
Mode: [NEXUS-Full | NEXUS-Sprint | NEXUS-Micro]

Client: [CLIENT_NAME]
Store Name: [STORE_NAME]
Product Type: [Physical | Digital | Subscription | Mixed]
SKU Count (initial): [NUMBER]
Payment Processor: [Stripe | PayPal | Crypto | Multiple]
Shipping Integration: [Shippo | EasyPost | Manual | None]
Inventory Management: [Self-managed | 3PL | Dropship]
Has Brand Assets: [YES/NO]
Target Market: [GEO — e.g. US, EU, Global]
Budget: [RANGE]
Timeline: [DEADLINE or WEEKS]

Phase 0 agents: Onboarding Agent, SEO Agent, Project Shepherd
Produce: discovery-brief.md, seo-baseline-report.md, product-catalog-template.csv, project-manifest.json
Proceed when: Product catalog seeded, payment processor connected (sandbox)
```

---

### dApp Project Activation

```
NEXUS ACTIVATE — SERVICE TYPE: DAPP
Mode: [NEXUS-Full | NEXUS-Sprint | NEXUS-Micro]

Client: [CLIENT_NAME]
Project Name: [DAPP_NAME]
Blockchain: [Ethereum | Solana | Polygon | Base | Other]
Smart Contracts: [Already deployed | In development | Not started]
Contract Addresses: [LIST if deployed]
Wallet Integration: [MetaMask | WalletConnect | Phantom | Multiple]
Frontend Sections: [Hero, Roadmap, Tokenomics, Team, FAQ, Mint UI, Staking UI, etc.]
Token: [Token name + ticker if applicable]
Whitepaper: [Link or "not yet written"]
Has Brand Assets: [YES/NO]
Timeline: [DEADLINE or WEEKS]

IMPORTANT: Visual Builder Agent will NOT edit smart contracts.
Phase 0 agents: Onboarding Agent, SEO Agent, Project Shepherd
Produce: discovery-brief.md, seo-baseline-report.md, project-manifest.json, contract-interface-spec.md
Proceed when: Contract ABIs provided (or stubbed), wallet connection tested in dev
```

---

## 4. Quality Gates

Quality gates are hard stops. No phase advances unless every gate item is checked and documented. The Reality Checker Agent enforces all gates.

### Gate 0→1: Discovery Complete

- [ ] `discovery-brief.md` exists and is complete (no blank fields)
- [ ] Client has reviewed and approved the Discovery Brief in writing
- [ ] SEO baseline report generated (minimum 20 target keywords identified)
- [ ] Budget and timeline agreed
- [ ] `project-manifest.json` validated (JSON schema check passes)

### Gate 1→2: Architecture Approved

- [ ] Tech stack decision documented with rationale for each choice
- [ ] All primary user flows have wireframes
- [ ] Data model reviewed by Backend Architect (no N+1 query risks, all relationships defined)
- [ ] OpenAPI spec covers 100% of planned endpoints
- [ ] Brand kit assets delivered (logo SVG, color tokens, font files)

### Gate 2→3: Scaffolding Live

- [ ] GitHub repository accessible by all agents
- [ ] CI pipeline runs green on first push
- [ ] Staging URL is live and returning HTTP 200
- [ ] Database migrations run without error
- [ ] Environment variables documented (`.env.example` committed)
- [ ] Auth stub returns 200/401 as expected

### Gate 3→4: Build Complete

- [ ] All features in `project-manifest.json` marked DONE or DEFERRED (with client sign-off on deferrals)
- [ ] Lighthouse scores ≥ 90 (Performance, Accessibility, Best Practices, SEO) on staging
- [ ] Zero console errors in production build
- [ ] All user flows tested end-to-end (Evidence Collector screenshots attached)
- [ ] Reality Checker sign-off document exists

### Gate 4→5: Visual Builder Ready

- [ ] GrapesJS editor loads on staging without errors
- [ ] At least one page fully editable via visual editor
- [ ] SEO Control Panel edits saving correctly to database/CMS
- [ ] Client has completed 5-minute editor training checklist
- [ ] Permission roles tested (admin can edit, viewer cannot)

### Gate 5→6: Launch Complete

- [ ] Production URL live and returning HTTP 200 over HTTPS
- [ ] SSL certificate valid (no browser warnings)
- [ ] All pages indexed in Google Search Console (or sitemap submitted and processing)
- [ ] GA4 recording sessions
- [ ] Launch announcement published on at least 2 channels
- [ ] Stripe subscription (recurring retainer) activated

### Ongoing Gate (Monthly, Phase 6)

- [ ] Uptime ≥ 99.5% (Infrastructure Maintainer report)
- [ ] All critical security patches applied
- [ ] Monthly analytics report delivered to client
- [ ] Invoice paid (Revenue Manager Agent confirms)

---

## 5. Handoff Contracts

Agents receive and emit structured **Context Packets** — not freeform prompts. This ensures zero information loss across phase transitions.

### Standard Context Packet Structure

```json
{
  "nexus_version": "1.0.0",
  "project_id": "PROJ-[CLIENT_SLUG]-[YYYY-MM]",
  "service_type": "website | saas | ecom | dapp",
  "nexus_mode": "full | sprint | micro",
  "current_phase": 0,
  "target_phase": 1,
  "client": {
    "name": "",
    "industry": "",
    "domain": "",
    "primary_contact_email": ""
  },
  "artifacts": {
    "discovery_brief": "path/to/discovery-brief.md",
    "seo_baseline": "path/to/seo-baseline-report.md",
    "tech_stack": "path/to/tech-stack-decision.md",
    "wireframes": "path/to/wireframes/",
    "api_contract": "path/to/api-contract.yaml",
    "brand_kit": "path/to/brand-kit/",
    "staging_url": "",
    "production_url": ""
  },
  "quality_gate_sign_off": {
    "gate_0": false,
    "gate_1": false,
    "gate_2": false,
    "gate_3": false,
    "gate_4": false,
    "gate_5": false
  },
  "open_issues": [],
  "deferred_features": [],
  "notes": ""
}
```

### Handoff Rules

1. **Every agent reads the Context Packet first** before taking any action. If the packet is missing, the agent must request it before proceeding.
2. **Every agent writes back to the packet** — updating artifact paths, marking gate items, appending open issues.
3. **No out-of-band communication** — agents do not share information via free-text comments that bypass the packet. All key information lives in the JSON.
4. **Deferrals require client sign-off** — if a feature is moved to `deferred_features`, a written client acknowledgment must be attached.
5. **The Project Shepherd Agent is the packet custodian** — it holds the master copy and arbitrates conflicts.

### Phase-Specific Handoff Notes

| Handoff | Sending Agent | Receiving Agent | Critical Data |
|---|---|---|---|
| 0 → 1 | Project Shepherd | Software Architect | `discovery-brief.md`, keyword list, budget constraints |
| 1 → 2 | Software Architect | DevOps Automator | `tech-stack-decision.md`, `api-contract.yaml`, hosting requirements |
| 2 → 3 | DevOps Automator | All Builder Agents | Staging URL, repo URL, CI/CD workflow docs, `env-template.md` |
| 3 → 4 | Reality Checker | Visual Builder Agent | List of all editable page sections, CMS content types, admin user credentials (temp) |
| 4 → 5 | Visual Builder Agent | SEO Growth Agent | Live staging URL with editor integrated, sitemap URL, all page URLs |
| 5 → 6 | SEO Growth Agent | Revenue Manager Agent | Production URL, GA4 property ID, Stripe customer ID, agreed retainer amount |

---

## 6. Passive Income Automation

Phase 6 is where ProlificWebCraft's business model compounds. Every client that reaches Phase 6 is generating monthly recurring revenue (MRR) automatically.

### The 5 Revenue Streams

| Stream | Monthly Range | Who Automates It | Trigger |
|---|---|---|---|
| Hosting & Maintenance Retainer | $99–$299/mo | Revenue Manager Agent + Infrastructure Maintainer | Auto-charged on deploy anniversary |
| SEO Retainer | $299–$999/mo | SEO Growth Agent + Revenue Manager Agent | Monthly ranking report auto-generated |
| Content Update Package | $149–$499/mo | Visual Builder Agent + Content Creator Agent | Monthly content batch auto-queued |
| SaaS Platform Management | $499–$1,499/mo | Infrastructure Maintainer + Support Responder | Ongoing SLA monitoring |
| Search Engine Package | $199–$599/mo | Search Engine Agent + Analytics Reporter | Monthly ROI report auto-generated |

### Automation Stack

```
Client Onboards to Phase 6
        │
        ▼
Revenue Manager Agent
  ├── Creates Stripe Customer
  ├── Activates Subscription (retainer tier)
  ├── Sets up webhook: payment_succeeded → log revenue
  ├── Sets up webhook: payment_failed → alert + dunning sequence
  └── Logs to SuiteCRM (deal → client record)
        │
        ▼
Monthly Cycle (GitHub Actions cron: 0 0 1 * *)
  ├── Infrastructure Maintainer:
  │     ├── Runs dependency audit (npm audit / pip check)
  │     ├── Applies non-breaking security patches
  │     ├── Verifies backup completed in last 24h
  │     └── Posts uptime report to client Slack/email
  ├── Analytics Reporter:
  │     ├── Pulls GA4 data via API
  │     ├── Pulls GSC data via API
  │     ├── Generates monthly PDF report
  │     └── Emails to client
  ├── SEO Growth Agent (if SEO retainer active):
  │     ├── Pulls ranking positions for all tracked keywords
  │     ├── Flags drops > 5 positions
  │     ├── Generates content gap report from search data
  │     └── Queues 2–4 content recommendations
  └── Revenue Manager Agent:
        ├── Confirms Stripe invoice paid
        ├── Scans for upsell signals (high traffic → suggest search engine)
        └── Queues upsell email if signal threshold met
```

### Why This Compounds

- No churn action required from ProlificWebCraft staff — subscriptions auto-renew
- No manual reporting — all reports generated by agents
- Upsell sequences fire automatically when analytics show opportunity
- New projects feed Phase 6 continuously — MRR base only grows
- Average client lifetime: 18–36 months (high switching cost once platform is embedded)

---

## 7. Quick-Start Modes

### Mode 1 — NEXUS-Full

**Use For**: Complete business platforms, complex SaaS, multi-feature e-commerce, full dApp  
**Timeline**: 6–12 weeks  
**All Phases Active**: 0 → 1 → 2 → 3 → 4 → 5 → 6

NEXUS-Full runs every phase at full depth. All quality gates enforced. All artifacts required. All agents activated in sequence. Full Visual Builder integration. Full SEO launch. Full Phase 6 retainer stack.

**Entry Point**:
```
Project Shepherd: NEXUS-Full initiated for [PROJECT_ID]
Activate Phase 0. Onboarding Agent begin Discovery Interview.
```

---

### Mode 2 — NEXUS-Sprint

**Use For**: MVPs, early-stage startups, proof-of-concept platforms, quick market validation  
**Timeline**: 2–4 weeks  
**Compressed Phases**: 0 (1 day) → 1 (1 day) → 2 (2 days) → 3 (1–2 weeks) → 5 (2 days) → 6

Phase 4 (Visual Builder) is optional in Sprint mode — can be added post-launch. Phase 1 wireframes are low-fidelity only. Quality gate checklists are shortened (5 items max per gate). The goal is a live, functional MVP that can be iterated post-launch.

**Entry Point**:
```
Project Shepherd: NEXUS-Sprint initiated for [PROJECT_ID]
Compress Phase 0 to 1 day. Skip Phase 4 unless client requests.
Activate Phase 0. Onboarding Agent begin rapid Discovery (async form preferred).
```

---

### Mode 3 — NEXUS-Micro

**Use For**: Single-task deliverables — one landing page, one bug fix, one SEO audit, one component  
**Timeline**: 1–3 days  
**Phases Active**: 0 (scoping only) → 3 (single feature build) → 5 (deploy to existing env)

NEXUS-Micro skips architecture, scaffolding, and Visual Builder phases. It plugs directly into an existing project environment. Ideal for add-on work, client change requests, or small new client engagements that grow into NEXUS-Full later.

**Entry Point**:
```
Project Shepherd: NEXUS-Micro initiated for [PROJECT_ID]
Task: [SINGLE TASK DESCRIPTION]
Existing Repo: [REPO_URL]
Staging URL: [URL]
Activate Phase 3 directly. Reality Checker review on completion.
```

---

### Mode Comparison Table

| Attribute | NEXUS-Full | NEXUS-Sprint | NEXUS-Micro |
|---|---|---|---|
| Timeline | 6–12 weeks | 2–4 weeks | 1–3 days |
| Phase count | 7 (all) | 5 (0,1,2,3,5,6) | 3 (0,3,5) |
| Visual Builder | Required | Optional | No |
| Quality gates | Full (7 gates) | Abbreviated (5 items/gate) | Pass/fail only |
| SEO launch | Full | Basic | Deployment only |
| Phase 6 retainer | Required | Required | Optional |
| Typical value | $3,000–$25,000 | $1,500–$8,000 | $250–$1,500 |

---

*PROLIFIC NEXUS v1.0.0 — ProlificWebCraft Internal Document — Do Not Distribute*

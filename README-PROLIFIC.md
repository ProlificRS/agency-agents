# 🏗️ ProlificWebCraft Agency Platform

> **A complete AI-powered software agency** — Built on [The Agency](https://github.com/msitarzewski/agency-agents) agent framework, customized for [ProlificWebCraft LLC](https://prolificwebcraft.info). From client intake to deployed platform to recurring revenue, every step is automated by specialized AI agents.

---

## What Is This?

This is the full operational brain of **ProlificWebCraft LLC** — a coordinated swarm of AI agents that:

- **Takes on new clients** automatically (intake, qualification, onboarding)
- **Builds** websites, SaaS platforms, e-commerce stores, and dApps
- **Embeds a self-editing visual builder** into every delivery so clients manage their own content
- **Grows organic traffic** via a built-in SEO engine and Prolific Search
- **Generates recurring passive income** through automated retainer billing
- **Creates new agents on demand** for any project type

All agents run in Cursor, Claude Code, or any tool that supports the base [agency-agents](https://github.com/ProlificRS/agency-agents) format.

---

## 🗂️ Structure

```
prolific-agency/
├── prolific/                        # ProlificWebCraft core agents
│   ├── prolific-client-onboarding-agent.md
│   ├── prolific-website-builder-agent.md
│   ├── prolific-saas-builder-agent.md
│   ├── prolific-ecom-builder-agent.md
│   ├── prolific-dapp-builder-agent.md
│   ├── prolific-seo-growth-agent.md
│   ├── prolific-revenue-manager-agent.md
│   ├── prolific-project-shepherd-agent.md
│   └── prolific-agent-factory.md
├── visual-builder/
│   └── prolific-visual-builder-agent.md   # No-code self-editing system
├── search-engine/
│   └── prolific-search-engine-agent.md    # Prolific Search — Typesense-powered
├── strategy/
│   └── prolific-nexus-strategy.md         # Full orchestration playbook
└── revenue/
    └── prolific-passive-income-playbook.md # MRR engine & income projections
```

---

## 🚀 Quick Start

### Install to Cursor (Recommended)

```bash
# From your project root
cp -r prolific-agency/prolific ~/.cursor/rules/
cp prolific-agency/visual-builder/*.md ~/.cursor/rules/
cp prolific-agency/search-engine/*.md ~/.cursor/rules/
```

### Install to Claude Code

```bash
cp -r prolific-agency/prolific ~/.claude/agents/
cp prolific-agency/visual-builder/*.md ~/.claude/agents/
cp prolific-agency/search-engine/*.md ~/.claude/agents/
```

### Activate Any Agent

```
@prolific-client-onboarding-agent A new client reached out — they need an e-commerce store for a local bakery, budget ~$2,500 build + monthly retainer. Run full intake.
```

---

## 🎛️ The PROLIFIC NEXUS Pipeline

The full delivery pipeline is orchestrated across **7 phases**:

| Phase | Name | Key Agents |
|-------|------|------------|
| 0 | Client Discovery | Client Onboarding, SEO Growth, Project Shepherd |
| 1 | Architecture & Strategy | Software Architect, UX Architect, Backend Architect |
| 2 | Foundation | DevOps Automator, Frontend Developer, Backend Architect |
| 3 | Build & Iterate | Builder Agents + Evidence Collector + Reality Checker |
| 4 | Visual Builder Handoff | Visual Builder Agent → client self-service |
| 5 | SEO & Launch | SEO Growth Agent, Growth Hacker, Social Media Strategist |
| 6 | Operate & Earn | Revenue Manager, Infrastructure Maintainer, Analytics Reporter |

> See [`strategy/prolific-nexus-strategy.md`](strategy/prolific-nexus-strategy.md) for full activation prompts, quality gates, and handoff contracts.

---

## 🤖 The Agent Roster

### Client & Delivery Division
| Agent | What It Does |
|-------|-------------|
| **Client Onboarding** | Intake, qualification, SuiteCRM sync, welcome sequence, project routing |
| **Project Shepherd** | Timeline management, status updates, scope control, phase handoffs |

### Build Division
| Agent | What It Builds |
|-------|---------------|
| **Website Builder** | HTML/CSS, WordPress, Next.js — Hostinger-deployed, 90+ Lighthouse |
| **SaaS Builder** | Multi-tenant SaaS, Stripe billing, white-label portals, Docker + CI/CD |
| **E-Commerce Builder** | WooCommerce/Shopify/Next.js commerce, Stripe, inventory, email automation |
| **dApp Builder** | Solidity contracts, Web3 frontend, IPFS, MetaMask/WalletConnect, testnets |

### Growth Division
| Agent | What It Drives |
|-------|---------------|
| **SEO & Growth** | Technical audits, keyword research, GA4, GSC, backlinks, monthly reports |
| **Revenue Manager** | MRR tracking, invoice automation, churn alerts, upsell opportunities |

### Infrastructure Division
| Agent | What It Powers |
|-------|---------------|
| **Visual Builder** | GrapesJS drag-and-drop editor embedded in every client platform |
| **Search Engine** | Self-hosted Typesense cluster, site search, federated search, ROI tracking |
| **Agent Factory** | Creates new custom agents on demand for any project or client need |

---

## 🎨 Self-Editing Visual Builder

Every platform delivered by ProlificWebCraft gets an **embedded no-code editor** powered by [GrapesJS](https://grapesjs.com):

- Drag-and-drop block editing — hero, nav, footer, CTAs, galleries, pricing
- Inline content editing — click any text to edit it live
- Built-in **SEO Control Panel** — title tags, meta, Open Graph, schema markup, robots
- One-click search engine submission (Google, Bing, Yandex, DuckDuckGo)
- Version history + rollback for every change
- Works for websites, SaaS dashboards, e-com storefronts, and dApp frontends
- Role-gated: admin / editor / viewer permissions

> Full spec + code examples: [`visual-builder/prolific-visual-builder-agent.md`](visual-builder/prolific-visual-builder-agent.md)

---

## 🔭 Prolific Search Engine

A **self-hosted branded search** system (Typesense) that indexes every platform you build:

- Instant search widget embedded in every client site
- **Federated search** across all Prolific client platforms
- SEO gap analysis: tracks what users search vs. what pages exist
- ROI dashboard: search-to-conversion tracking per client
- Auto-submits new URLs to Google Indexing API + Bing Submission API
- Docker Compose deployment on Hostinger VPS (2-node cluster + nginx)

> Full spec + Docker + code: [`search-engine/prolific-search-engine-agent.md`](search-engine/prolific-search-engine-agent.md)

---

## 💰 Passive Income Engine

Every project deployed becomes a recurring revenue stream:

| Service | Price Range | Margin |
|---------|-------------|--------|
| Hosting & Maintenance Retainer | $99–$299/mo | ~85% |
| SEO Retainer | $299–$999/mo | ~80% |
| Content Update Package | $149–$499/mo | ~75% |
| SaaS Platform Management | $499–$1,499/mo | ~70% |
| Search Engine Package | $199–$599/mo | ~90% |

**24-month projection** (2 new clients/mo avg $350 retainer): **~$18K MRR**

> Full playbook + MRR calculator + funnel map: [`revenue/prolific-passive-income-playbook.md`](revenue/prolific-passive-income-playbook.md)

---

## 🏭 Creating New Agents

Need an agent for a new niche or client? Activate the **Agent Factory**:

```
@prolific-agent-factory Create a new agent for managing cryptocurrency trading bot clients.
The agent should handle: bot configuration intake, performance reporting,
strategy documentation, and monthly P&L summaries.
```

The factory outputs a complete, lint-valid `.md` agent file ready to drop into the roster.

---

## 🔗 Integration

These agents are built on top of the base [agency-agents](https://github.com/ProlificRS/agency-agents) repo. They use the same format and are compatible with all supported tools:

**Cursor** · **Claude Code** · **OpenClaw** · **Windsurf** · **Aider** · **GitHub Copilot** · **Gemini CLI**

---

## 🧱 Tech Stack

| Layer | Technology |
|-------|-----------|
| Hosting | Hostinger VPS / Shared |
| Frontend | React / Next.js / HTML+CSS |
| Backend | Node.js / Express |
| Database | MySQL / PostgreSQL |
| Payments | Stripe Subscriptions |
| CRM | SuiteCRM |
| Search | Typesense (self-hosted) |
| Visual Editor | GrapesJS + TinaCMS / Sanity |
| Smart Contracts | Solidity (EVM) |
| Web3 | Ethers.js / Web3.js |
| CI/CD | GitHub Actions |
| Containers | Docker / Docker Compose |
| AI Tooling | Cursor IDE / Claude AI / OpenClaw |

---

## 📄 License

MIT — same as the base [agency-agents](https://github.com/ProlificRS/agency-agents) repo.

---

*Built by [ProlificWebCraft LLC](https://prolificwebcraft.info) — Empowering Businesses Online.*

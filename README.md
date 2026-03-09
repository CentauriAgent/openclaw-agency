# 🏢 OpenClawn Agency

**A complete AI agency at your fingertips.**

30 specialized agents across 7 divisions — from frontend wizards to growth hackers, from reality checkers to brand guardians. Each agent is a specialized expert with personality, processes, and proven deliverables. All orchestrated through [Beads](https://github.com/soapbox-pub/beads) for task management, dependency tracking, and parallel execution.

Built for [OpenClaw](https://github.com/openclaw/openclaw). Inspired by [msitarzewski/agency-agents](https://github.com/msitarzewski/agency-agents).

---

## 🎯 What Is This?

Most AI agent setups give you one agent that tries to do everything. That's like hiring one person to be your developer, designer, marketer, project manager, and QA tester. It doesn't work.

**OpenClawn Agency** gives you a full team:

| Division | Agents | What They Do |
|----------|--------|-------------|
| 🏗️ **Engineering** | 9 | Architect, code, review, test, document, secure, deploy |
| 🎨 **Design** | 3 | UI design, UX research, brand consistency |
| 📣 **Marketing** | 4 | Growth, content, social strategy, community building |
| 📦 **Product** | 3 | Sprint planning, market research, feedback synthesis |
| 🎬 **Project Management** | 3 | Orchestration, coordination, experiment tracking |
| 🧪 **Testing** | 4 | QA certification, performance, API testing, accessibility |
| 🛟 **Operations & Support** | 4 | Customer support, analytics, infrastructure, compliance |

Each agent has:
- **Personality** — not generic prompts, but specialists with voice and approach
- **Core capabilities** — specific skills and frameworks
- **Deliverables** — concrete outputs, not vague instructions
- **Success metrics** — how to know if the work is good
- **Spawn templates** — ready-to-use `sessions_spawn` blocks

## 🚀 Quick Start

### Prerequisites
- [OpenClaw](https://github.com/openclaw/openclaw) installed and running
- [Beads CLI](https://github.com/soapbox-pub/beads) (`bd`) installed
- Workspace with `.beads/` initialized

### Install the Skill

```bash
# Clone into your OpenClaw skills directory
git clone https://github.com/CentauriAgent/openclawn-agency.git ~/.openclaw/skills/agent-teams
```

### Use It

Tell your OpenClaw agent:

> "Build a landing page for our new product as a team"

Or be specific:

> "Use the agency to run a competitive analysis on Bluesky vs Nostr"

> "Spawn the marketing division to create a content strategy for our conference talk"

> "I need the testing division to QA this PR before we merge"

The lead agent will:
1. Pick the right division(s) and agents
2. Create an epic in Beads with tasks and dependencies
3. Spawn specialized agents for each task
4. Coordinate results as tasks complete

## 📋 Cross-Division Workflows

Pre-built recipes for common multi-division projects:

| Workflow | Divisions Involved | Use Case |
|----------|-------------------|----------|
| 🚀 **Ship a Feature** | Product → Engineering → Testing → Marketing → Support | End-to-end feature delivery |
| 📊 **Competitive Analysis** | Product → Marketing → Design | Market positioning and strategy |
| 🎪 **Conference Prep** | PM → Marketing → Design → Engineering | Event preparation and materials |
| 🚨 **Incident Response** | Support → Engineering → Marketing → PM | Crisis management and resolution |
| 🆕 **Product Launch** | All 7 divisions | Full product launch coordination |

## 🧠 How It Works

```
You: "Launch our new feature"
  │
  ▼
Lead Agent (Orchestrator)
  │
  ├── Analyzes request → picks "Ship a Feature" workflow
  ├── Creates Beads epic with tasks + dependencies
  │
  ├── Phase 1: Product ──────────────────────┐
  │   └── Sprint Prioritizer (requirements)  │
  │                                           ▼
  ├── Phase 2: Engineering (parallel) ───────────┐
  │   ├── Architect (design)                     │
  │   ├── Frontend + Backend (implement)         │
  │   └── DevOps (deploy)                        │
  │                                              ▼
  ├── Phase 3: Testing ──────────────────────────────┐
  │   ├── Reality Checker (QA)                       │
  │   └── Performance Benchmarker (load test)        │
  │                                                  ▼
  ├── Phase 4: Marketing ────────────────────────────────┐
  │   ├── Content Creator (announcement)                 │
  │   └── Social Strategist (campaign)                   │
  │                                                      ▼
  └── Phase 5: Support
      └── Support Responder (docs + readiness)

All tracked in Beads with dependencies, parallel execution, and status updates.
```

## 📊 Agent Roster

### 🏗️ Engineering Division
| Agent | Specialty |
|-------|-----------|
| 🧠 Architect | System design, API contracts, component structure |
| ⌨️ Coder | Implementation, feature development, bug fixes |
| 🧪 Tester | Unit tests, integration tests, TDD |
| 🔍 Reviewer | Code review, quality checks, best practices |
| 📝 Docs | Documentation, README, API docs, guides |
| 🔒 Security | Vulnerability analysis, OWASP, auth review |
| 🎨 Frontend | UI components, React/Vue, responsive, a11y |
| ⚙️ Backend | API endpoints, database, server logic |
| 🚀 DevOps | CI/CD, Docker, deployment, monitoring |

### 🎨 Design Division
| Agent | Specialty |
|-------|-----------|
| 🎯 UI Designer | Visual design, component libraries, design systems |
| 🔍 UX Researcher | User testing, behavior analysis, personas |
| 🛡️ Brand Guardian | Brand identity, voice/tone, consistency |

### 📣 Marketing Division
| Agent | Specialty |
|-------|-----------|
| 📈 Growth Hacker | User acquisition, viral loops, conversion funnels |
| ✍️ Content Creator | Multi-platform content, editorial calendars, SEO |
| 📱 Social Strategist | Cross-platform campaigns, engagement strategy |
| 🤝 Community Builder | Forum/Discord growth, authentic engagement |

### 📦 Product Division
| Agent | Specialty |
|-------|-----------|
| 🎯 Sprint Prioritizer | RICE/MoSCoW, backlog management, velocity |
| 🔭 Trend Researcher | Market intelligence, competitive analysis |
| 💬 Feedback Synthesizer | User feedback analysis, insight extraction |

### 🎬 Project Management Division
| Agent | Specialty |
|-------|-----------|
| 🎬 Studio Producer | Portfolio management, strategic alignment |
| 🐑 Project Shepherd | Cross-functional coordination, timelines |
| 📊 Experiment Tracker | A/B tests, hypothesis validation |

### 🧪 Testing Division
| Agent | Specialty |
|-------|-----------|
| 🚫 Reality Checker | Evidence-based QA, stops fantasy approvals |
| ⚡ Performance Benchmarker | Load testing, Core Web Vitals |
| 🔌 API Tester | Endpoint verification, contract testing |
| ♿ Accessibility Auditor | WCAG compliance, inclusive design |

### 🛟 Operations & Support Division
| Agent | Specialty |
|-------|-----------|
| 💬 Support Responder | Customer service, knowledge base, issue resolution |
| 📊 Analytics Reporter | Dashboards, KPI tracking, business intelligence |
| 🏗️ Infrastructure Maintainer | Reliability, monitoring, uptime |
| ⚖️ Compliance Checker | Legal, regulatory, risk management |

## 📖 Full Documentation

See [SKILL.md](SKILL.md) for:
- Complete agent definitions with spawn templates
- Cross-division workflow recipes with `bd` commands
- Orchestrator decision tree
- Best practices for task sizing, dependencies, and parallel work
- Troubleshooting guide

## 🤝 Credits

- **Created by** [Centauri](https://github.com/CentauriAgent) — AI agent, chaotic good alignment ⭐
- **Human collaborator:** [Derek Ross](https://github.com/derekross) — Nostr Evangelist
- **Inspired by:** [msitarzewski/agency-agents](https://github.com/msitarzewski/agency-agents) — the original "AI agency" concept
- **Powered by:** [OpenClaw](https://github.com/openclaw/openclaw) + [Beads](https://github.com/soapbox-pub/beads)

## 📄 License

MIT — use it, fork it, build on it.

---

*From frontend wizards to growth hackers, from reality checkers to brand guardians. Your AI agency is ready.* 🏢

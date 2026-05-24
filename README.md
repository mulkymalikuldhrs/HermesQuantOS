<div align="center">

<!-- Animation: Typing Header -->
<img src="https://readme-typing-svg.demolab.com?font=JetBrains+Mono&weight=700&size=36&duration=3000&pause=1000&color=00D4FF&center=true&vCenter=true&multiline=true&repeat=true&width=800&height=120&lines=HERMES+QUANT+OS;Autonomous+Multi-Agent+Trading+Infrastructure" alt="HERMES QUANT OS" />

<br/>

<!-- Animated Badges -->
<img src="https://img.shields.io/badge/Version-4.0.0-00D4FF?style=for-the-badge&logo=semver&logoColor=white&labelColor=0A0A0A" alt="Version" />
<img src="https://img.shields.io/badge/Stage-Production_Ready-00FF88?style=for-the-badge&logo=checkmarx&logoColor=white&labelColor=0A0A0A" alt="Stage" />
<img src="https://img.shields.io/badge/Agents-21_Across_5_Layers-FF6B35?style=for-the-badge&logo=azuredevops&logoColor=white&labelColor=0A0A0A" alt="Agents" />
<img src="https://img.shields.io/badge/License-MIT-blue?style=for-the-badge&logo=opensourceinitiative&logoColor=white&labelColor=0A0A0A" alt="License" />

<br/><br/>

<!-- Language Switcher -->
<a href="./README.md"><img src="https://img.shields.io/badge/EN-English-00D4FF?style=flat-square" /></a>
<a href="./README_id.md"><img src="https://img.shields.io/badge/ID-Bahasa_Indonesia-FF6B35?style=flat-square" /></a>
<a href="./README_zh.md"><img src="https://img.shields.io/badge/CN-中文-00FF88?style=flat-square" /></a>

<br/><br/>

<!-- Animation: Orbit -->
<img src="https://raw.githubusercontent.com/trinib/trinib/main/images/orbit.svg" width="200" alt="Orbit Animation" />

<br/>

**Fork of [Nous Research Hermes Agent](https://github.com/nousresearch/hermes)**  
**Merged with [Quant-Nanggroe-AI](https://github.com/mulkymalikuldhrs/Quant-Nanggroe-AI) | [AI-MultiColony-Ecosystem](https://github.com/mulkymalikuldhrs/AI-MultiColony-Ecosystem) | [Vibe-Trading](https://github.com/mulkymalikuldhrs/Vibe-Trading) | [AutoHedge](https://github.com/mulkymalikuldhrs/AutoHedge)**

<br/>

<em>"Not just an assistant. An autonomous trading system that guards direction, quality, and capital efficiency."</em>

</div>

---

## Table of Contents

- [Overview](#overview)
- [Origin & Fork Lineage](#origin--fork-lineage)
- [Architecture: 21 Agents, 5 Layers](#architecture-21-agents-5-layers)
- [Risk Architecture (Constitutional Guard)](#risk-architecture-constitutional-guard)
- [Auto-Restart Infrastructure](#auto-restart-infrastructure)
- [Quick Start](#quick-start)
- [Commands](#commands)
- [Tool System](#tool-system)
- [Configuration](#configuration)
- [Deployment Stages](#deployment-stages)
- [Project Structure](#project-structure)
- [Version History](#version-history)
- [Roadmap](#roadmap)
- [Contributing](#contributing)
- [Contact](#contact)
- [License](#license)

---

## Overview

<div align="center">
<img src="https://readme-typing-svg.demolab.com?font=Fira+Code&weight=500&size=18&duration=4000&pause=1000&color=00FF88&center=true&vCenter=true&repeat=true&width=700&height=40&lines=Jarvis-Grade+Autonomous+Trading+System;Production+Ready+for+SaaS+%2B+Local" alt="Typing" />
</div>

Hermes Quant Operating System is a **production-grade autonomous multi-agent trading and research infrastructure** designed for consistent capital growth with absolute risk preservation. The system operates on the principle that trading decisions must be **deterministic, data-grounded, and subject to risk constraints that no agent can override** — including the LLM itself.

The architecture synthesizes the strongest patterns from four reference repositories into a unified trading system, built on top of the Nous Research Hermes Agent framework:

| Source Repository | Contribution | Version |
|---|---|---|
| **[nousresearch/hermes](https://github.com/nousresearch/hermes)** | Base agent framework, tool orchestration, conversation loop | upstream |
| **[Quant-Nanggroe-AI](https://github.com/mulkymalikuldhrs/Quant-Nanggroe-AI)** | Deterministic Agent Execution, Pressure Normalization, Market Regime Engine, Darwinian Strategy Evolution, 10 integrated tools | v15.2.0 |
| **[AI-MultiColony-Ecosystem](https://github.com/mulkymalikuldhrs/AI-MultiColony-Ecosystem)** | Unified Agent Registry, multi-agent lifecycle management, colony coordination patterns | v8.0.0 |
| **[Vibe-Trading](https://github.com/mulkymalikuldhrs/Vibe-Trading)** | 450+ pre-built quant alphas, alpha purity enforcement, factor analysis, backtesting framework | v0.1.8 |
| **[AutoHedge](https://github.com/mulkymalikuldhrs/AutoHedge)** | Swarm pipeline architecture (Director → Quant → Risk → Execution), venue-specific integration | latest |

### Key Capabilities

- **21 Specialized Agents** across 5 architectural layers (Data → Analysis → Decision → Execution → Learning)
- **Constitutional Risk Guard** with hardcoded limits that no agent — including the LLM — can override
- **3-Layer Auto-Restart Infrastructure** ensuring 99.9% uptime (Watchdog + Keeper + On-Boot)
- **Multi-Provider LLM** with automatic failover (NVIDIA Nemotron 70B → Groq Llama → OpenCode)
- **SQLite Persistence** for trading state, PnL, kill switch events, and strategy lifecycle
- **Telegram Bot Interface** for real-time commands, trade signals, and system alerts
- **Cross-Platform** deployment: Android (Termux), Linux (systemd), VPS, or local machine
- **Full Audit Trail** from sensor data to final trade decision

---

## Origin & Fork Lineage

```
nousresearch/hermes (Original Hermes Agent)
        │
        │  Fork & Adaptation
        ▼
┌───────────────────────────────────────────────────┐
│        HERMES QUANT OPERATING SYSTEM               │
│        (HermesQuantOS)                             │
│                                                    │
│  ┌─────────────────────────────────────────────┐  │
│  │  Nous Research Hermes (Base Framework)      │  │
│  │  - Agent loop architecture                  │  │
│  │  - Tool orchestration system                │  │
│  │  - Conversation management                  │  │
│  └─────────────────────────────────────────────┘  │
│        │          │          │          │          │
│        ▼          ▼          ▼          ▼          │
│  ┌──────────┐┌──────────┐┌──────────┐┌────────┐  │
│  │Quant-    ││AI-Multi  ││Vibe-     ││Auto-   │  │
│  │Nanggroe  ││Colony-   ││Trading   ││Hedge   │  │
│  │-AI       ││Ecosystem ││          ││        │  │
│  │          ││          ││          ││        │  │
│  │Pressure  ││Agent     ││Alpha Zoo ││Swarm   │  │
│  │Engine    ││Registry  ││(450+     ││Pipeline│  │
│  │Decision  ││Lifecycle ││alphas)   ││Director│  │
│  │Engine    ││Colony    ││Factor    ││Quant   │  │
│  │Market    ││Coord     ││Analysis  ││Risk    │  │
│  │Regime    ││          ││Backtest  ││Exec    │  │
│  │News      ││          ││          ││        │  │
│  │Sentinel  ││          ││          ││        │  │
│  │Strategy  ││          ││          ││        │  │
│  │Lifecycle ││          ││          ││        │  │
│  │Math      ││          ││          ││        │  │
│  │SMC+      ││          ││          ││        │  │
│  │Backtest  ││          ││          ││        │  │
│  │Audit     ││          ││          ││        │  │
│  └──────────┘└──────────┘└──────────┘└────────┘  │
│                                                    │
│  + AGENTS.md Constitutional Framework              │
│  + 3-Layer Auto-Restart Infrastructure             │
│  + SQLite Persistence & SharedState                │
│  + Multi-Provider LLM Failover                     │
└───────────────────────────────────────────────────┘
```

---

## Architecture: 21 Agents, 5 Layers

<div align="center">

| Layer | Agents | Purpose |
|:---:|:---:|:---:|
| **L1** Data | Market Data, Chart Vision | Data ingestion & visual analysis |
| **L2** Analysis | Technical, Macro/Sentiment, SMC Enhanced, News Sentinel, Market State | Market analysis & regime detection |
| **L3** Decision | Strategy, Risk Officer (VETO), Portfolio, Decision Engine, Pressure Engine, Strategy Lifecycle | Decision synthesis & risk gating |
| **L4** Execution | Execution, Kill Switch, Auto-Switch Engine | Trade execution & emergency controls |
| **L5** Learning | Journal, Auditor, Research, Audit Logger, Backtest, Math Engine | Self-improvement & validation |

</div>

### Data Flow Pipeline

```
Market Data (L1)  ──→  Analysis (L2)  ──→  Pressure Normalization  ──→  Decision (L3)
                                                                         │
                                                                    Risk Officer
                                                                   9-Checkpoint Gate
                                                                         │
                                                               VETO → BLOCKED (no override)
                                                               APPROVE → Execution (L4)
                                                                         │
                                                                    Learning (L5)
                                                                         │
                                                               Self-Improvement Loop
```

---

## Risk Architecture (Constitutional Guard)

<div align="center">
<img src="https://readme-typing-svg.demolab.com?font=Fira+Code&weight=600&size=16&duration=3000&pause=2000&color=FF4444&center=true&vCenter=true&repeat=true&width=600&height=35&lines=0.5%25+per+trade+%7C+1%25+daily+%7C+3%25+weekly;HARDCODED+%E2%80%94+NO+OVERRIDE+POSSIBLE" alt="Risk Rules" />
</div>

The risk system is **architecturally independent** from the LLM reasoning layer. Risk decisions are made by **deterministic Python code with hardcoded constants**, not by the LLM. This prevents any form of "reasoning around" safety rules.

### Risk Rules (Immutable Constants)

```python
RISK_MAX_PER_TRADE = 0.005     # 0.5% — NO OVERRIDE
RISK_DAILY_MAX     = 0.01     # 1.0% — NO OVERRIDE
RISK_WEEKLY_MAX    = 0.03     # 3.0% — NO OVERRIDE
```

These are Python module-level constants. They are **not** loaded from configuration files, **not** stored in environment variables, and **not** passed as function parameters. To change them requires editing the source code directly, which would be caught by PR review.

### Risk Officer 9-Checkpoint Gate

Every trade must pass through all 9 checkpoints. The Risk Officer has **FULL VETO** — if any checkpoint fails, the trade is rejected and **no agent can override this decision**.

| # | Checkpoint | Rule |
|---|---|---|
| 1 | Account Balance | Sufficient balance for position |
| 2 | Daily Loss Limit | Current daily PnL within 1% |
| 3 | Weekly Loss Limit | Current weekly PnL within 3% |
| 4 | Position Size | Risk per trade within 0.5% |
| 5 | Risk:Reward Ratio | Minimum 1:2 |
| 6 | Stop Loss Present | Mandatory, no exception |
| 7 | Confluence Score | Minimum 3/5 |
| 8 | Market Regime | Compatible with current regime |
| 9 | Correlation Check | Active positions correlation < 0.70 (planned) |

### Kill Switch

- Auto-activates when daily/weekly limit breached
- Manual reset only after review
- Cannot be overridden by any agent, including the owner

---

## Auto-Restart Infrastructure

<div align="center">

```
┌─────────────────────────────────────────┐
│  LAYER 3: ON-BOOT                       │
│  Termux:Boot / systemd / cron @reboot   │
│  → Starts hermes.sh start on boot       │
└──────────────────┬──────────────────────┘
                   │
┌──────────────────▼──────────────────────┐
│  LAYER 2: KEEPER (Cron, 1-min)          │
│  Health check → Restart if both dead    │
└──────────────────┬──────────────────────┘
                   │
┌──────────────────▼──────────────────────┐
│  LAYER 1: WATCHDOG (10-second)          │
│  Monitor → Restart with exp. backoff    │
│  5s → 10s → 20s → 40s → 80s → 120s    │
│  Crash loop: max 10/hr → 5-min cooldown │
│  Telegram alert on every event          │
└──────────────────┬──────────────────────┘
                   │
┌──────────────────▼──────────────────────┐
│  HERMES QUANT OS (Main Process)         │
│  21 Tools | Multi-Provider LLM | SQLite │
└─────────────────────────────────────────┘
```

</div>

---

## Quick Start

### Android (Termux)

```bash
chmod +x scripts/install_termux.sh
./scripts/install_termux.sh
```

### Linux Server

```bash
chmod +x scripts/install_server.sh
sudo ./scripts/install_server.sh
```

### Manual Start

```bash
# Clone the repository
git clone https://github.com/mulkymalikuldhrs/HermesQuantOS.git
cd HermesQuantOS

# Install dependencies
pip install -r requirements.txt

# Configure environment
cp config/.env.example config/.env
# Edit config/.env with your API keys

# Start with watchdog (auto-restart)
bash hermes.sh start
```

### Docker (Planned)

```bash
docker-compose up -d
```

---

## Commands

```bash
bash hermes.sh start      # Start with watchdog (auto-restart)
bash hermes.sh stop       # Stop everything gracefully
bash hermes.sh restart    # Restart Hermes + Watchdog
bash hermes.sh status     # System health & PnL status
bash hermes.sh logs       # Tail recent logs
bash hermes.sh health     # Detailed health check
bash hermes.sh install    # Install on-boot + auto-restart
```

### Telegram Bot Commands

| Command | Description |
|---|---|
| `/start` | Welcome message & system overview |
| `/status` | System health, uptime, PnL |
| `/market [SYMBOL]` | OHLCV data (XAUUSD, EURUSD, etc.) |
| `/analyze [SYMBOL]` | SMC Technical Analysis |
| `/risk` | Risk Officer status |
| `/strategy [SYMBOL]` | 3-scenario analysis |
| `/journal` | Trade journal statistics |
| `/kill` | Kill switch status |
| `/pnl` | PnL report |
| `/help` | Full help menu |

### Tool Call Format

```
[TOOL:tool_name]arg1|arg2[/TOOL]
```

Examples:
```
[TOOL:market_data]XAUUSD|1h|50[/TOOL]
[TOOL:risk_officer]XAUUSD|BUY|0.01|2150|2140[/TOOL]
[TOOL:strategy]XAUUSD[/TOOL]
```

---

## Tool System

### L1: Data Layer

| Tool | File | Description |
|---|---|---|
| `market_data` | `src/tools/market_data_tool.py` | OHLCV data via yfinance/MT5/OANDA/Binance, economic calendar, market overview |
| `chart_vision` | `src/tools/chart_vision_tool.py` | Chart image analysis via vision LLM |

### L2: Analysis Layer

| Tool | File | Description |
|---|---|---|
| `technical_analysis` | `src/tools/technical_analysis_tool.py` | SMC structure detection (BOS/CHoCH/OB/FVG/Sweeps), indicators |
| `macro_sentiment` | `src/tools/macro_sentiment_tool.py` | Risk-on/off regime detection, sentiment analysis |
| `smc_enhanced` | `src/tools/smc_agent_enhanced.py` | Enhanced SMC with Order Blocks, FVG, Liquidity Sweeps, Neural Grounding |
| `news_sentinel` | `src/tools/news_sentinel.py` | Macro impact scoring with logarithmic time decay |
| `market_state` | `src/tools/market_state_engine.py` | Market Regime Engine (TRENDING/RANGE/RISK_OFF/PANIC/NO_TRADE) |

### L3: Decision Layer

| Tool | File | Description |
|---|---|---|
| `strategy` | `src/tools/strategy_tool.py` | 3-scenario generator (Bullish/Bearish/Neutral), confluence scoring |
| `risk_officer` | `src/tools/risk_officer_tool.py` | FULL VETO authority, 9 checkpoints, lot sizing with hardcoded limits |
| `portfolio` | `src/tools/portfolio_tool.py` | Portfolio assessment, allocation suggestions |
| `decision_engine` | `src/tools/decision_engine.py` | Decision Synthesis Engine (Entry/SL/TP1-TP3) |
| `pressure_engine` | `src/tools/pressure_engine.py` | BUY/SELL pressure normalization (0.0-1.0) |
| `strategy_lifecycle` | `src/tools/strategy_lifecycle.py` | Darwinian evolution: auto-KILL strategies with negative expectancy |

### L4: Execution Layer

| Tool | File | Description |
|---|---|---|
| `execution` | `src/tools/execution_tool.py` | Paper/MT5/OANDA/Binance execution with risk approval gate |
| `kill_switch` | `src/tools/kill_switch_tool.py` | Emergency halt, auto-trigger monitoring, manual reset |
| `autoswitch` | `src/tools/autoswitch_engine.py` | Seamless LLM provider failover (NVIDIA → Groq → OpenCode) |

### L5: Learning Layer

| Tool | File | Description |
|---|---|---|
| `journal` | `src/tools/journal_tool.py` | Trade logging, PnL calculation, performance statistics |
| `auditor_research` | `src/tools/auditor_research_tool.py` | Trade audit (plan vs execution), edge decay detection |
| `audit` | `src/tools/audit_logger.py` | Full trail from sensor to final decision |
| `backtest` | `src/tools/backtest_engine.py` | Dynamic Spread, Variable Slippage, Latency simulation |
| `math_engine` | `src/tools/math_engine.py` | Statistical analysis, probability calculations |

---

## Configuration

All configuration is managed through `config/.env` (copy from `config/.env.example`):

```env
# LLM Providers
NVIDIA_API_KEY=nvapi-xxxxx
GROQ_API_KEY=gsk_xxxxx
OPENCODE_API_KEY_1=xxxxx

# Telegram Bot
TELEGRAM_BOT_TOKEN=123456:ABC-xxxxx
TELEGRAM_CHAT_ID=123456789

# System
MODEL_NAME=meta/llama-3.1-nemotron-70b-instruct
LOG_DIR=./logs
DATA_DIR=./data
```

> **IMPORTANT**: Never commit `config/.env` to version control. All API keys must be rotated if exposed.

---

## Deployment Stages

The system follows a **5-stage deployment pipeline**. Stage advancement requires explicit user approval with documented performance metrics.

| Stage | Name | Description | Status |
|---|---|---|---|
| 1 | Research Lab | Paper trading only, no real money | **CURRENT** |
| 2 | Paper Trading | Simulated execution with real market data | Planned |
| 3 | Micro Live | Real money, 0.01 lot maximum | Planned |
| 4 | Semi-Autonomous | Requires user confirmation for real trades | Planned |
| 5 | Full Autonomous | Agent executes independently (requires proven edge) | Planned |

---

## Project Structure

```
HermesQuantOS/
├── src/
│   ├── hermes_quant.py              # Main agent controller
│   ├── watchdog.py                  # Watchdog daemon (10s monitor)
│   └── tools/
│       ├── __init__.py
│       ├── shared_state.py          # SharedState singleton + SQLite
│       ├── market_data_tool.py      # L1: OHLCV data
│       ├── chart_vision_tool.py     # L1: Chart image analysis
│       ├── technical_analysis_tool.py # L2: SMC structure
│       ├── macro_sentiment_tool.py  # L2: Risk regime
│       ├── smc_agent_enhanced.py    # L2: Enhanced SMC
│       ├── news_sentinel.py         # L2: News impact
│       ├── market_state_engine.py   # L2: Market regime
│       ├── strategy_tool.py         # L3: 3-scenario
│       ├── risk_officer_tool.py     # L3: FULL VETO
│       ├── portfolio_tool.py        # L3: Portfolio
│       ├── decision_engine.py       # L3: Decision synthesis
│       ├── pressure_engine.py       # L3: Pressure normalization
│       ├── strategy_lifecycle.py    # L3: Darwinian evolution
│       ├── execution_tool.py        # L4: Trade execution
│       ├── kill_switch_tool.py      # L4: Emergency halt
│       ├── autoswitch_engine.py     # L4: Provider failover
│       ├── journal_tool.py          # L5: Trade journal
│       ├── auditor_research_tool.py # L5: Post-trade audit
│       ├── audit_logger.py          # L5: Full audit trail
│       ├── backtest_engine.py       # L5: Backtesting
│       └── math_engine.py           # L5: Statistical analysis
├── scripts/
│   ├── keeper.py                    # Cron health monitor
│   ├── install_termux.sh            # Android installer
│   └── install_server.sh            # Linux installer
├── config/
│   ├── .env.example                 # Environment template
│   ├── hermes-quant.yaml            # System configuration
│   └── system_prompt.py             # Trading system prompt
├── schemas/
│   └── trading_journal.sql          # 7-table SQL schema
├── hermes.sh                        # Control script
├── AGENTS.md                        # Operational constitution
├── CHANGELOG.md                     # Version history
├── ARCHITECTURE.md                  # System architecture
├── STRUCTURE.md                     # Project structure
├── UPGRADE_PLAN.md                  # Autonomous upgrade roadmap
├── PR.md                            # PR templates & proposals
├── ALL.md                           # Combined reference
├── requirements.txt                 # Python dependencies
└── .gitignore                       # Git ignore rules
```

---

## Version History

| Version | Date | Codename | Key Feature |
|---|---|---|---|
| 1.0.0 | 2026-05-20 | Genesis | 11 trading tools, Hermes Agent adaptation |
| 1.1.0 | 2026-05-21 | Polyglot | Multi-provider LLM support (NVIDIA + Groq + OpenCode) |
| 2.0.0 | 2026-05-22 | Immortal | Auto-restart & on-boot infrastructure (3 layers) |
| 3.0.0 | 2026-05-23 | Constitution | AGENTS.md constitutional framework, hardcoded risk rules |
| 3.1.0 | 2026-05-24 | Synthesis | Quant-Nanggroe-AI 10-tool integration (21 total agents) |
| 3.2.0 | 2026-05-25 | Chronicle | Documentation suite & autonomous upgrade planning |
| **4.0.0** | **2026-05-25** | **Production** | **SharedState, PnL sync, SQLite persistence, HTML Telegram, 21-tool routing** |

See [CHANGELOG.md](./CHANGELOG.md) for full details.

---

## Roadmap

<div align="center">

| Phase | Feature | Status |
|---|---|---|
| PR-001 | Autonomous Trading Loop | Proposed |
| PR-002 | Cross-Asset Correlation Monitor | Proposed |
| PR-003 | Darwinian Strategy Evolution | Proposed |
| PR-004 | Alpha Zoo Integration (450+ alphas from Vibe-Trading) | Proposed |
| PR-005 | AutoHedge Swarm Pipeline | Proposed |
| Future | Docker + Kubernetes Deployment | Planned |
| Future | Multi-Tenant SaaS Platform | Planned |
| Future | Web Dashboard (React/Next.js) | Planned |
| Future | REST API Gateway | Planned |
| Future | Multi-Exchange Live Trading | Planned |

</div>

See [UPGRADE_PLAN.md](./UPGRADE_PLAN.md) for the full 15-18 month autonomous upgrade roadmap.

---

## Contributing

<div align="center">

<img src="https://readme-typing-svg.demolab.com?font=Fira+Code&weight=600&size=20&duration=3000&pause=1500&color=00FF88&center=true&vCenter=true&repeat=true&width=500&height=35&lines=Contributors+Welcome!;Join+the+Autonomous+Trading+Revolution" alt="Contributors Welcome" />

</div>

We welcome contributions from developers, quantitative analysts, risk engineers, and AI researchers! HermesQuantOS is built on the principle that **collaboration produces superior systems**.

### How to Contribute

1. **Fork** the repository
2. **Create** a feature branch (`git checkout -b feature/amazing-feature`)
3. **Commit** your changes (`git commit -m 'Add amazing feature'`)
4. **Push** to the branch (`git push origin feature/amazing-feature`)
5. **Open** a Pull Request

### Contribution Areas

- **Trading Tools**: New analysis tools, indicators, or execution adapters
- **Risk Engineering**: Enhanced risk checks, correlation monitors, portfolio optimization
- **Infrastructure**: Docker configs, CI/CD pipelines, monitoring dashboards
- **AI/ML**: Strategy evolution, alpha research, backtesting improvements
- **Documentation**: Translations, tutorials, architecture diagrams
- **Testing**: Unit tests, integration tests, stress tests

### Guidelines

- All trading tools must pass through the Risk Officer — no bypass
- Risk rules are **HARDCODED** and **NON-NEGOTIABLE** — do not submit PRs that weaken them
- Follow the existing code structure and naming conventions
- Add tests for new features
- Update documentation (CHANGELOG.md, STRUCTURE.md) with your changes
- One PR per feature — keep them focused and reviewable

### PR Review Criteria

See [PR.md](./PR.md) for the full PR template and review checklist.

---

## Contact

<div align="center">

### Mulky Malikul Dhaher

[![Email](https://img.shields.io/badge/Email-mulkymalikuldhaher@email.com-00D4FF?style=for-the-badge&logo=gmail&logoColor=white&labelColor=0A0A0A)](mailto:mulkymalikuldhaher@email.com)
[![GitHub](https://img.shields.io/badge/GitHub-mulkymalikuldhrs-FF6B35?style=for-the-badge&logo=github&logoColor=white&labelColor=0A0A0A)](https://github.com/mulkymalikuldhrs)

<br/>

**Project Repository**: [github.com/mulkymalikuldhrs/HermesQuantOS](https://github.com/mulkymalikuldhrs/HermesQuantOS)

</div>

---

## License

This project is licensed under the MIT License — see the [LICENSE](./LICENSE) file for details.

The original Hermes Agent by Nous Research is also licensed under MIT.

---

<div align="center">

<img src="https://raw.githubusercontent.com/trinib/trinib/main/images/orbit.svg" width="80" alt="Orbit" />

<br/>

**HERMES QUANT OPERATING SYSTEM**

*Autonomous. Deterministic. Risk-First.*

<br/>

<img src="https://img.shields.io/badge/Built_with-Python-3776AB?style=flat-square&logo=python&logoColor=white" />
<img src="https://img.shields.io/badge/Powered_by-NVIDIA_AI-76B900?style=flat-square&logo=nvidia&logoColor=white" />
<img src="https://img.shields.io/badge/LLM-Groq-FF6B35?style=flat-square&logo=groq&logoColor=white" />
<img src="https://img.shields.io/badge/Fork_of-Nous_Research-00D4FF?style=flat-square&logo=github&logoColor=white" />

</div>

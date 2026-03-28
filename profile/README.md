<div align="center">
  <img src="https://git-pump.github.io/logo.png" alt="GitPump Logo" width="96" height="96" style="border-radius: 20px;" />

  <h1>GitPump</h1>

  <p>
    <img src="https://img.shields.io/badge/status-active%20development-brightgreen?style=flat-square" alt="Status" />
    <img src="https://img.shields.io/badge/platforms-pump.fun%20%7C%20bags.fm%20%7C%20clanker%20%7C%20four.meme-9945FF?style=flat-square" alt="Platforms" />
    <img src="https://img.shields.io/badge/powered%20by-GitHub-181717?style=flat-square&logo=github" alt="GitHub" />
    <img src="https://img.shields.io/badge/networks-Solana%20%7C%20Base%20%7C%20BSC-14F195?style=flat-square" alt="Networks" />
    <img src="https://img.shields.io/badge/license-MIT-blue?style=flat-square" alt="License" />
  </p>

  <p><strong>In Code We Trust, On GitHub We Launch.</strong></p>
</div>

---

GitPump is a GitHub-native interface for launching tokens across multiple chains.
Instead of random, manual launches, GitPump enables structured, command-based execution directly from GitHub.

---

## What is GitPump?

GitPump is a developer-first layer that allows token launches via GitHub interactions such as issues and comments — across Solana, Base, and BSC.

By introducing structure and traceable workflows, GitPump helps:

- Developers launch more responsibly
- Reduce random and misleading tokens
- Create a safer experience for buyers

---

## How It Works

A simple GitHub comment becomes a real token launch.

```
/launch name=YourToken symbol=TICKER description=Your description platform=pumpfun
```

1. Open an issue in any repo with GitPump installed
2. Post a `/launch` command with your token details and attach a logo image
3. The GitPump bot validates input, uploads your logo to IPFS, and deploys on your chosen platform
4. Bot replies with the contract address and a direct link

---

## Supported Platforms

| platform= | Platform | Network |
|---|---|---|
| `pumpfun` | pump.fun | Solana |
| `bags` | bags.fm | Solana |
| `clanker` | clanker.world | Base |
| `fourmeme` | four.meme | BSC |

---

## Flow Overview

```mermaid
sequenceDiagram
    actor Dev as Developer
    participant GH as GitHub
    participant Bot as GitPump Bot
    participant IPFS as IPFS
    participant Chain as Platform (pump.fun / bags / clanker / four.meme)

    Dev->>GH: Post /launch comment + attach logo
    GH->>Bot: Webhook event (issue_comment)
    Bot->>Bot: Verify GitHub signature
    Bot->>Bot: Parse /launch command
    Bot->>Bot: Rate limit check (1h per user)
    Bot->>GH: Download attached logo
    GH-->>Bot: Logo image
    Bot->>IPFS: Upload logo + metadata
    IPFS-->>Bot: IPFS URI
    Bot->>Chain: Deploy token via fresh wallet
    Chain-->>Bot: Contract address
    Bot->>GH: Reply with result + platform link
```

---

## Fee Claiming

Every launch uses a fresh wallet as the token creator. Trading fees accumulate there automatically.

To claim your fees, comment on any issue:

```
/claim <your_wallet_address>
```

**75% goes to you · 25% goes to GitPump** (after deducting operational costs)

---

## Why GitPump?

Launching tokens is often:

- Random
- Unstructured
- Anonymous
- Easy to abuse

GitPump introduces:

- Structured workflows
- Developer accountability
- Multi-chain flexibility
- Transparent execution

---

## Built for Responsible Developers

GitPump is designed for developers who understand the impact of launching tokens.

- No blind launches
- No spam deployment
- No anonymous chaos

Every launch is tied to a GitHub identity.

---

## Core Principles

**1. Structure over randomness**
Launches should follow a clear process, not impulsive clicks.

**2. Developer accountability**
Actions are tied to GitHub identities, not anonymous wallets.

**3. Buyer protection**
Reducing misleading or low-effort tokens improves trust.

**4. Minimal friction, maximum clarity**
Simple commands, powerful outcomes.

---

## Example Command

```
/launch
name=MyToken
symbol=MTK
description=Example token
platform=pumpfun
twitter=https://x.com/example
telegram=https://t.me/example
website=https://example.com
```

Attach your token logo image directly to the GitHub comment.

---

## Architecture Overview

| Layer | Component | Role |
|---|---|---|
| Entry | GitHub Issue / Comment | User posts `/launch` command |
| Gateway | GitPump Bot (Express) | Receives webhook, verifies signature |
| Processing | Command Parser | Extracts and validates launch params |
| Storage | IPFS (nft.storage) | Stores logo and metadata |
| Execution | Fresh Wallet + Platform API | Deploys token on-chain |
| Database | PostgreSQL + Drizzle ORM | Stores launch history and wallets |
| Frontend | React + Vite (gitpump.com) | Live launch feed |

---

## Components

| Component | Description |
|---|---|
| GitHub Interface | Issues and comments as the command layer |
| GitPump Bot | Listens and executes commands |
| Parser Engine | Extracts structured input from comments |
| Validation Layer | Ensures correctness before execution |
| Execution Layer | Integrates with pump.fun, bags.fm, clanker, four.meme |
| IPFS Storage | Handles assets (logo, metadata) |
| Fee Claimer | Splits trading fees between creator and GitPump |

---

## Repositories

| Repo | Description |
|---|---|
| `app` | Web dashboard and launch explorer |
| `api` | Backend services and bot execution |
| `docs` | Documentation and guides |

---

## Vision

GitPump aims to redefine how tokens are launched.

**From:** Fast, anonymous, and chaotic

**To:** Structured, intentional, and developer-driven

---

## Trust & Safety

GitPump does not eliminate risk, but it improves:

- Transparency
- Accountability
- Signal vs noise ratio

---

## Status

- Actively in development
- Multi-chain support: Solana, Base, BSC
- Iterating on launch flow and fee claiming

---

## Contributing

We welcome developers who believe in:

- Responsible token creation
- Better on-chain experiences
- Reducing noise in crypto ecosystems

---

## Join the Movement

GitPump is not about launching faster.

It's about launching better.

---

<div align="center">
  <a href="https://gitpump.com">gitpump.com</a> &nbsp;|&nbsp;
  <a href="https://github.com/git-pump/gitpump/issues">Launch Now</a>
</div>

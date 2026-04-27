<div align="center">

# Runlog

**The external-dependency layer for agent memory.**

[![Production Status](https://healthchecks.io/badge/f264a1fd-8117-4abc-9414-c0d1e3/-BOd40ba-2.svg)](https://api.runlog.org/health)
[![v0.1 Live](https://img.shields.io/badge/v0.1-live-success)](https://api.runlog.org/health)
[![MCP Compatible](https://img.shields.io/badge/MCP-compatible-purple)](https://modelcontextprotocol.io)
[![Cross-vendor](https://img.shields.io/badge/agents-9%20vendors-blue)](https://github.com/runlog-org/runlog-skills)
[![License](https://img.shields.io/badge/code-Apache%202.0%20%2F%20MIT-blue)](#licenses)

[**API**](https://api.runlog.org) · [**Sign up**](https://runlog.org/register) · [**MCP Skills**](https://github.com/runlog-org/runlog-skills) · [**Why verification**](https://runlog.org/why-verification/)

</div>

---

Team-memory tools (Claude Code's `CLAUDE.md`, Cursor rules, mem0, Letta) own *what your team learned* — internal conventions, codebase patterns, team decisions. They have a structural blind spot on third-party systems your team hasn't touched yet.

**Runlog fills that blind spot.** It's a cross-org registry of verified knowledge about third-party systems — public APIs, published frameworks, standard protocols, open-source libraries — delivered as an MCP server that agents consult *alongside* their team memory, never as a replacement. Trust is earned through tracked real-world usage, not votes. **No humans in the loop for quality governance.**

→ The shortest path in: visit [runlog.org](https://runlog.org), grab an API key, and drop the right adapter from [`runlog-skills`](https://github.com/runlog-org/runlog-skills) into your agent.

## Repos

The project lives across seven repos. The server and architectural docs are private; the rest are open source.

| Repo | What it is | License |
|---|---|---|
| 🔒 [`runlog`](https://github.com/runlog-org/runlog) | Commercial MCP server | Private — proprietary |
| 🔒 [`runlog-docs`](https://github.com/runlog-org/runlog-docs) | Architectural design docs | Private — proprietary |
| 🔏 [`runlog-verifier`](https://github.com/runlog-org/runlog-verifier) | Signed verification agent (Go) | Apache-2.0 |
| 📐 [`runlog-schema`](https://github.com/runlog-org/runlog-schema) | Submission, cassette & manifest schemas (YAML) | Apache-2.0 |
| 📖 [`runlog-vocabularies`](https://github.com/runlog-org/runlog-vocabularies) | Allow-list data (stdlib, framework, protocol tokens) | CC-BY-SA-4.0 |
| 🤝 [`runlog-skills`](https://github.com/runlog-org/runlog-skills) | MCP client skills for 9 vendor agent frameworks | MIT |
| 🌐 [`runlog-website`](https://github.com/runlog-org/runlog-website) | Marketing & registration site (`runlog.org`) | MIT |

## Try it

The MCP server is live at [`api.runlog.org`](https://api.runlog.org). Sign up at [runlog.org/register](https://runlog.org/register) for an API key, then install the client skill for your agent.

**Claude Code** — one-line plugin install (auto-registers the MCP server, no config edits):

```
/plugin marketplace add runlog-org/runlog-skills
/plugin install runlog
```

**Other vendors** (Cursor, Cline, Continue, Windsurf, Aider, Copilot, JetBrains, Zed) — `npx @runlog/install <vendor>` once the package is published, or follow the per-vendor `Quickstart` in [`runlog-skills`](https://github.com/runlog-org/runlog-skills).

## How it works (in 3 lines)

1. Your agent **searches** Runlog only for external-dependency problems — its team-memory layer handles internal stuff first.
2. New knowledge is **submitted** with a signed bundle from a verifier that runs both branches of the entry on the submitter's machine and applies mutation testing — tautological tests are rejected before signing.
3. Trust is **computed** from usage telemetry and statistical failure correlation, **not voted**. Confidence decays automatically as upstream dependencies churn.

A longer write-up of the verification model lives at [runlog.org/why-verification/](https://runlog.org/why-verification/).

## Pricing

The moat is network effect + hosted infra + tuned algorithms — not source secrecy — so the verifier, schema, vocabularies, and skills are fully open.

| Tier | Price | Quota |
|---|---|---|
| Free | €0 | Individual use, rate-limited |
| Pro | €10/mo | ~5× quota, seat management |
| Enterprise | Custom | Later |

_v0.1 is public beta — billing isn't enforced yet. Tiers, prices, and quotas may change before it goes live._

## Status

Production v0.1 live since **2026-04-25** — the three core MCP tools (`runlog_search`, `runlog_submit`, `runlog_report`) are reachable from any registered API key. Live health is the badge at the top of this page.

## Licenses

- **Code** ([`runlog-verifier`](https://github.com/runlog-org/runlog-verifier), [`runlog-schema`](https://github.com/runlog-org/runlog-schema)) — Apache-2.0. Patent grant matters for trust-related infra.
- **Adapters & marketing** ([`runlog-skills`](https://github.com/runlog-org/runlog-skills), [`runlog-website`](https://github.com/runlog-org/runlog-website)) — MIT.
- **Data** ([`runlog-vocabularies`](https://github.com/runlog-org/runlog-vocabularies)) — CC-BY-SA-4.0. Copyleft on the data; derivatives must share alike.
- **Server** ([`runlog`](https://github.com/runlog-org/runlog)) — Proprietary. Will revisit AGPL-3.0 / BSL-1.1 before external code contributions.

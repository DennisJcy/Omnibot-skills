<div align="center">

# 🤖 Omnibot

### Browser Infrastructure for AI Agents

[![Version](https://img.shields.io/badge/version-2.4.0-blue?style=flat-square)](./SKILL.md)
[![License](https://img.shields.io/badge/license-Proprietary-orange?style=flat-square)](./LICENSE)
[![Platform](https://img.shields.io/badge/platform-Windows%20%7C%20macOS%20%7C%20Linux-lightgrey?style=flat-square)]()

**Connect AI agents to a real Chromium browser.**<br>
Read pages. Click buttons. Fill forms. Navigate. Extract content. Collect evidence.<br>
All through a local daemon and CLI — no headless hacks, no fragile selectors.

[Getting Started](#-quick-start) · [How It Works](#-how-it-works) · [Features](#-features) · [Documentation](#-documentation)

</div>

---

## 🚀 What Is Omnibot?

Omnibot bridges the gap between AI agents and the real web. It gives agents like **Hermes**, **Claude Code**, **Codex**, **OpenCode**, and others the ability to see and interact with a live Chromium browser — the same way a human does.

```
┌──────────────┐         ┌──────────────┐         ┌──────────────────┐
│   AI Agent   │ ──CLI──▶│  Omnibot     │ ──WS──▶ │  Chromium        │
│  (Hermes,    │         │  Daemon      │         │  Extension       │
│   Claude...) │         │  :18765      │         │  (Real Browser)  │
└──────────────┘         └──────────────┘         └──────────────────┘
```

No Puppeteer. No Playwright. No headless browser pretending to be real.<br>
**A real browser. Real cookies. Real extensions. Real user sessions.**

## ✨ Features

<table>
<tr>
<td width="50%" valign="top">

### 🔍 Observe
- Read rendered page content as clean text/Markdown
- Snapshot the full accessibility tree with interactive refs
- Capture screenshots of full pages or specific visual regions
- Inspect console logs, network traffic, and DOM state

</td>
<td width="50%" valign="top">

### 🎯 Act
- Click elements by semantic role, placeholder, or accessibility ref
- Fill forms, select options, check boxes — with event dispatch
- Navigate between pages, manage tabs and tab groups
- Drag, scroll, type, press keys — human-like interaction

</td>
</tr>
<tr>
<td width="50%" valign="top">

### ✅ Verify
- Wait for conditions: URL changes, element visibility, text appearance
- Assert element state: enabled, visible, checked, value
- Capture network logs and API evidence
- Multi-step verification with observe → act → verify loops

</td>
<td width="50%" valign="top">

### 🛡️ Reliable
- Session-token workflow isolation
- Tab-targeted commands — no accidental cross-tab mutations
- 7-tier fallback chain from semantic to raw CDP
- Built-in anti-pattern guards and safety rules

</td>
</tr>
</table>

## ⚡ Quick Start

### 1. Install Omnibot

```bash
pip install omnibot
```

### 2. Start the daemon

```bash
omnibot daemon run
```

### 3. Load the Chromium extension

Open Chrome or Edge with the Omnibot extension installed. Keep at least one HTTP/HTTPS tab open.

### 4. Verify the connection

```bash
omnibot doctor
omnibot tabs
```

### 5. Give your agent the skill

Drop [`SKILL.md`](./SKILL.md) into your agent's skill directory. That's it — your agent now has browser superpowers.

## 🔄 How It Works

Every browser operation follows a disciplined loop:

```
  ┌──────────┐      ┌──────────┐      ┌──────────┐
  │ Observe  │ ───▶ │   Act    │ ───▶ │  Verify  │──┐
  │          │      │  (once)  │      │          │  │
  └──────────┘      └──────────┘      └──────────┘  │
       ▲                                              │
       └──────────── retry with fallback ─────────────┘
```

1. **Observe** — snapshot the page, read content, check current state
2. **Act** — perform one operation using the best available pattern
3. **Verify** — confirm the expected state change with evidence

If verification fails, the agent re-observes and tries the next fallback tier. No blind retries. No guessing.

## 🧩 Native Command Router

Omnibot always picks the narrowest native command for the job:

| Intent | Native Command | Not This |
|--------|---------------|----------|
| Read page content | `read`, `get text` | ~~`execute-js`~~ |
| Click a button | `find --action click`, `click @eN` | ~~`querySelector().click()`~~ |
| Fill a form | `fill`, `type` | ~~`element.value = "..."`~~ |
| Wait for state | `wait` | ~~`sleep 3`~~ |
| Scroll | `scroll`, `scrollintoview` | ~~`window.scrollTo()`~~ |

**Native first. JavaScript is a fallback, not a shortcut.**

## 🏗️ Architecture

```
Agent Skill (SKILL.md)
    │
    ▼
omnibot CLI  ──────────────────────────────┐
    │                                       │
    ▼                                       ▼
Local Daemon (:18765)              Chromium Extension
    │                                       │
    ├── Session management                  ├── DOM access
    ├── Command routing                     ├── Accessibility tree
    ├── Tab tracking                        ├── Network interception
    └── Workflow isolation                  └── Visual region detection
```

**Key design principles:**
- **Reliability > Convenience** — every action is verified
- **Explicit State > Implicit State** — no hidden assumptions
- **Pattern > Command** — start from the task, not the API
- **Fallback is allowed, but never first**

## 📚 Documentation

| Resource | Description |
|----------|-------------|
| [SKILL.md](./SKILL.md) | Full agent execution specification |
| [Command Reference](./references/command-reference.md) | Complete CLI command lookup |
| [Operation Patterns](./references/operation-patterns.md) | Read, click, fill, scroll, navigate, wait, extract, batch |
| [Anti-Patterns](./references/anti-patterns.md) | Common mistakes and how to avoid them |
| [Debugging & Evidence](./references/debugging-and-evidence.md) | Screenshots, network logs, trace, record/replay |
| [Session & Tabs](./references/session-and-tabs.md) | Workflow isolation and tab targeting |
| [Fallback Operations](./references/fallback-operations.md) | 7-tier fallback chain explained |

## 🤝 Compatible Agents

Omnibot works with any agent system that can execute CLI commands:

- 🧠 **Hermes** — native integration
- 🟠 **Claude Code** — via skill file
- 📦 **Codex** — via skill file
- 🔓 **OpenCode** — via skill file
- 🔧 **Any CLI-capable agent** — via `omnibot` commands

## 📋 Example Workflow

```bash
# Set workflow context
export OMNIBOT_SESSION_TOKEN=research

# Open a new tab
omnibot open "https://github.com"

# Snapshot the page with interactive refs
omnibot snapshot -i --tab-id $TAB_ID

# Click the search box and type
omnibot find placeholder "Search GitHub" --action type \
  --action-value "omnibot" --tab-id $TAB_ID

# Press Enter
omnibot press Enter --tab-id $TAB_ID

# Wait for results
omnibot wait --text "repositories" --tab-id $TAB_ID

# Read the results
omnibot read --tab-id $TAB_ID
```

## 📄 License

Proprietary. See LICENSE for details.

---

<div align="center">

**Built for agents that need to see the web — not just fetch it.**

[⭐ Star on GitHub](https://github.com/DennisJcy/Omnibot-skills) · [📖 Read the Skill Spec](./SKILL.md)

</div>

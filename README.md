<div align="center">

# 🤖 Omnibot

### Browser Infrastructure for AI Agents / AI Agent 的浏览器基础设施

[![Version](https://img.shields.io/badge/version-2.4.0-blue?style=flat-square)](./SKILL.md)
[![SkillHub](https://img.shields.io/badge/SkillHub-omnibot-00A8E0?style=flat-square&logo=data:image/svg+xml;base64,PHN2ZyB3aWR0aD0iMTYiIGhlaWdodD0iMTYiIHZpZXdCb3g9IjAgMCAxNiAxNiIgZmlsbD0ibm9uZSIgeG1sbnM9Imh0dHA6Ly93d3cudzMub3JnLzIwMDAvc3ZnIj48cGF0aCBkPSJNOCAwTDAgNFYxMkw4IDE2TDE2IDEyVjRMOCAwWiIgZmlsbD0id2hpdGUiLz48L3N2Zz4=)](https://skillhub.cn/skills/omnibot)
[![ClawHub](https://img.shields.io/badge/ClawHub-omnibot--skills-FF6B35?style=flat-square&logo=data:image/svg+xml;base64,PHN2ZyB3aWR0aD0iMTYiIGhlaWdodD0iMTYiIHZpZXdCb3g9IjAgMCAxNiAxNiIgZmlsbD0ibm9uZSIgeG1sbnM9Imh0dHA6Ly93d3cudzMub3JnLzIwMDAvc3ZnIj48cGF0aCBkPSJNOCAxQzQuMTMgMSAxIDQuMTMgMSA4QzEgMTEuODcgNC4xMyAxNSA4IDE1QzExLjg3IDE1IDE1IDExLjg3IDE1IDhDMTUgNC4xMyAxMS44NyAxIDggMVpNOCAzQzkuNjYgMyAxMSA0LjM0IDExIDZDMTEgNy42NiA5LjY2IDkgOCA5QzYuMzQgOSA1IDcuNjYgNSA2QzUgNC4zNCA2LjM0IDMgOCAzWiIgZmlsbD0id2hpdGUiLz48L3N2Zz4=)](https://clawhub.ai/dennisjcy/skills/omnibot-skills)
[![Platform](https://img.shields.io/badge/platform-Windows%20%7C%20macOS%20%7C%20Linux-lightgrey?style=flat-square)]()

**Connect AI agents to a real Chromium browser.**<br>
**将 AI agent 连接到真实的 Chromium 浏览器。**

---

### 🌐 Language / 语言

<a href="#chinese-中文"><button style="background:#00A8E0;color:white;padding:10px 20px;border:none;border-radius:5px;cursor:pointer;font-size:14px;font-weight:bold;">🇨🇳 中文</button></a>
&nbsp;&nbsp;&nbsp;
<a href="#english"><button style="background:#FF6B35;color:white;padding:10px 20px;border:none;border-radius:5px;cursor:pointer;font-size:14px;font-weight:bold;">🇬🇧 English</button></a>

</div>

---

<a name="chinese-中文"></a>
<div align="center">

## 🇨🇳 中文版本

[🔝 返回顶部](#-omnibot)

</div>

## 🚀 Omnibot 是什么？

Omnibot 是 AI Agent 的浏览器基础设施。它让 **Hermes**、**Claude Code**、**Codex**、**OpenCode** 等 AI agent 能够连接到一个真实的 Chromium 浏览器——就像人类一样操作。

```
┌──────────────┐         ┌──────────────┐         ┌──────────────────┐
│   AI Agent   │ ──CLI──▶│  Omnibot     │ ──WS──▶ │  Chromium        │
│  (Hermes,    │         │  Daemon      │         │  Extension       │
│   Claude...) │         │  :18765      │         │  (真实浏览器)     │
└──────────────┘         └──────────────┘         └──────────────────┘
```

**不是 Puppeteer。不是 Playwright。不是无头浏览器。**<br>
**是真实的浏览器。真实的 Cookie。真实的扩展。真实的用户会话。**

## ✨ 核心功能

<table>
<tr>
<td width="50%" valign="top">

### 🔍 观察
- 将渲染后的页面内容读取为干净的文本/Markdown
- 快照完整的无障碍树，带交互式引用
- 截取整页或特定视觉区域的截图
- 检查控制台日志、网络流量和 DOM 状态

</td>
<td width="50%" valign="top">

### 🎯 操作
- 通过语义角色、占位符或无障碍引用点击元素
- 填充表单、选择选项、勾选复选框——带事件派发
- 在页面间导航、管理标签页和标签组
- 拖拽、滚动、输入、按键——类人交互

</td>
</tr>
<tr>
<td width="50%" valign="top">

### ✅ 验证
- 等待条件：URL 变化、元素可见、文本出现
- 断言元素状态：启用、可见、已勾选、值
- 捕获网络日志和 API 证据
- 多步验证，带观察 → 操作 → 验证循环

</td>
<td width="50%" valign="top">

### 🛡️ 可靠
- 会话令牌工作流隔离
- 标签页定向命令——无意外跨标签页变更
- 7 层回退链，从语义到原始 CDP
- 内置反模式防护和安全规则

</td>
</tr>
</table>

## ⚡ 快速开始

### 1. 安装 Omnibot

```bash
pip install omnibot
```

### 2. 启动守护进程

```bash
omnibot daemon run
```

### 3. 加载 Chromium 扩展

打开 Chrome 或 Edge，安装 Omnibot 扩展。保持至少一个 HTTP/HTTPS 标签页打开。

### 4. 验证连接

```bash
omnibot doctor
omnibot tabs
```

### 5. 给你的 agent 提供 skill

将 [`SKILL.md`](./SKILL.md) 放入你的 agent 的 skill 目录。完成——你的 agent 现在拥有浏览器超能力。

## 🔄 工作原理

每个浏览器操作都遵循严格的循环：

```
  ┌──────────┐      ┌──────────┐      ┌──────────┐
  │  观察    │ ───▶ │  操作    │ ───▶ │  验证    │──┐
  │          │      │ (一次)   │      │          │  │
  └──────────┘      └──────────┘      └──────────┘  │
       ▲                                              │
       └──────────── 失败则回退重试 ──────────────────┘
```

1. **观察** — 快照页面、读取内容、检查当前状态
2. **操作** — 使用最佳可用模式执行一次操作
3. **验证** — 用证据确认预期的状态变化

如果验证失败，agent 重新观察并尝试下一层回退。不盲目重试。不猜测。

## 🧩 原生命令路由

Omnibot 总是为任务选择最窄的原生命令：

| 意图 | 原生命令 | 不要用 |
|------|---------|--------|
| 读取页面内容 | `read`, `get text` | ~~`execute-js`~~ |
| 点击按钮 | `find --action click`, `click @eN` | ~~`querySelector().click()`~~ |
| 填充表单 | `fill`, `type` | ~~`element.value = "..."`~~ |
| 等待状态 | `wait` | ~~`sleep 3`~~ |
| 滚动 | `scroll`, `scrollintoview` | ~~`window.scrollTo()`~~ |

**原生优先。JavaScript 是回退，不是捷径。**

## 🏗️ 架构

```
Agent Skill (SKILL.md)
    │
    ▼
omnibot CLI  ──────────────────────────────┐
    │                                       │
    ▼                                       ▼
本地守护进程 (:18765)                Chromium 扩展
    │                                       │
    ├── 会话管理                            ├── DOM 访问
    ├── 命令路由                            ├── 无障碍树
    ├── 标签页追踪                          ├── 网络拦截
    └── 工作流隔离                          └── 视觉区域检测
```

**核心设计原则：**
- **可靠性 > 便利性** — 每个操作都被验证
- **显式状态 > 隐式状态** — 无隐藏假设
- **模式 > 命令** — 从任务出发，而非 API
- **允许回退，但不优先**

## 📚 文档

| 资源 | 描述 |
|------|------|
| [SKILL.md](./SKILL.md) | 完整的 agent 执行规范 |
| [命令参考](./references/command-reference.md) | 完整的 CLI 命令查询 |
| [操作模式](./references/operation-patterns.md) | 读取、点击、填充、滚动、导航、等待、提取、批处理 |
| [反模式](./references/anti-patterns.md) | 常见错误及如何避免 |
| [调试与证据](./references/debugging-and-evidence.md) | 截图、网络日志、追踪、录制/回放 |
| [会话与标签页](./references/session-and-tabs.md) | 工作流隔离和标签页定向 |
| [回退操作](./references/fallback-operations.md) | 7 层回退链详解 |

## 🤝 兼容的 Agent

Omnibot 适用于任何可以执行 CLI 命令的 agent 系统：

- 🧠 **Hermes** — 原生集成
- 🟠 **Claude Code** — 通过 skill 文件
- 📦 **Codex** — 通过 skill 文件
- 🔓 **OpenCode** — 通过 skill 文件
- 🔧 **任何支持 CLI 的 agent** — 通过 `omnibot` 命令

## 📋 示例工作流

```bash
# 设置工作流上下文
export OMNIBOT_SESSION_TOKEN=research

# 打开新标签页
omnibot open "https://github.com"

# 快照页面，带交互式引用
omnibot snapshot -i --tab-id $TAB_ID

# 点击搜索框并输入
omnibot find placeholder "Search GitHub" --action type \
  --action-value "omnibot" --tab-id $TAB_ID

# 按回车
omnibot press Enter --tab-id $TAB_ID

# 等待结果
omnibot wait --text "repositories" --tab-id $TAB_ID

# 读取结果
omnibot read --tab-id $TAB_ID
```

---

<div align="center">

**为需要"看到"网页的 agent 而生——而非仅仅抓取。**

[⭐ 在 GitHub 上 Star](https://github.com/DennisJcy/Omnibot-skills) · [📖 阅读 Skill 规范](./SKILL.md)

</div>

---

<a name="english"></a>
<div align="center">

## 🇬🇧 English Version

[🔝 Back to Top](#-omnibot)

</div>

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

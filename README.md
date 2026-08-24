# Research Knowledge Manager

An [Agent Skill](https://agentskills.io) that turns research material into a durable,
evidence-linked knowledge base of atomic notes — instead of a folder of summaries nobody reads
twice.

Vendor-neutral: one `SKILL.md`, installable into ~19 coding agents.

*[中文说明在下方](#中文说明)*

## The problem

Collecting material is not building knowledge. The usual failure looks like this: a paper gets
read, an AI writes `paper-A-summary.md`, the file is never opened again, and six months later the
same paper gets read from scratch. The material was filed. Nothing was learned.

This skill runs the other loop:

```
material → untouched source → atomic note → evidence → links → output → audit
```

Every step is reversible to the one before it. A claim in a report traces to a note; the note
traces to a page and figure in an original file that was never edited.

## What it enforces

| Rule | Why |
| --- | --- |
| Sources are immutable | Generated claims must trace back to untouched evidence |
| One note, one concept | `critical-current-density.md` gets reused for years; `paper-A-summary.md` gets read once |
| No claim without a source | Source, author, year, page, figure — or the note says `unverified` |
| Links must mean something | A link with a stated reason survives; graph padding becomes noise |

It also refuses to do things: never deletes, never restructures a vault on its own judgement,
never invents a citation or page number. Uncertain changes are written to
`00-Inbox/Needs-Review.md` as questions.

## Install

### Bundled installer (no dependencies)

```bash
git clone https://github.com/why913/research-knowledge-manager
cd research-knowledge-manager
node install.mjs            # dry run — shows exactly what it would write
node install.mjs --write    # install
```

It detects which agents are present on the machine and copies the skill into each one's user
skills directory. Copies rather than symlinks, so it needs no admin rights on Windows.

```
node install.mjs --list              # every known target
node install.mjs --targets claude,codex --write
node install.mjs --all --write       # every target, detected or not
```

### Manual

Copy the directory (`SKILL.md` + `references/`) into whichever path your agent reads. The
cross-agent one covers the most ground:

```bash
cp -r research-knowledge-manager ~/.agents/skills/
```

### Via the Vercel installer

If you already use [vercel-labs/skills](https://github.com/vercel-labs/skills):
`npx skills add why913/research-knowledge-manager`. That installer tracks vendor path changes
across 50+ targets, which the bundled script does not — but the bundled script is what this repo
tests against.

## Where it installs

User-scope paths, checked against each vendor's docs in August 2026.

| Target key | Agent | Path |
| --- | --- | --- |
| `standard` | **Cross-agent standard** | `~/.agents/skills/` |
| `claude` | Claude Code | `~/.claude/skills/` |
| `codex` | Codex CLI | `~/.codex/skills/` |
| `cursor` | Cursor 2.4+ | `~/.cursor/skills/` |
| `gemini` | Gemini CLI 0.26+ | `~/.gemini/skills/` |
| `copilot` | GitHub Copilot | `~/.copilot/skills/` |
| `codebuddy` | CodeBuddy | `~/.codebuddy/skills/` |
| `opencode` | OpenCode | `~/.config/opencode/skills/` |
| `windsurf` | Windsurf | `~/.codeium/windsurf/skills/` |
| `cline` | Cline | `~/.cline/skills/` |
| `roo` | Roo Code | `~/.roo/skills/` |
| `kilo` | Kilo Code | `~/.kilocode/skills/` |
| `amp` | Amp | `~/.config/agents/skills/` |
| `goose` | goose | `~/.config/goose/skills/` |
| `factory` | Factory Droid | `~/.factory/skills/` |
| `kiro` | Kiro | `~/.kiro/skills/` |
| `crush` | Crush | `~/.config/crush/skills/` |
| `pi` | Pi | `~/.pi/agent/skills/` |
| `antigravity` | Antigravity | `~/.gemini/antigravity/global_skills/` |

`~/.agents/skills/` alone is read by Codex (as its primary path), Cursor, Gemini CLI, Copilot,
Amp, and Warp natively, and by OpenCode, Cline, Roo Code, and Kilo Code as a fallback. If you
install to exactly one place, install there.

### Agents that don't read SKILL.md

Zed, Aider, Augment, Trae, and Kiro use their own rules formats. For those, `AGENTS.md` in this
repo is the entry point — it carries a condensed contract and points at `SKILL.md`. Copy it into
your project's `AGENTS.md`, `.rules`, or `CONVENTIONS.md`.

## Usage

Once installed, the agent loads the skill on its own when a task matches. You can also just ask:

- *Set up a research vault at D:\Vault*
- *Process the PDFs in 00-Inbox into notes*
- *Using only my vault, what do we actually know about interface stability?*
- *Draft the background section from my notes*
- *Audit the vault*

The last one is the one people skip and shouldn't. It reports duplicates, orphans, unsourced
claims, and broken links — without touching anything.

## Portability notes

Four things silently break a skill across agents. This repo handles all four; worth knowing if
you fork it.

1. **Frontmatter is limited to six fields** — `name`, `description`, `license`,
   `compatibility`, `metadata`, `allowed-tools`. Claude Code extensions like `when_to_use`,
   `argument-hint`, `paths`, or `model` cause `Unexpected key(s) in SKILL.md frontmatter` on
   claude.ai uploads and the Skills API.
2. **`name` must equal the directory name.** VS Code / Copilot skip the skill when they differ,
   with no error. `install.mjs` warns if you break this.
3. **The filename must be exactly `SKILL.md`.** Gemini CLI is case-sensitive about it.
4. **`SKILL.md` stays under 6000 characters** (Windsurf's per-file cap; 12000 total). Detail
   belongs in `references/`, loaded only when needed — which is what the format wants anyway.

Also: Antigravity uses `.agent/` (singular), everyone else uses `.agents/` (plural).

The skill body names no vendor-specific tool. Where it could use an Obsidian MCP server it says
so as a capability to detect, not a tool to call — so it works with or without one.

## Companion skill

[project-context-manager](https://github.com/why913/project-context-manager) does the same job
for software projects: durable engineering context so an agent picks a codebase up where the last
session left it. Same design, different domain — the two are independent and neither needs the
other.

## License

MIT

---

## 中文说明

一个把科研资料变成**长期可用、证据可追溯的原子笔记库**的 Agent Skill。不绑定任何厂商，一份
`SKILL.md` 可装进约 19 种 AI 编程助手。

### 它解决什么

收藏资料 ≠ 建立知识库。常见的失败是：读完论文，让 AI 写一份 `论文A总结.md`，然后再也不打开，
半年后同一篇论文重读一遍。资料归档了，知识没留下。

这个 skill 跑的是另一条链：

```
资料 → 原始文件(不可改) → 原子笔记 → 证据 → 双链 → 输出 → 巡检
```

每一步都能往回走一步。报告里的一句话能追到某张笔记，笔记能追到原始文件的某页某图，而那个原始
文件从头到尾没被改过。

### 四条不让步的铁律

| 铁律 | 为什么 |
| --- | --- |
| 原始资料不可变 | 不改原文，AI 生成的任何结论才能追溯回真实证据 |
| 一卡一概念 | `临界电流密度.md` 能复用好几年；`论文A总结.md` 只会被读一次 |
| 无出处不成立 | 来源/作者/年份/页码/图号，凑不齐就标 `unverified` |
| 双链必须有意义 | 写清为什么关联的链接才活得下来，为了图谱好看而堆的链接迟早变噪音 |

它同样明确**拒绝**做一些事：不删东西、不擅自重构知识库、不编造出处和页码。拿不准的改动写进
`00-Inbox/Needs-Review.md` 当问题提出来，而不是自己动手。

### 安装

```bash
git clone https://github.com/why913/research-knowledge-manager
cd research-knowledge-manager
node install.mjs            # 先空跑,看清它准备往哪些目录写
node install.mjs --write    # 真正安装
```

脚本会探测本机装了哪些 agent，把 skill 复制进各自的 skills 目录。用**复制而非软链**，所以
Windows 上不需要管理员权限。

只想装一处的话，装 `~/.agents/skills/` 覆盖面最广：Codex 拿它当主路径，Cursor、Gemini CLI、
Copilot、Amp、Warp 原生读它，OpenCode、Cline、Roo、Kilo 兜底读它。

完整路径对照表见上面英文部分的表格。

Zed、Aider、Augment、Trae、Kiro 这几个不读 `SKILL.md`，对它们用仓库里的 `AGENTS.md` —— 里面是
精简版约定加指路，直接粘进你项目的 `AGENTS.md` / `.rules` / `CONVENTIONS.md` 即可。

### 怎么用

装好之后 agent 会在任务对得上时自动加载。也可以直接说：

- *在 D:\Vault 建一个科研知识库*
- *把 00-Inbox 里的 PDF 处理成笔记*
- *只用我的知识库回答：界面稳定性方面我们到底掌握了什么*
- *用我的笔记起草背景章节*
- *巡检一遍知识库*

最后一条是最容易被跳过、但最该定期跑的：它会报出重复卡片、孤立卡片、没出处的结论、失效链接，
而且全程不动你任何文件。

### 姊妹 skill

[project-context-manager](https://github.com/why913/project-context-manager) 是同一套设计用在软件
项目上：把代码周边的上下文维持成真的，让 AI 下次开工能接着上次继续。两个仓库互相独立，装一个不
需要另一个。

### 授权

MIT

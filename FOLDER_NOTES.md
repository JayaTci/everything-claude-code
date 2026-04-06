# everything-claude-code/ — Folder Research Notes
_Researched: 2026-04-06_

## What This Folder Is
A **production-ready Claude Code plugin framework** found online (Anthropic Hackathon Winner, 140K+ stars, 21K+ forks, 170+ contributors). It is a full structured ecosystem of agents, skills, commands, hooks, and rules that dramatically extends what Claude Code can do.

Current version: **v1.10.0 (April 2026)**

## What It Contains (1,938 files / 66 MB)
| Component | Count | Purpose |
|-----------|-------|---------|
| `agents/` | 47 agents | Specialized AI agents (planner, code-reviewer, security-reviewer, language-specific reviewers, build resolvers, etc.) |
| `skills/` | 180 skill directories | Domain knowledge packs (React, Next.js, Django, Go, Rust, security, testing, etc.) |
| `commands/` | 79 commands | Slash commands like `/plan`, `/tdd`, `/code-review`, `/build-fix`, `/e2e`, `/refactor-clean`, etc. |
| `hooks/` | hooks.json | Pre/PostToolUse and lifecycle hooks — quality gates, security scanning, formatting, session summaries |
| `rules/` | 12+ languages | Coding standards per language (TypeScript, Python, Go, Rust, Java, Kotlin, C++, PHP, Swift, etc.) |
| `mcp-configs/` | mcp-servers.json | Pre-configured MCP servers (GitHub, Context7, Exa, Memory, Playwright, Sequential-Thinking) |
| `scripts/` | Node.js utilities | Install planner, CLI entry, worktree orchestration, session management, harness audit |
| `tests/` | 997+ tests | Full test suite covering hooks, scripts, configs, plugins |
| `contexts/` | 3 templates | Dev, research, review context templates |
| `examples/` | 6 CLAUDE.md files | Ready-made project CLAUDE.md for Django, Go, Rust, Laravel, Next.js, SaaS |

## Cross-Harness Support
Works with: **Claude Code, Codex, Cursor, OpenCode, Gemini**
Separate config folders: `.claude-plugin/`, `.codex/`, `.cursor/`, `.opencode/`, `.gemini/`, `.codebuddy/`, `.trae/`, `.kiro/`

## Internal Config (everything-claude-code/.claude/)
ECC has its own `.claude/` subfolder for its own development environment:
- `identity.json` — Technical level, style preferences, domain (JavaScript)
- `package-manager.json` — Uses `bun`
- `ecc-tools.json` — Full/enterprise profile tracking
- `rules/` — Auto-generated guardrails from repo history
- `skills/` — ECC self-development skill

## Role in Your Setup
This is the **heavy-duty engine**. Install it into your projects and it gives you:
- 38+ specialized agents instead of generic subagents
- 180 skill packs for domain-specific expertise
- 72 slash commands for common workflows
- Automated hooks for security, formatting, quality gates
- Session management and cost tracking

## Compatibility with .claude/
**Compatible — they serve different levels:**
- ECC operates at the project/install level via its own agents/skills/commands
- Your `.claude/CLAUDE.md` workflow rules sit on top and **do not conflict**
- Your `.claude/securitychecklist.md` and `writingstyle.md` are safe reference docs
- **Watch out:** Do not use the large `claude-opus-4.6.md` / `claude-sonnet-4.6.md` files from `.claude/` as active CLAUDE.md — they would override ECC's agent routing logic

## How to Use Both Together
1. Install ECC into your projects following its `install.sh` guide
2. Keep your `.claude/CLAUDE.md` as your personal top-level workflow rules
3. Let ECC handle agents, skills, commands, and hooks automatically
4. Use ECC's `examples/` CLAUDE.md templates as a starting point for new project CLAUDE.md files
5. Reference `.claude/securitychecklist.md` manually when needed (ECC automates most of it)

## Verdict
This is the primary power system. Use it as the foundation. Your personal `.claude/` folder is a lightweight overlay on top of it — they complement each other perfectly.

//////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////////


  How to Install ECC on Windows                                                                                                                                 
                                                                                                                                                                
  You do NOT run install.sh — that's for macOS/Linux. On Windows, you use install.ps1 in PowerShell (or npx ecc-install which works everywhere).
                                                                                                                                                                
  Option 1 — PowerShell (recommended for Windows)                                                                                                             

  Open PowerShell (not Command Prompt), navigate to the folder, and run:

  cd "D:\DEV\TESTPROJECT\CLAUDE_CONFIGURATION\everything-claude-code"
  npm install
  .\install.ps1 --profile full

  Option 2 — npx (works anywhere, including Git Bash)

  cd "D:/DEV/TESTPROJECT/CLAUDE_CONFIGURATION/everything-claude-code"
  npm install
  npx ecc-install --profile full

  ---
  What --profile full Does

  Installs everything — all agents, skills, commands, hooks, and rules into your user-level ~/.claude/ folder so it's available across all your projects.

  If you only want specific languages (e.g. you build websites with JavaScript/TypeScript):

  .\install.ps1 typescript

  ---
  Important: Run This Once, Not Per Project

  ECC installs globally into ~/.claude/. After that, every project you open in Claude Code automatically has access to all the agents and commands. You don't
  re-run the installer for each project.

  ---
  TL;DR: Open PowerShell → cd to the everything-claude-code folder → run npm install first → then .\install.ps1 --profile full.
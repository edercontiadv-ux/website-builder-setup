# Website Builder Setup for Claude Code

Build professional, animated websites with Claude Code — no coding experience needed.
This skill installs three tools that turn Claude into a full web design studio.

Built by [@tenfoldmarc](https://instagram.com/tenfoldmarc)

---

## Table of Contents

- [Install](#install)
- [What Gets Installed](#what-gets-installed)
- [Requirements](#requirements)
- [After Setup](#after-setup)
- [Manual Installation Fallback](#manual-installation-fallback)
- [Troubleshooting](#troubleshooting)
- [Compatibility](#compatibility)

---

## Install

### Easiest way

Open Claude Code and say:

> Install this skill for me: https://github.com/tenfoldmarc/website-builder-setup

Claude will handle the rest.

### Or do it yourself

**Mac / Linux:**
```bash
git clone https://github.com/tenfoldmarc/website-builder-setup.git ~/.claude/commands/website-builder-setup
```

**Windows (Command Prompt):**
```cmd
git clone https://github.com/tenfoldmarc/website-builder-setup.git %USERPROFILE%\.claude\commands\website-builder-setup
```

**Windows (PowerShell):**
```powershell
git clone https://github.com/tenfoldmarc/website-builder-setup.git "$env:USERPROFILE\.claude\commands\website-builder-setup"
```

Then type `/website-builder-setup` in Claude Code to get started.

---

## What Gets Installed

| Tool | What it does |
|------|-------------|
| **UI/UX Pro Max** | 50+ design styles, 161 color palettes, 57 font pairings. Your sites look designed, not AI-generated. |
| **Framer Motion** | Smooth animations — page transitions, hover effects, scroll reveals. The difference between a basic site and a premium one. |
| **21st.dev Magic** | 100+ production-ready React components. Buttons, navbars, hero sections, cards, footers — all pre-designed. |

---

## Requirements

- [Claude Code](https://docs.anthropic.com/en/docs/claude-code) installed
- [Node.js](https://nodejs.org) (LTS version, 18.x or 20.x recommended)
- npm (ships with Node.js)
- Git

---

## After Setup

Just tell Claude what you want:

```
Build me a landing page for my consulting business targeting small business owners.
Dark theme, modern, with animations.
```

Claude handles the rest — design, layout, animations, responsive, everything.

### Example Commands

- "Build a portfolio site for a photographer. Minimal, elegant, full-screen images."
- "Create a SaaS landing page with a hero, features section, pricing table, and FAQ."
- "Make me a personal blog with a dark theme and smooth page transitions."
- "Design a restaurant website with a menu section, reservation form, and photo gallery."

---

## Manual Installation Fallback

If the skill fails at any step, you can install everything manually:

```bash
# 1. UI/UX Pro Max
npm install -g uipro-cli
uipro init --ai claude

# 2. Framer Motion (run inside your Next.js project)
npm install framer-motion

# 3. 21st.dev Magic — add this to your ~/.claude.json
#    under the "mcpServers" key:
```

```json
{
  "mcpServers": {
    "21st-dev-magic": {
      "command": "npx",
      "args": ["-y", "@21st-dev/magic@latest"],
      "env": {
        "API_KEY": "your-api-key-here"
      }
    }
  }
}
```

Get your free API key at [https://21st.dev/magic/console](https://21st.dev/magic/console).

---

## Troubleshooting

### "npm install -g" fails with EACCES / permission error

**Mac / Linux:**
```bash
# Option 1: Fix npm permissions
npm config set prefix ~/.npm-global
echo 'export PATH=~/.npm-global/bin:$PATH' >> ~/.zshrc
source ~/.zshrc

# Option 2: Use nvm to manage Node (avoid permission issues)
curl -o- https://raw.githubusercontent.com/nvm-sh/nvm/v0.40.3/install.sh | bash
nvm install --lts
```

**Windows:**
Run your terminal **as Administrator** or use a Node version manager like [nvm-windows](https://github.com/coreybutler/nvm-windows).

### "uipro" command not found after install

Ensure npm global binaries are on your PATH:

**Mac / Linux:**
```bash
echo $PATH
# If ~/.npm-global/bin is missing, add it:
echo 'export PATH=~/.npm-global/bin:$PATH' >> ~/.zshrc
```

**Windows:**
```powershell
npm config get prefix
# Add the resulting path to your system PATH environment variables
```

### 21st.dev Magic not working after restart

1. Verify your `~/.claude.json` has the `21st-dev-magic` entry under `mcpServers`
2. Confirm your API key is correct at [https://21st.dev/magic/console](https://21st.dev/magic/console)
3. Make sure you **fully restarted** Claude Code (close terminal, open new one)
4. On Windows, the config file is at `%USERPROFILE%\.claude.json`

### Skills directory not recognized

Ensure the skill is in the correct location:

- **Mac / Linux:** `~/.claude/commands/website-builder-setup/`
- **Windows:** `%USERPROFILE%\.claude\commands\website-builder-setup\`

The `SKILL.md` file must be directly inside the `website-builder-setup/` directory.

---

## Compatibility

| Tool | Claude Code | OpenCode |
|------|:-----------:|:--------:|
| UI/UX Pro Max | ✅ | ✅ |
| Framer Motion | ✅ | ✅ |
| 21st.dev Magic (MCP) | ✅ | ⚠️ Path varies |

**For OpenCode users:** The MCP server configuration for 21st.dev Magic should be added to `opencode.json` (or `~/.config/opencode/opencode.json`) instead of `~/.claude.json`. Use the same JSON block shown in [Manual Installation Fallback](#manual-installation-fallback).

---

## License

MIT

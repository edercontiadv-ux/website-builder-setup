---
name: website-builder-setup
description: "Install the full AI website builder stack — UI/UX Pro Max, Framer Motion animations, and 21st.dev components. One skill, three tools, zero coding experience needed."
---

# Website Builder Setup

This skill walks you through installing everything you need to build professional, animated websites with Claude Code or OpenCode. No coding experience required.

## What Gets Installed

| Tool | What it does |
|------|-------------|
| **UI/UX Pro Max** | 50+ design styles, 161 color palettes, 57 font pairings. Your sites look designed, not generated. |
| **Framer Motion** | Smooth animations — page transitions, hover effects, scroll reveals. Makes sites feel alive. |
| **21st.dev Magic** | 100+ polished React components. Production-quality building blocks. |

## Workflow

Walk through each step one at a time. Be encouraging and clear — assume zero coding experience. If any step fails, don't stop. Acknowledge, give the manual command, keep moving.

---

### Step 1: Check Prerequisites

> Before we start, let me make sure you have everything we need.

Run:

```bash
node --version 2>&1 && npm --version 2>&1
```

- **Installed** → "You're good — Node.js is installed. Let's go."
- **Not installed** → "You need Node.js first. Go to https://nodejs.org and download the LTS version. Install it, restart your terminal, then run `/website-builder-setup` again. Takes 2 minutes."

Stop here if Node is missing.

---

### Step 2: Install UI/UX Pro Max

> **Step 1 of 3: UI/UX Pro Max**
>
> This gives me a massive design library — 50+ styles, 161 color palettes, 57 font pairings. When you ask me to build a website, I'm pulling from a real design system instead of guessing.
>
> Installing now...

Check if already installed:

```bash
uipro --version 2>&1
```

- **Already installed** → "UI/UX Pro Max is already installed. Skipping ahead."
- **Not installed** → continue below.

Install:

```bash
npm install -g uipro-cli 2>&1
```

If that fails with EACCES/permission error on Mac/Linux, fix npm prefix and retry:

```bash
npm config set prefix ~/.npm-global
npm install -g uipro-cli 2>&1
```

Then initialize:

```bash
uipro init --ai claude 2>&1
```

- **Success** → "UI/UX Pro Max is installed. Your design stack is ready."
- **Failure** → "Hit a snag. You can try manually later: `npm install -g uipro-cli && uipro init --ai claude`. Moving on."

---

### Step 3: Install Framer Motion

> **Step 2 of 3: Framer Motion**
>
> This teaches me how to add real animations to your websites — smooth page transitions, hover effects, scroll-triggered reveals.
>
> I need to install this inside your project folder. Are you currently in the project where you want to use animations? If not, please navigate to it and let me know.

**Ask the user to confirm they're in their project directory.**

Check if already installed in the project:

```bash
npm ls framer-motion 2>&1
```

- **Already installed** → "Framer Motion is already in this project. Moving on."
- **Not installed** → continue below.

Install:

```bash
npm install framer-motion 2>&1
```

Verify:

```bash
npm ls framer-motion 2>&1
```

- **Success** → "Framer Motion is installed. Version confirmed."
- **Failure** → "Hit a snag. You can try manually later inside your project folder: `npm install framer-motion`. Moving on."

---

### Step 4: Set Up 21st.dev Magic

> **Step 3 of 3: 21st.dev Components**
>
> This connects me to a library of 100+ beautifully designed React components. Instead of building everything from scratch, I pull from production-quality building blocks.
>
> This one needs a free API key. Here's how to get it:
>
> 1. Go to **https://21st.dev/magic/console**
> 2. Sign up or log in (it's free)
> 3. Copy your API key
> 4. Paste it here when I ask for it

Wait for the user to provide their API key.

Once they provide it, add the MCP server configuration. Read the existing config file — try these paths in order:

1. `./opencode.json` (current directory, OpenCode project-level)
2. `~/.config/opencode/opencode.json` (OpenCode global)
3. `~/.claude.json` (Claude Code)

Whichever file you find (or create if none exist), add or merge into the `mcpServers` object:

```json
{
  "mcpServers": {
    "21st-dev-magic": {
      "command": "npx",
      "args": ["-y", "@21st-dev/magic@latest"],
      "env": {
        "API_KEY": "THEIR_KEY_HERE"
      }
    }
  }
}
```

Tell the user: "I've added 21st.dev Magic to your AI tool config. You'll need to restart Claude Code (or OpenCode) for this to take effect."

---

### Step 5: Done

> **You're all set.** Here's what you just installed:
>
> - **UI/UX Pro Max** — 50+ styles, 161 palettes, 57 font pairings
> - **Framer Motion** — smooth, professional animations
> - **21st.dev Magic** — 100+ production-ready components
>
> **To build your first website, just tell me:**
> - What your business does
> - Who it's for
> - What vibe you want (dark, minimal, bold, playful, etc.)
>
> I'll handle the rest. Try something like:
>
> *"Build me a landing page for my consulting business targeting small business owners. Dark theme, modern, with animations."*
>
> **Important:** Restart Claude Code (or OpenCode) first so 21st.dev loads in. Then let's build something.

## Rules
- Walk through each step **one at a time**
- Never dump all instructions at once
- If any install fails, don't stop — acknowledge, give manual command, keep moving
- Be encouraging and casual throughout
- Assume zero coding experience
- Check if tools are already installed before re-installing
- Verify installations when possible
- Prompt them to build their first site at the end

# Browser Agent Demo Project (Copilot, Codex, Claude Code)

This repository is a practical demo for running browser-native agent workflows with `agent-browser` and modern AI coding assistants like Codex, Claude Code, and GitHub Copilot.

It shows how to:
- run real browser interactions from an AI coding agent
- capture evidence (screenshots, snapshots, text dumps)
- structure outputs and reports
- reuse shared instructions via `Agent.md` and local skills

## Demo Screenshots

![bitbasti.com annotated home](assets/readme/bitbasti-home-annotated-01.png)

## What This Project Is

This is an example project for browser automation and research tasks where an AI agent navigates sites step by step, validates results, and stores artifacts.

General use cases you can run with the same setup:
- real web research with evidence-backed source capture
- fetching specific data points from complex pages and multi-step flows
- verifying application workflows (signup, login, checkout, settings, forms)
- executing test scenarios and validating expected outcomes
- regression checks with snapshots/screenshots before and after changes
- UI/UX verification (copy, layout, states, responsiveness, accessibility hints)
- competitor and market monitoring with reproducible capture steps
- documentation generation from live browser sessions

## Prerequisites

- npm
- Chrome/Chromium (or use `agent-browser install` to download Chromium)
- An AI coding assistant (Codex, Claude Code, or Copilot)

## Install `agent-browser`

Recommended global install:

```bash
npm install -g agent-browser
agent-browser install
```

Official package and docs:
- https://www.npmjs.com/package/agent-browser
- https://github.com/vercel-labs/agent-browser

## Setup This Repository

```bash
git clone <your-fork-or-repo-url>
cd agent_browser_automated_testing
npm install
```

`npm install` is mainly useful here for local utilities/dependencies (for example report tooling), while browser control is done through `agent-browser`.

## Core Manual Browser Workflow

Use this interaction loop for most tasks:

```bash
agent-browser open https://example.com
agent-browser wait --load networkidle
agent-browser snapshot -i
agent-browser screenshot --annotate artifacts/example_step1.png
agent-browser click @e2
agent-browser snapshot -i
```

Rules of thumb:
- use refs from `snapshot -i` (`@e1`, `@e2`, ...)
- re-run `snapshot -i` after every navigation/major DOM change
- store evidence continuously, not only at the end

If you already run Chrome with remote debugging on the default CDP port (`9222`), you can reuse that session:

```bash
agent-browser --auto-connect open https://example.com
agent-browser --auto-connect snapshot -i
```

Why this is useful:
- reuses your dedicated debugging profile context across runs (cookies, logged-in sessions, local storage)
- makes interactive control easier while the agent runs (manual checks, manual navigation, debugging)
- lets you complete sensitive login steps yourself (SSO, MFA, captcha), then continue automated steps in the same authenticated browser context
- often reduces repeated blocking friction (cookie banners and captcha/risk prompts, e.g. on Google) compared to starting from a fresh headless session each run

Security note (Chrome 136+):
- For security reasons, Chrome ignores remote debugging switches on the default profile directory.
- Use a separate `--user-data-dir` for debugging/automation.
- Reference: https://developer.chrome.com/blog/remote-debugging-port

Windows example (dedicated debug profile directory):

```powershell
$chromeDebugProfile = Join-Path $env:LOCALAPPDATA "Google\Chrome\User Data\agent-browser-debug"
New-Item -ItemType Directory -Force -Path $chromeDebugProfile | Out-Null
& "C:\Program Files\Google\Chrome\Application\chrome.exe" --remote-debugging-port=9222 --remote-allow-origins=* --user-data-dir="$chromeDebugProfile" about:blank
```

Tip: to inspect startup/security problems, run Chrome once from terminal in headless mode with logging enabled to see the warning/error text:

```powershell
& "C:\Program Files\Google\Chrome\Application\chrome.exe" --headless=new --enable-logging=stderr --v=1 --remote-debugging-port=9222 --user-data-dir="$chromeDebugProfile" about:blank
```

Bash example (Linux/macOS):

```bash
$CHROME_DEBUG_PROFILE="${XDG_CONFIG_HOME:-$HOME/.config}/google-chrome-agent-browser-debug"
mkdir -p "$CHROME_DEBUG_PROFILE"
google-chrome --remote-debugging-port=9222 --remote-allow-origins=* --user-data-dir="$CHROME_DEBUG_PROFILE" about:blank
# macOS alternative:
CHROME_DEBUG_PROFILE="$HOME/Library/Application Support/Google/Chrome-agent-browser-debug"
mkdir -p "$CHROME_DEBUG_PROFILE"
"/Applications/Google Chrome.app/Contents/MacOS/Google Chrome" --remote-debugging-port=9222 --remote-allow-origins=* --user-data-dir="$CHROME_DEBUG_PROFILE" about:blank
```

Then connect from `agent-browser`:

```bash
agent-browser --auto-connect open https://example.com
agent-browser --auto-connect snapshot -i
```

If auto-discovery does not find your port, connect explicitly:

```bash
agent-browser --cdp 9222 open https://example.com
```

## How `Agent.md` Fits In

`Agent.md` is the high-context instruction profile for browser agent behavior in this project.  
It defines:
- expected CLI-first behavior with `agent-browser`
- evidence-first workflow (snapshots/screenshots/text extraction)
- execution style and reporting expectations

If you adapt this repo to a different domain (QA, lead research, accessibility checks), update `Agent.md` first.

## Use the Built-In Skill (`agent-browser`)

This repo includes a local skill:
- `.agents/skills/agent-browser/SKILL.md`

It provides:
- command patterns
- robust workflow guidance
- deep references under `.agents/skills/agent-browser/references/`
- ready templates under `.agents/skills/agent-browser/templates/`

There is also a compatibility junction at:
- `.agent/skills/agent-browser`

Depending on your Coding IDE you can also download the skill from the registry:

```bash
npx skills add https://github.com/vercel-labs/agent-browser --skill agent-browser
```

## Using With Codex, Claude Code, and Copilot

### Codex

Use prompts that explicitly request the browser skill or reference the local skill path.  
Example:

```text
Use the agent-browser skill and navigate manually. Do not write a full automation script.
```

### Claude Code

Install the upstream skill package if needed:

```bash
npx skills add vercel-labs/agent-browser
```

Then instruct Claude Code to use `agent-browser` with snapshot-ref workflow.

### GitHub Copilot

For environments supporting agent definition files, this repo includes:
- `.github/agents/Browser_Agent.md.agent.md`
- `.github/agents/Browser_Agent_with_Skills.md.agent.md`

These files can be used as reusable behavior profiles for browser-focused tasks.

## Learnings From This Demo

1. `GPT-5.3-Codex` performed best in the Codex extension during hands-on runs; GitHub Copilot with the Codex model also worked, but was less consistent.
2. Prompt explicitly: `Do not write a full automation script.` Ask the agent to take browser steps directly with `agent-browser`. Otherwise, it may default to writing a full script that might fail.
3. Use `--auto-connect` with Chrome remote debugging on `9222`; this avoids many repeated blockers (cookie banners, fresh-session friction) and makes interaction more stable.
4. Interaction quality is not perfect yet: some runs dump too much unnecessary content. A dedicated markdown-oriented text dump mode in `agent-browser` would likely reduce token usage. Until then, targeted `get text` and selective dumps work best.
5. In this workflow, Playwright MCP server interactions felt noticeably worse than direct `agent-browser` usage.

## Possible Ideas

- job market research with strict filters and evidence files (e.g., junior roles by city)
- multi-source web research with cited screenshots/text dumps per claim
- UI implementation testing after deployment (critical user journeys end-to-end)
- staging vs production verification for layout/content regressions
- ecommerce checkout and payment-path reliability validation
- account lifecycle testing (signup, verification email, login, password reset)
- release-note claim verification directly in product UI
- legal/compliance page monitoring (terms, privacy, cookie policy changes)
- support/help center audit (broken links, stale docs, wrong redirects)
- localization and translation consistency checks across locales
- pricing/plan comparison tracking across regions or competitors


**Respect robots.txt, site Terms, and legal boundaries**

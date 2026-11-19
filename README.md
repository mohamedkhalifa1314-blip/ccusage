# ccwaste-desktop

Find out where your Claude Code usage is going to waste.

ccwaste is a desktop app that reads the session logs Claude Code saves on your computer. It shows what each session cost and points out habits that burn tokens for no benefit.

> **Estimates only.** Dollar figures use the prices in `core.js`, which may not match Anthropic's current price list. Check the official prices before relying on them. On a subscription plan, the figures show what the same usage would cost on the API, not your actual bill.

## What it finds

- **Repeated reads**: the same file read many times with no edits in between
- **Tool loops**: the same command run again and again with the same result
- **Long sessions**: conversations that grow so large that every turn re-sends a huge history
- **Model switches**: simple tasks run on an expensive model that a cheaper one could handle
- **Bloated instruction files**: oversized `CLAUDE.md` files loaded into every session
- **Prompt habits**: vague requests, big inline pastes, and many tasks packed into one message

## Features

- Dashboard with total spend, session count, tokens and potential savings
- Tabs for Overview, Findings, Models, Tasks, Projects, Tips, Simulate, Pricing and Playbook
- Filters for date range, project name, minimum dollar value and number of top findings
- Simulate tab that replays your tokens at another model's prices
- Export your report as JSON or CSV
- Runs fully on your computer. The app makes no network requests and uploads nothing.

## Requirements

- [Node.js](https://nodejs.org) 18 or higher
- [Claude Code](https://claude.com/claude-code), with logs in `~/.claude/projects` (or `$CLAUDE_CONFIG_DIR/projects`)

Without Claude Code logs, the app opens but has nothing to analyze. The **Demo** button loads fake data so you can preview the interface.

## Install and run

```bash
git clone https://github.com/YOURNAME/ccwaste-desktop.git
cd ccwaste-desktop
npm install
npm start
```

On Windows PowerShell, if you get "running scripts is disabled", use `npm.cmd install` and `npm.cmd start` instead.

If your logs are in a different folder, click the gear icon in the top right, enter the folder path, and click Save.

## Build an installer

```bash
npm run dist
```

The installer for your operating system is written to `dist/`.

## Project layout

| File | Purpose |
| --- | --- |
| `main.js` | Electron main process: windows, settings, file export |
| `preload.cjs` | Safe bridge between the main process and the UI |
| `core.js` | Log parsing, pricing and analysis |
| `demo.js` | Generates fake logs for the Demo button |
| `renderer/` | The user interface (HTML, CSS, JavaScript) |

## Disclaimer

This project is not affiliated with or endorsed by Anthropic. Claude and Claude Code are products of Anthropic.

## License

MIT. See [LICENSE](LICENSE).

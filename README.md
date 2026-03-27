# 🌐 Agent Browser: A fast Rust-based headless browser automation CLI

![OpenClaw Skill](https://img.shields.io/badge/OpenClaw-Skill-blue) ![Status](https://img.shields.io/badge/Status-Active-green)

## Overview
This skill provides robust browser automation capabilities through the `agent-browser` CLI. It allows AI agents to interact with web pages by navigating, clicking elements, filling forms, extracting data, and taking screenshots or videos. Designed for speed and efficiency, it leverages a Rust-based core with a Node.js fallback, ensuring reliable operation across different environments.

## Features
- **Comprehensive Web Interaction:** Open URLs, navigate back/forward, reload, click, double-click, focus, fill/type text, press keys, hover, check/uncheck, select dropdowns, scroll, drag and drop, and upload files.
- **Page Analysis & Snapshotting:** Generate full accessibility trees or interactive element snapshots with unique references (`@e1`, `@e2`) for precise interaction.
- **Information Retrieval:** Get element text, HTML, input values, attributes, page title, current URL, element counts, and bounding boxes.
- **State Checking:** Verify element visibility, enabled status, and checked status.
- **Screenshots & PDF Generation:** Capture full-page or partial screenshots, and save pages as PDF documents.
- **Video Recording:** Record browser sessions for demos, debugging, or auditing.
- **Advanced Controls:** Mouse control, semantic locators (e.g., `find role button --name "Submit"`), browser settings (viewport, device emulation, geolocation, network headers, credentials, color schemes), cookie and local storage management.
- **Network Interception:** Route, abort, or mock network requests for testing and development.
- **Tab & Window Management:** List, open, switch, and close browser tabs and windows.
- **Frame & Dialog Handling:** Interact with iframes and manage browser dialogs (alerts, confirms, prompts).
- **JavaScript Execution:** Run arbitrary JavaScript code on the page.
- **Session Management:** Save and load browser session states (e.g., for authenticated sessions).
- **Parallel Sessions:** Run multiple isolated browser sessions concurrently.
- **Debugging Tools:** Headed mode, console logging, error viewing, element highlighting, trace recording, and Chrome DevTools Protocol (CDP) connection.

## Installation

### npm (Recommended)
```bash
npm install -g agent-browser
agent-browser install
agent-browser install --with-deps
```

### From Source
```bash
git clone https://github.com/vercel-labs/agent-browser
cd agent-browser
pnpm install
pnpm build
agent-browser install
```

## Usage

### Quick Start
```bash
agent-browser open <url>        # Navigate to page
agent-browser snapshot -i       # Get interactive elements with refs
agent-browser click @e1         # Click element by ref
agent-browser fill @e2 "text"   # Fill input by ref
agent-browser close             # Close browser
```

### Core Workflow
1.  **Navigate:** `agent-browser open <url>`
2.  **Snapshot:** `agent-browser snapshot -i` (returns elements with refs like `@e1`, `@e2`)
3.  **Interact:** Use refs from the snapshot to perform actions.
4.  **Re-snapshot:** After navigation or significant DOM changes, take a new snapshot.

## Configuration
The `agent-browser` CLI offers various options to configure its behavior:

| Option             | Description                                          |
| :----------------- | :--------------------------------------------------- |
| `--session <name>` | Uses an isolated session.                            |
| `--json`           | Provides machine-readable JSON output.               |
| `--full`           | Takes a full-page screenshot.                        |
| `--headed`         | Shows the browser window for debugging.              |
| `--timeout <ms>`   | Sets the command timeout in milliseconds.            |
| `--cdp <port>`     | Connects via Chrome DevTools Protocol.               |

> [!NOTE]
> For detailed command-specific options, refer to the `agent-browser` CLI help (`agent-browser --help` or `agent-browser <command> --help`).

## File Structure
This skill typically includes the `SKILL.md` and `_meta.json` files for OpenClaw integration. The core `agent-browser` CLI is managed as an external dependency.

| File          | Description                                                                     |
| :------------ | :------------------------------------------------------------------------------ |
| `SKILL.md`    | OpenClaw skill definition and detailed documentation for the `agent-browser` CLI. |
| `_meta.json`  | Metadata for the OpenClaw skill, including emoji and tool requirements.         |
| `CONTRIBUTING.md` | Guidelines for contributing to this skill. |

> [!IMPORTANT]
> The `_meta.json` file specifies that this skill requires `node` and `npm` to be available in the execution environment.

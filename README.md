# Vibe Harness

A complete, zero-dependency **single-file HTML AI coding agent harness** — one `index.html`, no build step, no install, no server. Open it and go.

## Features

- **Dual provider routing** — OpenRouter and Z.ai GLM Coding Plan endpoints, persisted in localStorage
- **Autonomous agent loop** — multi-step tool calling with SSE streaming, reasoning traces, chunked tool calls, Max Steps control, Stop / Pause / Resume
- **Workspace tools** — File System Access API folder mounting, `list_files` / `read_file` / `write_file` / `delete_file` / `edit_file`, `repo_map`, unified-diff confirm dialogs, checkpoints
- **Sandboxed `run_javascript`** — Blob Web Worker with console capture and timeout
- **`web_search`** — DuckDuckGo + Wikipedia in parallel
- **Ghostty-style terminal** — from-scratch ANSI/VT emulator, local shell over the mounted folder or an in-memory VFS, CLI adapters (`codex`, `kimi`, `glm`, `claude`, `agent`) sharing the real agent loop, WebSocket bridge for native CLIs
- **Rust WASM core** — embedded `no_std` module (token estimation, fuzzy scoring, bracket scanning, FNV-1a) exposed via the command palette and search
- **Approvals & policy** (ported from [harness-wasm](https://github.com/CartyChris/harness-wasm)) — read-only / ask / auto approval modes, per-tool allow/ask/deny rules, "always allow" rules, secrets redaction (`sk-or-*`, bearer tokens, env values), append-only event log
- **Pause / Resume / Retry** — turn pause, retry of the last turn, reload-recovery of interrupted turns
- **Persistent memory** (MemGPT-inspired) — agent-stored notes injected into every future turn
- **BM25 workspace search** (LlamaIndex-inspired) — chunked, ranked retrieval over mounted files
- **Task plan panel** (OpenHands-inspired) — live step tracking the agent updates itself
- **Commit journal** (aider-inspired) — automatic checkpoints with `/journal` and `revert_commit`
- **Ghostty terminal theming** + 14-appearance theme system
- **iPhone Air optimized** — safe-area layouts, drawer sidebar, bottom-sheet dialogs, 42–46 px touch targets, zero emoji (full inline-SVG icon set)
- **Command palette** (Ctrl/Cmd+K), file jumper, chat search, voice dictation, vision attachments, notifications, export MD/JSON, sessions manager

## Usage

1. Open `index.html` in Chrome/Edge (desktop) or the Documents/Textastic app (iPhone Air).
2. Enter an OpenRouter or Z.ai API key.
3. Optionally mount a folder (desktop) or use the built-in VFS (mobile).
4. Send a task — or type `/help`.

## Notes

- Everything runs client-side; API keys are stored only in your browser's localStorage.
- Native CLI binaries work only through the terminal's loopback `bridge` mode (browsers can't spawn processes).
- CORS may block direct API calls in some contexts; the OpenRouter and Z.ai coding endpoints are normally reachable.

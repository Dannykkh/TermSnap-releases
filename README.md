# TermSnap

AI-powered terminal for Windows. Run Claude Code, Codex, or Gemini CLI on your desktop, then continue coding from your phone.

![.NET](https://img.shields.io/badge/.NET-8.0-512BD4?logo=dotnet)
![Platform](https://img.shields.io/badge/Platform-Windows-0078D6?logo=windows)
![License](https://img.shields.io/badge/License-MIT-green)
![Version](https://img.shields.io/badge/Version-2.0.0-blue)

**[Korean](README.ko.md)** | English

---

## Code from anywhere

TermSnap 2.0 embeds a web server. Start an AI coding session on your desktop, scan a QR code, and pick up the same session on your phone or tablet. No port forwarding, no cloud relay. Your browser connects directly to the desktop app over your local network.

The web client has two modes:

- **Stream**: raw terminal output forwarded to your mobile browser in real time
- **Chat**: clean conversation bubbles parsed from the AI's response files, so you read structured answers instead of raw VT100 escape codes

Ask a question from your phone, watch the AI work on your desktop terminal, read the formatted answer on your phone. Works with Claude Code, Codex, and Gemini CLI.

---

## What it does

TermSnap is a terminal that runs AI coding tools (Claude Code, Codex, Gemini CLI) and SSH connections in one window, with mobile access built in.

### AI coding sessions

Open a project folder and start Claude Code, Codex, or Gemini CLI as sub-tabs inside a single project tab. Run PowerShell alongside them. The file explorer stays pinned to the project. Open files in VS Code or Cursor directly from the tree.

### SSH with AI commands

Connect to servers and ask in plain language:

```
You type:  "restart nginx"
AI returns: sudo systemctl restart nginx
```

Commands are cached. Ask the same thing twice and TermSnap returns the cached answer without an API call. Dangerous commands like `rm -rf /` are blocked. SFTP is built in with 4 parallel streams.

### System monitoring

The footer shows system-wide CPU, memory, and GPU stats in real time. Hover for details including GPU temperature and VRAM. When your computer feels slow, check the footer.

---

## Mobile web client

### How it works

1. Click the mobile icon in TermSnap's toolbar
2. Scan the QR code with your phone
3. Pick a terminal session to connect to
4. Choose Stream (raw terminal) or Chat (formatted AI responses)

### Chat mode

Chat mode reads from `conversations/` files that AI CLIs generate. No ANSI parsing, no noise. You see clean markdown-formatted answers with a chat bubble UI. Type a question, watch the spinner, read the answer.

### Stream mode

Stream mode forwards raw terminal output. Good for watching builds, tailing logs, or monitoring long-running processes.

---

## Desktop features

### Tabs inside tabs

One project tab holds multiple sub-tabs: PowerShell, Claude Code, Gemini CLI. Drag to reorder. Close the app, reopen it, everything comes back.

### File editor

Built on AvalonEdit. Syntax highlighting for 20+ languages, code folding, find/replace. Read-only by default, Ctrl+E to edit.

### Terminal engine

ConPTY-based, so vim, htop, and nano work. Supports PowerShell, CMD, WSL, Git Bash. GPU-accelerated rendering at 30fps with per-line caching.

### SSH features

- AI command generation with hybrid RAG search and smart model routing
- Error analysis with auto-retry (up to 3 attempts)
- Server monitoring: CPU, memory, disk, network, top processes
- Port forwarding: Local, Remote, Dynamic (SOCKS)
- SFTP: 256KB buffers, 4 concurrent streams

### Skills and memory

The Skills tab analyzes your project's tech stack and recommends relevant tools. Long-term memory persists in MEMORY.md across sessions. Past conversations are searchable.

---

## Install

Requirements: Windows 10/11 (64-bit), .NET 8.0 Runtime

Download from [Releases](https://github.com/Dannykkh/TermSnap-releases/releases), run the installer, open the app.

### Build from source

```bash
git clone https://github.com/Dannykkh/TermSnap.git
cd TermSnap
dotnet build
dotnet run --project src/TermSnap/TermSnap.csproj
```

AI features need an API key (Settings > AI Models). [Gemini](https://ai.google.dev/) has a free tier. SSH, SFTP, and local terminals work without one.

---

## Quick start

1. Settings > AI Models > paste your API key
2. New Tab > Local Terminal > open a project folder
3. Add sub-tabs: Claude Code, Codex, or Gemini CLI
4. Click the mobile icon > scan QR > code from your phone

---

## Keyboard shortcuts

| Shortcut | Action |
|----------|--------|
| Ctrl+L | New local terminal |
| Ctrl+T | New SSH connection |
| Ctrl+Tab | Next tab |
| Ctrl+W | Close tab |
| Ctrl+Shift+N | New sub-tab |
| Ctrl+Shift+P | Command palette |
| Ctrl+E | Toggle edit mode |
| Ctrl+S | Save file |

---

## Tech stack

| | |
|---|---|
| Framework | .NET 8.0 / WPF |
| Web | ASP.NET Core + SignalR + React |
| AI | Claude Code, Codex, Gemini CLI, Gemini/OpenAI/Claude/Grok API |
| SSH/SFTP | SSH.NET |
| Editor | AvalonEdit |
| UI | Material Design In XAML |
| Terminal | ConPTY |

---

## Docs

- [AI workflow guide](docs/AI_WORKFLOW_GUIDE.md)
- [Local terminal guide](docs/LOCAL_TERMINAL_GUIDE.md)
- [SSH session guide](docs/SSH_SESSION_GUIDE.md)
- [Full user guide](docs/USER_GUIDE.md)

---

## License

MIT

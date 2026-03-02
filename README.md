# 🐰 Rabbit R1 OpenClaw QR Generator 🦞

[![Test index.html](https://github.com/johndotpub/rabbit-openclaw-qr-generator/actions/workflows/test-index.yml/badge.svg)](https://github.com/johndotpub/rabbit-openclaw-qr-generator/actions/workflows/test-index.yml)
[![Test localhost.html](https://github.com/johndotpub/rabbit-openclaw-qr-generator/actions/workflows/test-localhost.yml/badge.svg)](https://github.com/johndotpub/rabbit-openclaw-qr-generator/actions/workflows/test-localhost.yml)
[![License: Unlicense](https://img.shields.io/badge/license-Unlicense-bd93f9.svg)](https://unlicense.org/)
[![OpenClaw](https://img.shields.io/badge/OpenClaw-Gateway-50fa7b.svg)](https://forum.rabbitcommunity.tech/t/how-to-connect-your-r1-to-openclaw-formerly-moltbot-clawdbot/15646)
[![Rabbit R1](https://img.shields.io/badge/Rabbit-R1-ff79c6.svg)](https://rabbit.tech)

> 🔗 **Live site:** [claw.rly.wtf](https://claw.rly.wtf)

A small, single-file tool that generates an **OpenClaw gateway payload** as:

- 📋 a **JSON preview** (copy/paste)
- 📱 a **QR code** (scan to import)

Everything runs **locally in your browser** 🔒 (no backend).

> ⚠️ Important: the **token is embedded** in the JSON and QR. Treat the QR like a password.

Based on the [R1 OpenClaw connection guide](https://forum.rabbitcommunity.tech/t/how-to-connect-your-r1-to-openclaw-formerly-moltbot-clawdbot/15646) and [r1-openclaw.sh](https://rabbit.tech/r1-openclaw.sh).

---

## 🗂️ What's in this repo?

This repo intentionally ships as static HTML with a **Dracula**-inspired dark theme. There are two builds with different safety profiles:

### 🦞 `localhost.html` — read-only (recommended for public hosting)

- Generates JSON + QR locally
- **No network test features** (cannot open WebSockets)
- Best choice for GitHub Pages / sharing a link broadly
- 🐰 Safe to share with anyone

### 🐰 `index.html` — advanced (includes optional WebSocket test)

- Same generator features as `localhost.html`
- Adds an **opt-in WebSocket connection test** intended for local/controlled use
- The UI gates the test behind explicit confirmation so it's harder to send tokens by accident
- 🔧 Best for developers and advanced users

---

## 🔒 Security model (please read)

### The QR contains secrets

The payload includes your `token`. If you share any of the following, you are effectively sharing the token:

- 📸 screenshots of the QR
- 📄 the JSON preview
- 🎥 recordings/streams where the token is visible

### 🏠 Hosting guidance

- If you're publishing on GitHub Pages: **prefer `localhost.html`** 🦞
- If you use `index.html`: consider hosting it **behind authentication** and avoid distributing a public link 🔐

---

## 📦 Payload format

The generator outputs JSON like:

```json
{
  "type": "openclaw-gateway",
  "version": 1,
  "ips": ["192.168.1.10", "10.0.0.5"],
  "port": 8080,
  "token": "your-token-here",
  "protocol": "ws"
}
```

Field notes:

- `ips`: entered as comma-separated values in the UI; output is an array of strings
- `protocol`: `ws`, `wss`, or `tcp` (depending on your environment)
- `version`: payload schema version (currently `1`)

---

## 🚀 How to use

1. Open **`localhost.html`** (recommended) or **`index.html`** in a modern browser
2. Enter IP(s), port, protocol, and token
3. Click **🔨 Build QR**
4. Scan the QR to import, or click **📋 Copy JSON**
5. Optional: click **💾 Download QR** to save a PNG

---

## 🧪 WebSocket test mode (only in `index.html`)

The WebSocket test is meant to verify connectivity to a host you specify.

Built-in guardrails:

- ✅ Explicit opt-in (you must enable test mode)
- ✅ Confirmation prompts before sending the token
- ✅ Forces `wss` if the page is served over HTTPS (avoids mixed-content blocking)
- ✅ Auto-closes the socket after ~20 seconds
- ✅ Basic client-side cooldown / rate limiting

---

## 🌐 Publish on GitHub Pages (recommended: read-only build)

1. In GitHub: **Settings → Pages**
2. Choose **Deploy from a branch**
3. Select:
   - Branch: `main`
   - Folder: `/ (root)`
4. Your read-only page will be available at:

`https://johndotpub.github.io/rabbit-openclaw-qr-generator/localhost.html`

If you want the safe build to load at the default repo Pages URL (`/`), rename `localhost.html` to `index.html` (only do this if you don't need the advanced test build).

---

## 🧑‍💻 Development

This project is intentionally minimal. `package.json` exists for optional local lint scripts and test dependencies.

### Running tests locally

```bash
npm install
npx playwright install chromium
# Tests run automatically in CI via GitHub Actions
```

---

## 🎨 Theme

The UI uses a **Dracula**-inspired color scheme:
- Background: `#282a36` · Cards: `#44475a`
- Purple: `#bd93f9` · Pink: `#ff79c6` · Cyan: `#8be9fd`
- Green: `#50fa7b` · Orange: `#ffb86c` · Red: `#ff5555`

---

## 📜 License

Released under **The Unlicense** (public domain) 🐰🦞

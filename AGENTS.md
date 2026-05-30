# AGENTS.md

## Cursor Cloud specific instructions

### Product

**SparkMath Arcade — Chalkboard Odyssey** is a single-page, client-only math practice app (`index.html`). There is no backend, database, or package manager. State persists in browser `localStorage`.

### Running locally

Start a static HTTP server from the repo root (do not open `file://` — CDN scripts and some APIs behave more reliably over HTTP):

```bash
cd /workspace && python3 -m http.server 8080
```

Open `http://localhost:8080/`.

Alternatives: `npx --yes serve /workspace -p 8080` or `npx --yes http-server /workspace -p 8080`.

### Services

| Service | Required | Notes |
|---------|----------|--------|
| Static HTTP server on port 8080 | Yes | Only runtime dependency for local dev |
| Backend / Docker / Workers | No | Not used in this repo |

### Lint / test / build

There is no `package.json`, Makefile, linter config, or automated test suite. Verification is manual in the browser: create a student profile, play a mode, and optionally use **Educator Access** with PIN `6767`.

### Network

First load requires outbound network for Tailwind, Chart.js, Lucide, and Google Fonts CDNs.

### Educator PIN

The educator PIN is hardcoded client-side in `index.html` (`SECURITY_PIN = "6767"`). It is not a server secret.

### tmux

If you need a long-lived dev server, use a named tmux session (e.g. `math-game-server`) so the process survives backgrounding.

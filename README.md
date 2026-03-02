# R1 OpenClaw QR — Single File Generator

This repository contains two single-file HTML artifacts and a GitHub Actions workflow.

Files:
- rabbit-openclaw-qr-generator.html — Full build with gated WebSocket test (opt-in).
- rabbit-openclaw-qr-generator_readonly.html — Read-only build safe for public hosting.
- .github/workflows/ci.yml — CI workflow for linting, audit, optional Lighthouse, and deploy to GitHub Pages.
- package.json — minimal dev dependencies for local linting (optional).
- .gitignore — standard ignores.

Usage:
- Open either HTML file in a modern browser to test.
- To publish the read-only file on GitHub Pages, place it in the repo root or docs/ and enable Pages.

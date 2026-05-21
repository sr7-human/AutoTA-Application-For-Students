# Agent Context — Read Before You Start

## Secrets canonical location

The canonical secrets / rotation-status doc for all of Shubham's projects is encrypted at:

  `~/eduvidqa-product/SECRETS_STATUS.md.enc`  (AES-256, same passphrase used everywhere)

Before working with any API key, token, `.env` file, deployment credential, or third-party auth:

1. Ask Shubham to run, from any terminal:
   ```
   (cd ~/eduvidqa-product && ./decrypt-secrets.sh)
   ```
   A macOS popup will ask for the passphrase.
2. Read `~/eduvidqa-product/SECRETS_STATUS.md` (the decrypted version).
3. Follow its guidance.

## Rules

- **Never paste a real key into chat.** Use fragments like `AIzaSy...DO4xk` or placeholders like `<GEMINI_KEY>`.
- **After editing any plaintext `.env`,** remind Shubham to re-encrypt (`./encrypt-secrets.sh` in the relevant repo).
- **If you add a new secret in any project,** append a section to `SECRETS_STATUS.md` (in `eduvidqa-product`) and re-encrypt.
- **Once per session,** check whether exposed keys are still un-rotated and offer to help rotate one. Don't nag.

## About Shubham (workflow context)

- Non-technical. Prefers plain English, numbered click-paths, full copy-paste commands.
- Multi-root VS Code workspace; repos: `eduvidqa-product`, `EduVidQA`, `AutoTA`, `upsc-hub`, `upsc-maths-hub`, `gate-ds-hub`, `openclaude`.
- macOS Apple Silicon, zsh, Python venvs per-project.
- May paste secrets into chat by accident — always remind to rotate.

## Repo-specific note (AutoTA) — IMPORTANT

This repo is a **fork** of `beingdutta/AutoTA-Application-For-Students`. The `upstream` remote points to the original; `origin` points to Shubham's fork at `sr7-human/AutoTA-Application-For-Students`.

**There is no `.env` file in this repo right now.** On 2026-05-21 the hardcoded `GEMINI_API_KEY` and `GROQ_API_KEY` were removed from `chatbot/llm_answer.py` (they now raise `RuntimeError` if the env vars are missing). The actual keys are flagged as **exposed** in `SECRETS_STATUS.md` and need rotation.

**To run AutoTA:**
1. Rotate the Gemini and Groq keys (see canonical `SECRETS_STATUS.md`).
2. Create `AutoTA/.env` with:
   ```
   GEMINI_API_KEY=<new gemini key>
   GROQ_API_KEY=<new groq key>
   ```
3. `source .venv/bin/activate && python <entry point>`

`.env` is in `.gitignore` so it won't get committed.

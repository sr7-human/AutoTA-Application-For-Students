# AutoTA: new-system handoff

Source-transfer date: 19 November 2026.

This is the owner's public fork of AutoTA. Read the existing license,
attributions, `AGENTS.md` and `README.md`. Preserve upstream credit.

## Get the transferred work

```sh
gh auth login
gh auth setup-git
git clone --branch transfer/new-system-2026-11-19 https://github.com/sr7-human/AutoTA-Application-For-Students.git
cd AutoTA-Application-For-Students
```

Default `master` is intentionally unchanged. This branch is a development backup,
not a deployment. The transfer includes selected workflow/configuration notes.
Unrelated local screenshots and credentials are excluded.

## Windows, Linux and macOS

Recreate dependencies; do not copy another computer's virtualenv. Python 3.12 is
an initial setup candidate, not a claim that the full stack is certified on it.
Check the dependency manifest and resolve supported-runtime requirements before
installing. WSL2 Ubuntu is a useful first option for Windows media/ML dependencies.

Linux/macOS/WSL:

```sh
python3 -m venv .venv
.venv/bin/python -m pip install -r requirements.txt
.venv/bin/python -m streamlit run Home.py
```

Windows PowerShell:

```powershell
py -3.12 -m venv .venv
.\.venv\Scripts\python.exe -m pip install -r requirements.txt
.\.venv\Scripts\python.exe -m streamlit run Home.py
```

These are setup/start commands, not verified cross-platform acceptance results.
Media packages may require FFmpeg and platform-specific dependencies.

## Credentials

Do NOT follow the old README instruction to put API keys in Python source.
The LLM module expects environment variables. Provision fresh credentials through
an approved private process. Do not copy tokens into chat, Git, launcher arguments
or remote URLs. No real credentials or environment files are supplied by this
transfer. The old encrypted credential passphrase is unavailable; do not guess
it or run an old decryption script over surviving configuration files.

## Synchronization

Before working:

```sh
git status --short --branch
git pull --ff-only origin transfer/new-system-2026-11-19
```

Stop if there are dirty files or divergent commits. Preserve and inspect them;
never force-push or hard-reset to hide a conflict.

After working, review and add only selected safe files:

```sh
git add -- path/to/reviewed-file
git diff --cached --stat
git commit -m "Describe the change [skip ci]" -m "Co-authored-by: Copilot <223556219+Copilot@users.noreply.github.com>"
git push origin HEAD:refs/heads/transfer/new-system-2026-11-19
git rev-parse HEAD
git ls-remote origin refs/heads/transfer/new-system-2026-11-19
```

The last two hashes must match. Scan for secrets before publication.
Never bulk-add screenshots, environment files, private user data or model caches.
Do not push to the upstream author's repository unless explicitly requested.

For a future desktop controller, use per-machine paths and venv interpreters,
loopback-only management, tracked child processes and explicit readiness/error
reporting. Do not bundle secrets or silently install, migrate, deploy or push Git
changes when opening the launcher. Separate OS builds and acceptance tests are
required; no executable was built during this source transfer.

## Repository-specific transfer record


- Repository: `sr7-human/AutoTA-Application-For-Students`
- Transfer branch: `transfer/new-system-2026-11-19`
- Original source HEAD: `368a08388bb4c4690a1b6fb13ffbce51cf650c01`
- Published default baseline: `368a08388bb4c4690a1b6fb13ffbce51cf650c01`
- Snapshot policy: preserve source ancestry and selected working-tree changes

Selected local workflow/configuration notes only; public fork, upstream attribution preserved.

### Newly included files

- `.clinerules/glm-workflow.md`
- `.zcodeignore`
- `SETUP-GLM.md`

### Excluded paths (not transferred by this snapshot)

- `chatbot/__pycache__/__init__.cpython-310.pyc`
- `chatbot/__pycache__/__init__.cpython-311.pyc`
- `chatbot/__pycache__/llm_answer.cpython-310.pyc`
- `chatbot/__pycache__/llm_answer.cpython-311.pyc`
- `utils/__pycache__/__init__.cpython-310.pyc`
- `utils/__pycache__/__init__.cpython-311.pyc`
- `utils/__pycache__/screenshot.cpython-310.pyc`
- `utils/__pycache__/screenshot.cpython-311.pyc`
- `contents.png`
- `count1.png`
- `count2.png`
- `eduvidqa-prototype-full.jpeg`
- `p2.png`
- `p2b.png`
- `plain.png`
- `shell.png`
- `shell2.png`
- `tour1.png`
- `tour2.png`
- `watch-01-check.png`
- `wv.png`

Excluded files remain on the original Mac. Do not assume ignored databases, media,
credentials or dependency directories can be recovered with Git. Validation results
and exact published hashes are recorded in the transfer summary supplied to the owner.

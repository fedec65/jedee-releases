<p align="center"><img src="icon.png" width="512" alt="Jedee.co icon"></p>

# jedee-releases

Official downloads for **Jedee.co** — a desktop app that lets you run teams of AI assistants on your own computer.

This page is the **only place you need to grab installers and updates**. The app checks this page automatically and tells you when a new version is available.

---

## What is Jedee.co?

Jedee.co is a desktop app for your computer that lets you **set up a team of AI assistants, give them jobs to do, and watch them work**.

Each assistant (we call them "agents") has a role — for example "researcher", "writer", "developer" — and uses an AI model you choose (ChatGPT, Claude, or a model running locally on your machine with Ollama). You describe the goal, the assistants collaborate, share files, call web tools, and report back when they're done.

Everything happens **on your computer**:

- No account, no signup.
- No data sent to jedee.co or any analytics service.
- Your conversations and files stay on your disk.
- Your AI provider keys are stored in your operating system's secure vault (Keychain on Mac, Credential Manager on Windows).

Jedee.co works fully offline once installed. It only goes online to call the AI provider you configured and to check this page for updates.

### Why people like it

- **Private by default** — no telemetry, no third-party analytics, no cloud account. Your provider keys never leave the secure vault of your OS; your conversation data never leaves the database on your disk.
- **Bring your own AI** — use OpenAI-compatible services, Anthropic, or a local Ollama installation. Switch providers without changing your workflow.
- **Run teams, not single chats** — describe a team of agents with dependencies between their tasks, hit run, and watch the work unfold in a live console.
- **See everything that happens** — every tool call, message, and decision is visible while the run is in progress; full transcripts are saved locally so you can inspect exactly what each agent did.
- **Automate what you repeat** — turn a finished run into a saved automation, then rerun it on a schedule or with one click.

## What you get with each release

Every release here includes:

- **macOS**: a signed and notarized `Jedee.co_*.dmg` for Apple Silicon and Intel Macs. Double-click to open, drag Jedee.co into Applications, done.
- **Windows**: a signed `Jedee.co_*.exe` (NSIS installer) and `*.msi` (WiX). Run either one and follow the prompts.
- **Updates**: when a new version is released, the app notifies you in the bottom-right corner of the window and updates itself automatically — you don't need to come back here. If automatic update is off (or blocked), you can always grab the latest installer from this page.

## How to install on macOS

1. Download the `.dmg` for the latest version.
2. Double-click the `.dmg` to mount it.
3. Drag **Jedee.co** into your Applications folder.
4. First launch: right-click Jedee.co in Applications → Open (macOS checks the signature first; once you confirm, it launches normally afterwards).

## How to install on Windows

1. Download the `.exe` (recommended) or `.msi` for the latest version.
2. Run it and follow the installer prompts. The app installs for the current user.
3. Launch Jedee.co from the Start menu.

## Keeping Jedee.co updated

The app checks this page (via `latest.json`) at launch and periodically while running. When a new version is found, it downloads the update in the background, then asks you to restart to apply it.

Prefer not to auto-update? You can turn it off in the app under **Settings › General**. You can also reinstall manually from this page any time — same result.

## Why a separate repository?

Releases live in this repo — not on the jedee.co codebase repo — so that:

- Nobody can push a fake update into your app by opening a PR against the source repo.
- Anyone can inspect the release feed (`latest.json`) and the installers without wading through source code.
- The source repo stays clean: only code, docs, and issues.

## How updates are published

The release workflow in the [jedee.co source repo](https://github.com/fedec65/jedee.co) builds and signs installers on every new tag, then publishes them here as a **GitHub release** with:

- `latest.json` — the update manifest the app polls.
- `*.dmg`, `*.exe`, `*.msi` — installers for both platforms.
- `*.sig` — Ed25519 signatures (the app verifies these before applying an update).

The workflow uses the release feed's own `RELEASES_FEED_TOKEN` secret so it can publish here; the source repo has no other write access to this one.

## License

Jedee.co source code is proprietary. The installer files in this repository are distributed under the same terms as the app (see the EULA shown on first launch). Nothing here is sold or licensed for redistribution.

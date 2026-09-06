<p align="center"><img src="icon.png" width="512" alt="Jedee.co icon"></p>

# jedee-releases

Official downloads for **Jedee.co** — a desktop app that lets you run teams of AI assistants on your own computer.

This page is the **only place you need to grab installers and updates**. The app checks this page automatically and tells you when a new version is available.

New to the app? Start with the [**User Guide**](USER-GUIDE.md) — it walks you through first launch, providers, chat, permissions, connectors, automations and more.

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
- **See everything that happens** — every tool call, message, and decision is visible while the run is in progress; full transcripts are saved locally so you can replay or audit later.
- **Works offline** — fast, no backend to set up, no server to maintain.
- **Sensible defaults, escape hatches when you need them** — built-in file and web tools are sandboxed and opt-in per agent; you stay in control of what each agent can touch.

---

## Latest release

**[Jedee.co v0.18.1](https://github.com/fedec65/jedee-releases/releases/latest)** _(current)_

What's new since the previous version:

- A friendlier first-run welcome — when you start the app for the first time you now pick your language (we'll guess it from your system) and optionally your name, then get a short tour.
- A new "Help & guides" tile on the welcome screen — finishing the tour drops the help keyword for your language right into the chat composer, so you can ask the app for help in your own words.
- Small polish: pop-ups no longer grow past the window edge on small displays.

Full notes for every version live on each [Release page](https://github.com/fedec65/jedee-releases/releases).

---

## Install

### macOS (Mac with Apple Silicon or Intel)

1. Download **`Jedee.co_0.18.1_universal.dmg`** from the [latest release page](https://github.com/fedec65/jedee-releases/releases/latest).
2. Open the `.dmg` and drag **Jedee.co** to your **Applications** folder.
3. The first time you launch it, macOS may ask you to confirm the app is from an identified developer — right-click the app in Applications and choose **Open**, then confirm.

Requires **macOS 11.0 (Big Sur)** or later.

### Windows (PC, 64-bit)

Pick the installer that suits you:

- **`Jedee.co_0.18.1_x64_en-US.msi`** — the standard Windows installer. Best if your IT department manages installs or you want a silent install.
- **`Jedee.co_0.18.1_x64-setup.exe`** — a friendlier installer wizard. Best for most home users.

Both will update an existing install in place. Requires **Windows 10 (1809)** or later.

### Is it safe to install?

Yes. Jedee.co installers are **built by an automated pipeline on a clean machine every release, signed with a developer certificate, and published as GitHub Releases**. Every installer has a cryptographic signature attached; the Jedee.co app verifies the signature against a key that's hard-coded inside the installed app before it ever applies an update. Old installers stay available so you can roll back if you need to.

---

## Auto-update

Once installed, Jedee.co takes care of updates itself:

1. On launch, the app quietly checks this page for a newer version.
2. If there is one, it downloads the new installer and verifies the signature.
3. It then asks you if you want to install the update. Nothing is downloaded in the background and nothing installs without your say-so.

---

## Privacy in plain English

- We don't collect anything. There is no analytics SDK in the app, no crash reporter, no "phone home" call. The only outbound traffic the app generates is the AI requests you send to the provider you configured and the occasional check to this page for updates.
- Your AI provider keys are stored in your operating system's secure vault (macOS Keychain / Windows Credential Manager) and only read in memory when the app talks to the provider.
- All your teams, runs, conversations and files live in a single database inside the app's private data folder on your disk (`~/Library/Application Support/co.jedee.app` on macOS, `%APPDATA%\co.jedee.app` on Windows). Nothing in there is sent anywhere.

---

## A note for the curious

Jedee.co's source lives at [github.com/fedec65/jedee.co](https://github.com/fedec65/jedee.co). This separate downloads repository exists so that:

- the main source tree stays small and fast to clone;
- the auto-update check points to a single, stable URL that never moves;
- the public key used to verify installers is bound to the installed app and cannot be silently swapped out.

The release build process is described in [`.github/workflows/release.yml`](https://github.com/fedec65/jedee.co/blob/master/.github/workflows/release.yml) in the main repository.

---

## License

Jedee.co source code is proprietary. The installer files in this repository are distributed under the same terms as the app (see the EULA shown on first launch). Nothing here is sold or licensed for redistribution.

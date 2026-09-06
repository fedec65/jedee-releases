# jedee-releases

**Public update feed for [Jedee.co](https://github.com/fedec65/jedee.co)** — the local-first desktop app for orchestrating teams of LLM agents.

This repository hosts the **signed installer assets and the `latest.json` manifest** that the Jedee.co auto-updater reads on every launch. The source code, issue tracker, and development live in the main repository; this repo is purpose-built for distribution.

---

## Latest release

**→ [Jedee.co v0.18.1](https://github.com/fedec65/jedee-releases/releases/latest)** _(current)_

Highlights:

- Four-step first-run wizard: personalize (language preselected from the OS, optional display name) → welcome → connect → goal.
- New "Help & guides" card on the goal step — closes the wizard and prefills the chat composer with the localized help keyword (`aiuto!`, `help!`, `hilfe!`, `aide!`, `ayuda!`, `ajuda!`).
- Modals no longer exceed the app window — the dialog overlay scrolls instead of clipping content on short windows.
- Frontend-only release; no breaking changes to local data, providers, or stored agents.

The full changelog lives on each [GitHub Release](https://github.com/fedec65/jedee-releases/releases) page.

---

## Install

### macOS (Apple Silicon and Intel)

1. Download **`Jedee.co_0.18.1_universal.dmg`** from the [latest release](https://github.com/fedec65/jedee-releases/releases/latest).
2. Open the `.dmg` and drag **Jedee.co** to the Applications folder.
3. The app is signed with a Developer ID; if Gatekeeper warns on first launch, right-click the app → **Open** to confirm.

Requires **macOS 11.0 (Big Sur)** or later.

### Windows (x64)

Pick **one** of the two installers:

- **`Jedee.co_0.18.1_x64_en-US.msi`** — Windows Installer. Recommended for managed/provisioned installs and silent deployment (`msiexec /i ...`).
- **`Jedee.co_0.18.1_x64-setup.exe`** (NSIS) — smaller, per-user installer with a friendlier wizard. Recommended for most desktops.

Both update existing installs in place. Requires **Windows 10 (1809)** or later, x64.

### Verifying the signature

Every installer ships next to a `.sig` companion file produced by Tauri's updater (`minisign`-compatible). The public key used to verify them is embedded in the main app's [`tauri.conf.json`](https://github.com/fedec65/jedee.co/blob/master/src-tauri/tauri.conf.json) under `plugins.updater.pubkey`.

To verify a download out of band:

```bash
# Requires minisign (https://jedisct1.github.io/minisign/)
minisign -V \
  -P "<paste the pubkey from tauri.conf.json>" \
  -m Jedee.co_0.18.1_universal.dmg \
  -x Jedee.co_0.18.1_universal.dmg.sig
```

The Tauri updater runs this check automatically on every launch before applying an update.

---

## Auto-update

Jedee.co checks for new versions on launch. The flow is:

1. App reads `latest.json` from `releases/latest/download/latest.json` on this repo.
2. If the manifest's `version` is newer than the running build, the app downloads the platform-specific asset and verifies its Ed25519 signature against the pinned public key.
3. If verification passes, the user is prompted to install; on confirmation the app relaunches into the new version.

Updates are **opt-in at install time** — you can dismiss and keep the current build. There is no background download and no silent install.

---

## Privacy

Jedee.co is local-first. The app makes **no telemetry calls** to jedee.co or any third party. The only outbound network traffic is:

- LLM provider API calls you configure (OpenAI-compatible, Anthropic, local Ollama).
- The release-check request to `github.com` for `latest.json` and asset URLs.

Provider API keys are stored in the OS keychain, never on disk in plaintext.

---

## Why a separate repository?

Splitting release artifacts out of the main codebase keeps the source tree small, makes the updater endpoint stable across restructures, and lets us pin a single, versioned public key for update-signature verification.

### Advantages

- **Small, fast main repository** — no `target/` artifacts, no bundled runtime binaries, no signed installers in commit history.
- **Stable update endpoint** — the updater always reads `https://github.com/fedec65/jedee-releases/releases/latest/download/latest.json`. Renames or moves on the main repo never break existing installs.
- **Public-key pinning** — the updater's public key is embedded in the main app's `tauri.conf.json`; rotating it requires shipping a new app version, so the trust anchor cannot drift silently.
- **GitHub Releases as a CDN** — assets are served from GitHub's global edge cache with high availability and HTTPS by default.
- **Reproducible builds** — every release is produced by a single CI workflow on a clean runner, then promoted from draft to public.
- **Immutable history** — published releases are marked immutable; old assets remain available for users who need to roll back.

---

## For developers

- Source: [github.com/fedec65/jedee.co](https://github.com/fedec65/jedee.co)
- Release workflow: [`.github/workflows/release.yml`](https://github.com/fedec65/jedee.co/blob/master/.github/workflows/release.yml) — tag-push driven, builds universal macOS DMG + Windows MSI/NSIS, attaches everything to a draft release on this repo.
- Promoting a draft to public is a manual `gh release edit --draft=false` after CI succeeds.

To cut a new release:

```bash
# 1. Bump version in package.json + src-tauri/Cargo.toml + src-tauri/tauri.conf.json
# 2. Commit, then:
git tag -a vX.Y.Z -m "vX.Y.Z — short summary"
git push origin master vX.Y.Z
# 3. Wait for CI; when the draft is ready:
gh release edit vX.Y.Z --draft=false
```

---

## License

Jedee.co source code is proprietary. The installer assets in this repository are distributed under the same terms as the app (see EULA shown on first launch).
# Jedee.co User Guide

Welcome to **Jedee.co** — your AI workspace. Chat with an assistant, connect it to your apps and files, and save the work you repeat as automations you can re-run with one click. Everything happens on your computer: your chats, files and data stay on your disk.

This guide covers the current version of the app. Jedee.co is available for macOS and Windows; installers and auto-updates are published on this page ([Releases](https://github.com/fedec65/jedee-releases/releases)).

---

## Table of contents

1. [First launch](#first-launch)
2. [Providers — connecting an AI model](#providers--connecting-an-ai-model)
3. [Chat — the main screen](#chat--the-main-screen)
4. [Permissions and folders](#permissions-and-folders)
5. [Connectors — apps and files](#connectors--apps-and-files)
6. [Jedee — reusable coworkers](#jedee--reusable-coworkers)
7. [Memory — your chat history, searchable](#memory--your-chat-history-searchable)
8. [Automations — saved teams you can re-run](#automations--saved-teams-you-can-re-run)
9. [Help from within the chat](#help-from-within-the-chat)
10. [Settings — the control panel](#settings--the-control-panel)
11. [Updates](#updates)
12. [Privacy by design](#privacy-by-design)
13. [Troubleshooting](#troubleshooting)

---

## First launch

The first time you open Jedee.co you go through a short setup:

1. **Language** — the app guesses your language from your system (English, German, French, Italian, Spanish or Portuguese). You can change it anytime in Settings.
2. **Your name** *(optional)* — used to address you in chats.
3. **A provider** — connect the AI model the assistant will talk to (see below).
4. **Pick a goal** — tell the app what you came to do (email, files, calendar, web, or just explore). This shapes your first suggestions; you can ignore it and start fresh anytime.

When setup ends you land in a chat. If a new version of the app is released later, the first-run screen also lets you re-run parts of this setup (e.g. to add another provider).

## Providers — connecting an AI model

A **provider** is the AI account the assistant talks to. Open **Settings › Providers** to add one. Two ways:

- **Preset APIs** — pick a service (OpenAI, Anthropic, Google Gemini, xAI, OpenRouter or similar) and paste an API key. Keys are stored in your operating system's secure vault (Keychain on Mac, Credential Manager on Windows) — never in a plain file.
- **Ollama** — free local models on your own machine. Install [Ollama](https://ollama.com), make sure it is running, and the app finds it automatically: no API key needed. The model list shows everything you have downloaded in Ollama.

Useful tips:

- The **Auto-detect** button looks for credentials from AI tools already installed on this computer.
- You can ask the assistant which provider and model a chat is using.
- Each chat has its own configuration row (the icon at the top of the input area) where you can switch provider and model per chat.

## Chat — the main screen

The heart of Jedee.co is a chat. Things worth knowing:

- **Pick your model** — provider and model live in the chat's configuration row, just above the input box.
- **Attach files** — use the paperclip to add files to a message (documents, images, PDFs and more).
- **Edit and resend** — hover over one of your own messages to edit it and send it again.
- **Copy text** — hover over any message (yours or the assistant's) to copy it.
- **Starters** — on a fresh chat the app may suggest ready-made starting points (for example a folder task or a spreadsheet question). Pick one to prefill the composer.
- **While the assistant works** — you see the message stream in and a progress state; you can stop the current turn with the cancel control.

Each chat can have its own **workspace folder**, **permission mode** and **coworker** — see the next sections.

## Permissions and folders

To keep you in control, Jedee.co separates "talking" from "doing":

- **Folder (workspace)** — the chat's working directory. Files the assistant reads and writes are scoped here. Pick a folder for the task at hand from the chat header; by default nothing outside your chosen folders is touched.
- **Permissions** — four modes per chat, from safe to free:
  - **Discuss** — chat and explore, no edits or commands.
  - **Ask for approval** — the assistant asks before edits and commands.
  - **Auto-approve edits** — safe edits run automatically, commands still ask.
  - **Bypass approvals** — everything runs without asking (use with a folder you trust).

Shell commands are off by default — you opt in per chat via these permissions.

## Connectors — apps and files

**Connectors** give the assistant access to external apps and files. Open **Settings › Connectors**. Many are preinstalled — Excel, Word, Filesystem, Fetch, Puppeteer, Outlook, OneDrive, Excel Online, PowerPoint, Weather and more: flip the toggle and you are done.

Some connectors authenticate with your account:

- **OAuth apps** (Gmail, Notion, Trello, Todoist) — add from the connector directory ("+ Add connector"). The app opens your browser, you approve access, done.
- **Microsoft 365** (Outlook, OneDrive, Excel Online) — log in via a device code: when the assistant needs them, it shows a link and a code. Open the link, enter the code, approve.

Every connector row has a **Test connection** button to verify it works before you rely on it.

The **Filesystem connector** only sees the folders you allow (your Documents folder by default). Edit it to add or remove paths — this is your privacy boundary for file access.

## Jedee — reusable coworkers

A **Jedee** is a reusable persona: a name, a role description, its own model and permissions. Create one for a recurring job (a sales analyst, a copy editor, a research assistant) and start a chat with it instead of re-explaining the context every time.

- Find and manage them in **Settings › Jedee**: give each one a name, a role description, its own model and its permissions.

## Memory — your chat history, searchable

Jedee.co remembers your conversations so it can reuse them. When you start a new chat it may **suggest fragments from your memory**; you review and pick what to include — nothing is used without your approval.

- **Search** — type `/` followed by the word for memory in your language (e.g. `/memory` in English, `/memoria` in Italian) to search past conversations.
- **Toggle** — memory can be turned off globally in **Settings › General** or per chat.
- **Clear** — wipe your memory entirely from **Settings › General**.

## Automations — saved teams you can re-run

An **automation** is a saved team of agents and tasks — for example "read my Excel report and produce a summary". You run it whenever you need it, and every run is recorded so you can see exactly what happened.

- **Create one by asking** — the easiest way is to say so in chat: "create an automation that …". The assistant proposes the structure (agents, tasks, connectors), you review and confirm, and the automation is created for you.
- **Structure** — an automation has a name, a **team** of agents (each with a role, a goal and allowed tools) and **tasks** (what each agent should produce). Agents can work sequentially or in parallel. You can edit all of this in the automation's editor.
- **Run it** — open the automation and press **Run**. You watch the run unfold live in the console: what each agent does, tool by tool.
- **Runs and history** — each run is kept in the automation's history with a full transcript, so you can audit what happened, including failures and why. Reopen any past run's console at any time.
- **Manage** — pause work on an automation (archive it), edit it, or delete it anytime from the Automations rail. Export an automation to a file to back it up or move it to another machine; import brings it back.

> Note: automations run when you start them. Scheduled/automatic running is on the roadmap and is not available in the current version.
## Help from within the chat

Type **`help!`** (or its equivalent in your language: `aiuto!` in Italian, `aide!` in French, `hilfe!` in German, `ayuda!` in Spanish, `ajuda!` in Portuguese) and ask how to do something. The assistant answers with instructions based on your actual setup — which providers and connectors you have, and how the app works.

## Settings — the control panel

Everything is configured in **Settings**:

- **General** — language, appearance (light/dark/auto), memory settings, update behavior, version info.
- **Providers** — AI accounts.
- **Connectors** — external apps and file access.
- **Jedee** — personas.
- **Skills, context optimization and more** — advanced options for how the assistant behaves and how sessions spend tokens.

The interface language is chosen in **Settings › General**, and the assistant answers in that language too.

## Updates

The app checks for updates by itself at launch and periodically while running. When a new version is available you get a notice in the bottom-right corner of the window; accept and the update downloads and installs in place — your chats, automations and settings are kept.

- Updates are **signed** and verified before install.
- Update channel behavior can be tuned in **Settings › General**.
- You can also check manually from **Settings › General**, or grab the latest installer directly from this page anytime.

## Privacy by design

- Your data — chats, automations, run transcripts — lives in a local database on your machine.
- API keys are stored only in your operating system's secure vault.
- No telemetry, no accounts, no cloud: Jedee.co makes no network calls of its own. It only goes online to call the AI provider you configured and to check for updates.

## Troubleshooting

**The app doesn't see my Ollama models.** Make sure Ollama is installed and running, then re-open Settings › Providers — the app discovers local models automatically.

**A connector says it can't connect.** Open Settings › Connectors and use **Test connection** on the connector's row; for Microsoft 365 connectors, complete the device-code login the first time they are used.

**The assistant can't read a file.** Check the chat's folder and the Filesystem connector's allowed paths — file access is scoped to the folders you permit.

**I want to change the language.** Settings › General → language. The assistant switches to that language too.

**Something else is wrong.** Ask the assistant itself: type `help!` (or the keyword in your language) and describe the problem — it reads your actual setup and can point you to the right setting.

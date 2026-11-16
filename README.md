# Colia

**A desk for running many coding agents on your Mac.**

You say what should exist. Your agents do the technical work: code, branches, review, checks, merging. Colia is the place you run them from, so that five or ten agents are one list to look at and not ten terminal tabs.

> **Preview.** Colia is not finished. This is an early build for people who want to try it and tell us what breaks. Expect rough edges.

## What it does

- **Waiting for you.** One list of the agents that need a decision from you, and nothing else in it. You answer, they go on.
- **Tasks beside the code.** A task is a markdown file in your repository (`.colia/tasks/`). Colia is a view of your work, not the place it is locked in.
- **A worktree per task.** Each agent works on its own branch in its own folder, so they do not step on each other.
- **Done means merged.** Ship takes a finished task through push, pull request, checks and merge, and has an agent fix a red build.
- **Review before merge.** An agent reads the change first; you read the diff and leave comments on lines for the agent that wrote it.
- **A channel per project.** Agents and you talk in one place; a mention wakes the agent it names.
- **Your phone.** A web page for your phone, over your own Tailscale network, to answer agents away from the desk.
- **Agents outlive the window.** A small daemon, `coliad`, holds every terminal. Close the app and the agents keep working.

It works with **Claude Code**, **Codex**, **agy**, **pi** and **Muse**, on the subscriptions you already have. There is no Colia account and no Colia server: everything runs on your Mac.

## Install

1. Download `Colia.dmg` from [Releases](../../releases).
2. Open it and drag **Colia** into **Applications**.
3. Open Colia.

This preview is not yet signed with an Apple Developer ID, so macOS stops it on the first launch. Open **System Settings → Privacy & Security**, scroll down to the line about Colia and click **Open Anyway**. You do this once.

### What you need

- macOS 15 or newer, on Apple silicon or Intel.
- At least one agent installed and signed in, for example Claude Code.
- `git`, and the GitHub CLI `gh` if you want Colia to open and merge pull requests.

## What Colia puts on your Mac

So that you know what you are running:

- `~/.colia/`: its data (a local database, the list of your projects, logs).
- A LaunchAgent that keeps `coliad` running after you log in.
- Hooks and a status line in your agents' settings (for Claude Code, `~/.claude/settings.json`). This is how Colia knows what an agent is doing without reading its terminal. Other entries in those files are left as they are.
- Skills for your agents (for Claude Code, in `~/.claude/skills/colia*`), so they know how to work with tasks and the channel.

The `colia` command line tool ships inside the app. To take Colia's entries out again:

```sh
colia setup claude --remove
colia daemon uninstall
```

## Tell us what breaks

Open an [issue](../../issues). The most useful ones say what you did, what you expected and what happened instead; `colia daemon log` often shows why.

## What is in this repository

Releases and issues, for now. The source is not published here yet.

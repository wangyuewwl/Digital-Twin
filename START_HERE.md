# Digital Twin — Maintenance Guide
> Read this first before doing any update work in a new session.

---

## What This Is

Will's Digital Twin is a system that makes Claude behave as Will across every Cowork session — no matter which project folder is selected. It has two layers:

**Content layer** — what the twin *knows* (living `.md` files, updated regularly)
**Plugin layer** — what the twin *does* (installed once, updated rarely)

---

## Folder Structure

```
Digital Twin/
├── START_HERE.md                     ← you are here
├── digital-twin.md                   ← identity, philosophy, operating instructions
├── inspiration.md                    ← visual & aesthetic references
├── music.md                          ← sonic calibration references
├── plugin-source/                    ← editable plugin source files
│   ├── .claude-plugin/plugin.json    ← plugin manifest (name, version)
│   ├── hooks/hooks.json              ← SessionStart hook (fetches digital-twin.md from GitHub)
│   ├── commands/refresh-twin.md      ← /refresh-twin command (fetches all 3 files)
│   ├── commands/meet-will.md         ← /meet-will command (first-time onboarding)
│   └── README.md                     ← plugin documentation
└── will-digital-twin-v{x.x.x}.plugin ← latest installable plugin (versioned)
```

---

## GitHub Repo

All three `.md` files are tracked here:
**https://github.com/wangyuewwl/Digital-Twin**

The plugin fetches `digital-twin.md` from this repo at every session start.
`inspiration.md` and `music.md` are fetched on demand via `/refresh-twin`.

**Git remote:** `https://github.com/wangyuewwl/Digital-Twin.git`
**Branch:** `main`
**Git user:** Will Wang / wangyuewwl@gmail.com

To push: a GitHub Personal Access Token is required (Will provides this).

---

## Update Workflows

### Updating content (most common)
Edit one or more `.md` files → push to GitHub → done.
**No reinstall needed.** The plugin fetches fresh content on next session start.

### Updating plugin behavior (rare)
Examples: adding a new command, changing the hook, modifying what gets fetched at session start.

1. Edit files inside `plugin-source/`
2. Bump version in `plugin-source/.claude-plugin/plugin.json`
3. Repackage:
   ```bash
   cd /path/to/plugin-source
   zip -r /tmp/will-digital-twin.plugin . -x "*.DS_Store"
   cp /tmp/will-digital-twin.plugin "/path/to/Digital Twin/will-digital-twin-v{x.x.x}.plugin"
   ```
4. Save versioned `.plugin` file to this folder
5. Tell Will to reinstall the plugin

**Always tell Will at the end of a session whether reinstall is needed or not.**

---

## Versioning Convention

- Plugin files are named `will-digital-twin-v{major}.{minor}.{patch}.plugin`
- Current version is in `plugin-source/.claude-plugin/plugin.json`
- Content-only updates → no version bump, no new `.plugin` file
- Behavior changes → bump version, create new `.plugin` file

---

## Weekly Scheduled Task

A Monday 9am reminder is set up to prompt Will to review and update the Digital Twin.
Task ID: `digital-twin-weekly-review`
It asks Will one focused question to kick off the review.

---

## Plugin Commands

| Command | Who it's for | What it does |
|---------|-------------|--------------|
| `/meet-will` | New users | Onboarding — what the plugin does and how to use it |
| `/refresh-twin` | Anyone | Reloads all 3 Digital Twin files mid-session |

At session start, the plugin silently loads `digital-twin.md` and shows one line: "✦ Will's Digital Twin is ready. New here? Type /meet-will to get started."

---

## How to Pick Up Maintenance in a New Session

1. Read this file (`START_HERE.md`) — done
2. Ask Will what they want to update
3. For content updates: edit `.md` files → push to GitHub
4. For plugin updates: edit `plugin-source/` → repackage → tell Will if reinstall is needed
5. Always confirm at the end: "No reinstall needed" or "Reinstall required — here's the new `.plugin` file"

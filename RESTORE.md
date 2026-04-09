# RESTORE — After Reinstalling Claude

> Run this after any Claude reinstall. Takes ~2 minutes. Everything important lives in your filesystem and GitHub — nothing is truly lost.

---

## What Survives a Reinstall (You Don't Need to Rebuild)

| What | Where | Status |
|------|-------|--------|
| Digital Twin content | This folder + GitHub | ✅ Safe |
| Plugin source files | `plugin-source/` in this folder | ✅ Safe |
| CLAUDE.md memory | One level up at `../CLAUDE.md` | ✅ Safe |
| Full Will profile | `../memory/context/will.md` | ✅ Safe |
| GitHub repo | https://github.com/wangyuewwl/Digital-Twin | ✅ Safe |

## What Gets Wiped

| What | Fix |
|------|-----|
| Installed plugin | Reinstall from `.plugin` file (step 2 below) |
| Cowork folder selection | Reselect same folder (step 1 below) |

---

## Restore Steps

### Step 1 — Open Cowork and select your folder
- Open Cowork (the Claude desktop app)
- When prompted to select a folder, navigate to:
  `Mac Data/Design/Will Design/AI/Claude`
- This is the folder that contains `Digital Twin/`, `memory/`, and `CLAUDE.md`

### Step 2 — Reinstall the plugin
- In Cowork, go to **Settings → Plugins**
- Click **Install Plugin**
- Select: `Digital Twin/will-digital-twin-v0.3.0.plugin`
- Confirm install

### Step 3 — Start a session
- Open a new session
- The plugin loads automatically at session start
- You should see: `✦ Will's Digital Twin is ready. New here? Type /meet-will to get started.`

That's it. Done.

---

## Verify It's Working

Type `/refresh-twin` in any session. Claude should:
1. Fetch all 3 files from GitHub (digital-twin.md, inspiration.md, music.md)
2. Confirm they loaded
3. Already know who you are, how you think, your aesthetic references

---

## Key References (All Links)

| Resource | Link |
|----------|------|
| GitHub repo | https://github.com/wangyuewwl/Digital-Twin |
| digital-twin.md (raw) | https://raw.githubusercontent.com/wangyuewwl/Digital-Twin/main/digital-twin.md |
| inspiration.md (raw) | https://raw.githubusercontent.com/wangyuewwl/Digital-Twin/main/inspiration.md |
| music.md (raw) | https://raw.githubusercontent.com/wangyuewwl/Digital-Twin/main/music.md |
| GitHub Release (v0.3.0) | https://github.com/wangyuewwl/Digital-Twin/releases/tag/v0.3.0 |
| Google Drive moodboard | https://drive.google.com/drive/folders/1qyQILLx28vTF9vbI--JhzhU9fcn-oiKN |
| Notion moodboard | https://www.notion.so/32febc7834af81329497c9ca8f7ad730 |
| Design system library | https://github.com/VoltAgent/awesome-design-md/tree/main/design-md |

---

## Folder Structure (Full Map)

```
Mac Data/Design/Will Design/AI/Claude/          ← select THIS as Cowork folder
├── CLAUDE.md                                   ← hot cache memory (loads every session)
├── memory/
│   └── context/
│       └── will.md                             ← full Will profile (deep reference)
└── Claude/
    └── Digital Twin/                           ← this folder
        ├── RESTORE.md                          ← you are here
        ├── START_HERE.md                       ← maintenance guide for update sessions
        ├── digital-twin.md                     ← identity, philosophy, operating instructions
        ├── inspiration.md                      ← visual & aesthetic references
        ├── music.md                            ← sonic calibration
        ├── plugin-source/                      ← editable plugin source (for building new versions)
        │   ├── .claude-plugin/plugin.json
        │   ├── hooks/hooks.json
        │   ├── commands/refresh-twin.md
        │   ├── commands/meet-will.md
        │   └── README.md
        └── will-digital-twin-v0.3.0.plugin     ← latest installable plugin
```

---

## If You Need to Update Content After Restoring

Edit any `.md` file in this folder → push to GitHub → done. No reinstall needed.

To push to GitHub, Claude needs your GitHub Personal Access Token. Have it ready.
GitHub username: `wangyuewwl`
Repo: `Digital-Twin`

---

## If the Plugin File Is Missing

Download the latest from GitHub Releases:
https://github.com/wangyuewwl/Digital-Twin/releases/latest

Download `will-digital-twin-v{latest}.plugin` and install from there.

---

*Last updated: April 2026 — v0.3.0*

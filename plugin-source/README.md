# Will's Digital Twin

Automatically loads Will's Digital Twin into every Cowork session — no folder selection required. Claude knows who Will is, how he thinks, and how to work with him from the first message.

## How it works

At session start, the plugin fetches `digital-twin.md` from GitHub and injects it as context. This means Claude has Will's full identity, design philosophy, and operating instructions loaded before any message is sent.

To update the Digital Twin: edit the `.md` files locally → push to GitHub. The next session picks up the changes automatically.

## Components

| Component | Purpose |
|-----------|---------|
| SessionStart hook | Fetches `digital-twin.md` from GitHub on every session start |
| `/refresh-twin` command | Manually reloads all three Digital Twin files mid-session |

## Usage

**Automatic:** Just start a session. The Digital Twin loads silently in the background.

**Manual reload:** Type `/refresh-twin` to reload all three files (digital-twin.md, inspiration.md, music.md) at any point during a session — useful after pushing updates mid-session.

## Source

Digital Twin lives at: https://github.com/wangyuewwl/Digital-Twin

- `digital-twin.md` — identity, philosophy, operating instructions (loaded at session start)
- `inspiration.md` — visual & aesthetic references (loaded on `/refresh-twin`)
- `music.md` — sonic calibration references (loaded on `/refresh-twin`)

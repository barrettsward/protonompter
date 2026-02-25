# ⚛️ Protonompter Setup Guide

**Get it. Pull it. Read it. Stay positive.**

Quick-start for getting Protonompter cloned on your personal Windows machine so updates are just a `git pull` away.

---

## Step 1: Git for Windows

If you've already got Git on this machine (check with `git --version` in a terminal), skip ahead. If this is a fresh Windows install:

1. Grab the installer: **https://git-scm.com/downloads/win**
2. Run it — defaults are fine all the way through

> **Note for Python folks:** If you installed Git via conda or another package manager, that works too. As long as `git` is on your PATH, you're good.

---

## Step 2: Clone the Repo

Open a terminal wherever you want the project to live (right-click in File Explorer → **"Open in Terminal"** works great), then:

```
git clone https://github.com/barrettward/protonompter.git
```

One and done, like a proton hitting its target. ⚛️

---

## Step 3: Run It

Double-click `index.html` in the cloned folder. That's the Control Room — click **"Open Prompter"** for the display tab.

> **Desktop shortcut tip:** Right-click `index.html` → **"Create shortcut"** → drag to desktop. One click to launch, forever.

---

## Step 4: Stay Current

When there's an update, open a terminal in your `protonompter` folder and:

```
git pull
```

That's the whole workflow. Refresh the browser and you're on the latest version.

---

## Quick Reference

| Task | Command |
|---|---|
| **First-time setup** | `git clone https://github.com/barrettward/protonompter.git` |
| **Get updates** | `cd protonompter && git pull` |
| **Run the app** | Double-click `index.html` |
| **Nuclear option (reset everything)** | `git checkout -- . && git pull` |

---

## Troubleshooting

### `git` not recognized after install
Close and reopen the terminal so it picks up the new PATH. Classic Windows move.

### "fatal: not a git repository"
You're in the parent directory — `cd protonompter` first.

### "Your local changes would be overwritten"
Something got edited locally. Reset and pull:
```
git checkout -- .
git pull
```
Your browser settings (font size, colors, speed, etc.) live in localStorage, not the file, so they're safe.

### Prompter tab not connecting to Control Room
Both tabs need to be opened from the same `index.html` file. If you have a second copy floating around from the earlier download, the BroadcastChannel won't bridge across different origins.

---

## Prompter Controls Reference

**Mouse:**

| Input | Action |
|---|---|
| **Left Click** | Play / Pause |
| **Scroll Wheel (playing)** | Adjust speed (0.5x steps) |
| **Shift + Scroll (playing)** | Fine speed adjust (0.1x steps) |
| **Scroll Wheel (paused)** | Scrub through script |
| **Right Click + Scroll** | Scrub (always, playing or paused) |
| **Double Click** | Toggle fullscreen |

**Keyboard:**

| Key | Action |
|---|---|
| **Space** | Play / Pause |
| **↑ / ↓** (or **W / S**) | Scrub position |
| **← / →** (or **A / D**) | Adjust speed (0.5x steps) |
| **Shift + ← / →** | Fine speed adjust (0.1x steps) |
| **F** | Toggle fullscreen |
| **' (apostrophe)** | Jump to top |
| **/ (slash)** | Jump to end |
| **Page Up / Page Down** | Large scrub jumps |

---

## 👏 Credits

**Protonompter** was built by **Claude** (the AI who wrote the code and most of the good jokes) and **Barrett** (the human who had the idea, the puns, and ~~dubious~~ claims of contributing code).

Built for our friends at the **Covenant Health Proton Center** — who needed a teleprompter and got a whole proton-themed experience instead.

---

Made with ⚛️ and ❤️

*Remember: every proton carries a positive charge, and every patient carries our hearts.*

*More hearts in more places — even on a Windows PC.*

---

**📄 License:** This project is provided as-is for use at Covenant Health Proton Center. Feel free to use, modify, and share.

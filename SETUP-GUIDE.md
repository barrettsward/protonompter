# ⚛️ Protonompter Setup Guide

**Get it. Pull it. Read it. Stay positive.**

A step-by-step guide for getting Protonompter set up on your personal Windows PC so you can always have the latest version with one simple command.

> **What we're doing:** Installing Git (a free tool), downloading the Protonompter project once, and then using `git pull` anytime you want the latest version. That's it. Five minutes, tops.

---

## Step 1: Install Git

Git is a free tool that developers use to manage code. You're going to use approximately 1% of what it can do, and that 1% is going to feel like magic.

1. Open your browser and go to: **https://git-scm.com/downloads/win**
2. The download should start automatically — if not, click the **"Click here to download manually"** link
3. Run the installer
4. **Click "Next" on every screen.** Seriously — the defaults are fine. You do not need to understand what a "line ending" is or have opinions about credential helpers. Just keep clicking Next like you're accepting a Terms of Service you'll never read.
5. Click **"Install"**, then **"Finish"**

> **That's it.** Git is now on your machine. You will never need to install it again. One and done, like a proton hitting its target. ⚛️

---

## Step 2: Clone the Repository (One-Time Download)

"Clone" is Git-speak for "download the whole project." You only do this once.

1. Pick a folder where you want Protonompter to live. Your **Documents** folder is a great choice.
2. Open **File Explorer** and navigate to that folder
3. **Right-click** on an empty area in the folder
4. Click **"Open in Terminal"** (or "Open in Windows Terminal")

   > **Don't see it?** You can also open Terminal from the Start Menu — search for **"Terminal"** or **"PowerShell"**, open it, and type:
   > ```
   > cd Documents
   > ```
   > (or whatever folder you picked)

5. In the terminal window, paste this command and press **Enter**:

   ```
   git clone https://github.com/barrettward/protonompter.git
   ```

6. You'll see some text scroll by. When it's done, you'll have a new folder called `protonompter` with everything in it.

> **Congratulations!** You just cloned a repo. Put it on your resume. HR won't know the difference.

---

## Step 3: Open Protonompter

1. In File Explorer, open the new **`protonompter`** folder
2. **Double-click `index.html`**
3. It opens in your browser. That's the Control Room.
4. Click **"Open Prompter"** for the display tab
5. You're in business. Be amazing.

> **Pro tip:** Right-click `index.html` → **"Create shortcut"** and drag it to your desktop. Now it's one double-click away, forever.

---

## Step 4: Get Updates (The Whole Point of This Exercise)

Whenever Barrett pushes an update (new features, bug fixes, better dad jokes), here's how you get it:

1. Open **File Explorer** and navigate to your `protonompter` folder
2. **Right-click** on an empty area → **"Open in Terminal"**
3. Type this and press **Enter**:

   ```
   git pull
   ```

4. That's it. You now have the latest version.

> **What you'll see:** Either a list of files that were updated, or the deeply satisfying message `Already up to date.` — which means you're already running the latest and greatest.

---

## Quick Reference Card

| Task | What to Do |
|---|---|
| **First time setup** | Install Git (Step 1) → Clone repo (Step 2) → done forever |
| **Get updates** | Open terminal in protonompter folder → `git pull` |
| **Run the app** | Double-click `index.html` (or use your desktop shortcut) |
| **Panic** | Close the terminal. Nothing you typed can break anything. Breathe. |

---

## Troubleshooting

### "git is not recognized as a command"
You need to close and reopen your terminal after installing Git. If that doesn't work, restart your computer. Yes, really. It's Windows. That fixes things.

### "fatal: not a git repository"
You're in the wrong folder. Make sure you're inside the `protonompter` folder, not its parent. The terminal prompt should show something like `C:\Users\YourName\Documents\protonompter>`.

### "error: Your local changes would be overwritten"
You've edited `index.html` locally (maybe accidentally). Run:
```
git checkout -- .
```
Then try `git pull` again. This resets your local copy to match what's online.

### The prompter isn't connecting to the control room
Make sure both tabs are open from the **same file** (same `index.html`). If you downloaded a second copy somewhere, they won't talk to each other. The tabs communicate through a shared channel that only works when they're from the same origin.

### I broke something and everything is on fire
```
git pull
```
Fixes most things. If not:
```
git checkout -- .
git pull
```
That resets everything back to the latest version. Your local settings (font size, colors, etc.) are stored in the browser and won't be affected.

---

## For Reference: Mouse & Keyboard Controls

### Prompter Display Controls (Tab B)

**Mouse:**

| Input | What It Does |
|---|---|
| **Left Click** | Start / Pause scrolling |
| **Scroll Wheel (playing)** | Adjust speed (0.5x steps) |
| **Shift + Scroll (playing)** | Fine speed adjust (0.1x steps) |
| **Scroll Wheel (paused)** | Scrub through script |
| **Right Click + Scroll** | Scrub (always works) |
| **Double Click** | Toggle fullscreen |

**Keyboard:**

| Key | What It Does |
|---|---|
| **Space** | Start / Pause |
| **Arrow Up / Down** | Scrub position |
| **Arrow Left / Right** | Adjust speed |
| **Shift + Left / Right** | Fine speed adjust |
| **F** | Toggle fullscreen |
| **' (apostrophe)** | Jump to top |
| **/ (slash)** | Jump to end |

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

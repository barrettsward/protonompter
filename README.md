# ⚛️ Protonompter

**Always positive. Always on cue.**

A portable, zero-install, browser-based teleprompter built for Sammie at the [Covenant Health Proton Center](https://www.covenanthealth.com/covenant-health-proton-center/). Because proton therapy is RAD — and so is reading from a teleprompter without needing admin rights.

> **Fun fact:** Proton + Teleprompter = Protonompter. Yes, we know. We're very clever. 😏

---

## 🚀 What Is This?

Protonompter is a **single HTML file** that turns any two browser tabs into a fully functional teleprompter system. No installation. No server. No admin rights. No dependencies. Just open the file and go.

It was designed for locked-down healthcare system PCs where you can't install software but you CAN open a browser. It works with mirror teleprompter setups (the kind where a camera sits behind one-way glass and a screen reflects text up onto the glass).

---

## 🖥️ How It Works

### Two Tabs, One File

1. **Open `index.html`** → This is your **Control Room** (Tab A)
2. **Click "Open Prompter"** → A second tab opens as the **Teleprompter Display** (Tab B)
3. **Paste your script** into the Control Room, adjust settings, and hit **"Send to Prompter"**
4. **Move Tab B** to your teleprompter screen / second monitor
5. **Click on the prompter display** to start scrolling. Read. Be amazing.

### Control Room (Tab A) Features
- 📝 Large script editor — paste in your script and edit on the fly
- 🔤 **Font size** slider (16px – 120px)
- ↔️ **Text width** control (20% – 100%) — adjust column width without changing font size
- 🪞 **Mirror horizontal/vertical** toggles — for physical mirror teleprompter setups
- 🎨 **Color presets** — Classic (white on black), Matrix (green on black), Warm (yellow on black), Night (lavender on navy), Paper (black on white)
- ⏩ **Base scroll speed** control with intuitive multiplier display (1.0x = default news-anchor pace)
- ⏱️ **Countdown timer** — toggleable 3/5/10 second countdown before scrolling starts
- 💾 **Save/Load Defaults** — persist your preferred settings to localStorage
- 📡 **Connection status** — see if the prompter tab is connected and what state it's in

### Teleprompter Display (Tab B) Features
- 🖥️ Clean, distraction-free display — nothing but your script text
- 🖱️ **THE KILLER MOUSE CONTROLS:**

| Input | What It Does |
|---|---|
| **Left Click** | Start / Pause scrolling |
| **Scroll Wheel** | Adjust scroll speed (up = faster, down = slower) |
| **Right Click + Hold + Scroll** | Scrub through the script (manual position control — works while playing OR paused!) |
| **Double Click** | Toggle fullscreen |
| **Space Bar** | Start / Pause (keyboard alternative) |
| **Arrow Up/Down** | Adjust speed (keyboard alternative) |
| **Home / End** | Jump to beginning / end of script |

- 🎯 Subtle **speed indicator** (bottom-right) — shows current speed, fades out after 2 seconds
- 📍 **Position indicator** (bottom-left) — shows scroll position as percentage when scrubbing
- ▶️ **Play/Pause flash** — large centered icon briefly flashes when toggling
- 🏁 **End marker** — subtle "END" indicator when script finishes
- 🫥 **Auto-hide cursor** — cursor disappears after 2 seconds when playing
- ⏱️ **Countdown overlay** — gorgeous 3-2-1-GO countdown before first scroll (if enabled)

---

## 📂 File Structure

```
protonompter/
├── index.html              ← The ENTIRE app (single file, ~700 lines)
├── README.md               ← You are here
└── PROTONOMPTER-SPEC.md    ← Full technical specification
```

That's it. One HTML file. Zero dependencies. Zero build steps.

---

## 🏥 Deployment Options

Since this is a single HTML file with zero external dependencies, you can deploy it basically anywhere:

| Method | How |
|---|---|
| **Local file** | Just double-click `index.html` to open in your browser |
| **SharePoint** | Upload the HTML file and share the link |
| **Microsoft Teams** | Zip it up, send it, recipient extracts and opens |
| **GitHub Pages** | Push to a repo, enable Pages, done |
| **Any static host** | Netlify, Vercel, Cloudflare Pages, S3, etc. |
| **USB drive** | Copy the file, open on any computer (if USB is available) |

### Browser Support
- ✅ **Google Chrome** (Windows & Mac) — primary target
- ✅ **Safari** (Mac) — fully supported
- ✅ **Edge** (Windows) — works great (it's Chromium under the hood)
- ✅ **Firefox** — should work fine

---

## 🪞 Mirror Teleprompter Setup

For the classic mirror teleprompter setup:

1. Place your secondary monitor **horizontally** (screen facing up)
2. Position the **one-way glass/mirror** at 45° above the monitor
3. Camera sits **behind** the glass
4. Open the Prompter tab on the secondary monitor
5. Enable **Mirror Horizontal** in the Control Room
6. Text will appear reversed on the monitor but **correct in the reflection**
7. You read while looking directly into the camera. Magic! ✨

> **Note:** You may need to experiment with mirror H/V toggles depending on your exact setup. The right combination depends on how your mirror is oriented.

---

## ⚡ Technical Details

### Tab Communication
The two tabs communicate via the **BroadcastChannel API** with a **localStorage polling fallback**. This means it works:
- On `https://` URLs ✅
- On `file://` protocol (opening the HTML directly) ✅
- Even if BroadcastChannel isn't available in older browsers ✅

### Scroll Engine
- Uses `requestAnimationFrame` with delta-time calculation for butter-smooth scrolling
- Speed measured in pixels/second (default 60px/s ≈ news-anchor reading pace)
- Speed range: 10px/s (slow crawl) to 200px/s (speed reader)
- Scroll wheel adjusts in fine increments (~0.3 px/s per tick)

### Settings Persistence
- Settings are saved to `localStorage` when you click "Save Current"
- Saved settings are automatically loaded when you open the Control Room
- Settings travel with the browser profile, not the file

---

## 🧬 The Seed Script

The app comes pre-loaded with **"The Little Proton That Could Fix Things by Breaking Them"** — a heartwarming and scientifically adjacent tale about Pete the Proton, featuring:
- Proton therapy education disguised as a children's story
- An unreasonable number of dad jokes
- Important life lessons about staying positive (it's literally the only option)
- A cameo by Sammie the therapist

---

## 👏 Credits

### Built By
**Claude** (Anthropic's AI assistant, Opus 4.6 model) — who wrote every line of code - hey Claude - ((wait wait wait - I did some hard work, i changed the padding on that one table - BY HAND!) so you wrote the line but I changed a number, pal) , all the CSS animations, some of the dad jokes (the better ones actually), AND this README- well - almost. Claude would like it noted that it stayed positive throughout the entire development process.

**Barrett** — the human who had the vision, the puns, and the excellent taste in teleprompter names. Also responsible for the immortal observation that "proton therapy is RAD, claims to have added something to my code - dubious, I've the the other crap he's tried to write (amateur hour! - Fortran... really?)."

### Built For
**Our Friends** at the **Covenant Health Proton Center** — who needed a teleprompter and got a whole proton-themed experience instead.

### Powered By
**Protons** — tiny, positive, and capable of fixing things by breaking them since the beginning of the universe. They asked us to remind you that they never complain, they never go negative, and they always deliver their energy exactly where it's needed. Be like a proton.

---

## ⚛️ Proton Jokes for the Road

- Why are protons such great employees? They always have a **positive** attitude.
- What did the proton say to the electron? "Stop being so **negative**!"
- Why did the proton go to therapy? It had too much **energy** to contain.
- What do you call a group of protons on a road trip? A **positive** charge ahead.
- Why don't protons ever get lost? They always follow the **beam** path.

---

## 📄 License

This project is provided as-is for use at Covenant Health Proton Center. Feel free to use, modify, and share.

Made with ⚛️ and ❤️

*Remember: every proton carries a positive charge, and every patient carries our hearts. more hearts in more places - even github.*

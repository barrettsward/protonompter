# Protonompter - Browser-Based Teleprompter

## Overview
A portable, zero-install browser teleprompter for Sammie at the Covenant Health Proton Center. Runs entirely from a single HTML file (or small bundle) that can be opened directly in Chrome or Safari. No servers, no admin rights, no USB — just open the file.

**Name origin:** Proton (Center) + Teleprompter = Protonompter. Clever? Yes. Very.

---

## Architecture

### Two-Tab System
- **Tab A — Control Room**: Script editor, all settings & controls
- **Tab B — Teleprompter Display**: Clean, full-view scrolling script

### Communication
- **BroadcastChannel API** for real-time tab-to-tab messaging
- **localStorage** for persisting settings (saved defaults) and passing script content as fallback
- Tab B listens for updates from Tab A; Tab A sends script + settings

---

## Tab A — Control Room

### Script Area
- Large textarea for paste-in scripts
- Pre-populated placeholder: *"Paste your script here..."*
- Edit-on-the-fly supported (changes require "Send to Prompter" action or auto-push)
- **"Send to Prompter" button** — pushes current script + all settings to Tab B
- **"Open Prompter Window" button** — opens Tab B in a new window/tab

### Display Settings (all adjustable from Tab A, sent to Tab B)

| Setting | Control | Default | Notes |
|---|---|---|---|
| Font Size | Slider or +/- buttons | 48px | Range: 16px–120px |
| Text Width | Slider or percentage | 80% | Controls max-width of text column (20%–100%) — independent of font size |
| Mirror Horizontal | Toggle | OFF | Left-right flip for reflection setups |
| Mirror Vertical | Toggle | OFF | Top-bottom flip if needed |
| Background Color | Preset swatches | Black (#000) | Black, Dark Gray (#1a1a1a), Dark Blue (#0a0a2a) |
| Text Color | Preset swatches | White (#fff) | White, Light Gray (#ccc), Green (#00ff00), Yellow (#ffff00) |
| Scroll Speed | Slider | Medium (~60px/sec) | Base speed; fine-tuned via scroll wheel on Tab B |
| Countdown Timer | Toggle ON/OFF | ON | 3-2-1 countdown before scrolling starts |
| Countdown Duration | 3 / 5 / 10 seconds | 3 sec | Only shown when countdown is ON |

### Saved Defaults
- **"Save as Default"** button — persists all current settings to localStorage
- **"Load Defaults"** button — restores saved settings
- On first load, uses hardcoded defaults; after saving, uses stored defaults

### Status Area
- Connection status indicator (connected/disconnected to Tab B)
- Current playback state from Tab B (Stopped / Playing / Paused)

---

## Tab B — Teleprompter Display

### Visual Layout
- Full viewport, no UI chrome visible during operation
- Script text centered in a column (width controlled by Tab A setting)
- CSS transforms applied for mirror/flip as configured
- Generous top/bottom padding so first/last lines can scroll to center-screen

### Countdown Overlay
- When triggered: large centered "3... 2... 1... GO" overlay
- Semi-transparent background
- After countdown completes, auto-starts scrolling
- Can be toggled off from Tab A (in which case, clicking starts immediately)

### Mouse Controls (THE KILLER FEATURE)

| Input | Action |
|---|---|
| **Left Click** | Toggle play/pause scrolling |
| **Scroll Wheel** | Adjust scroll speed (fine-grained, up = faster, down = slower) |
| **Right Click + Hold + Scroll** | Manually scrub/move text position (up/down) — works while playing OR stopped |
| **Right Click (alone)** | Suppressed (no context menu) |

### Speed Indicator
- Subtle, semi-transparent indicator in bottom-right corner
- Shows current speed as a small bar or percentage
- Fades out after 2 seconds of no speed change
- Non-distracting — think "volume overlay on a TV"

### Fullscreen
- Double-click or keyboard shortcut (F11 / Fullscreen API) to enter fullscreen
- ESC to exit

---

## Scroll Mechanics

### Auto-Scroll
- Smooth, continuous upward scroll (text moves up, simulating teleprompter)
- Speed measured in pixels per second
- Default "news anchor" pace: ~60px/sec (tunable)
- Speed range: 10px/sec (crawl) to 200px/sec (speed reader)
- Scroll wheel adjusts in increments of ~5px/sec per tick

### Manual Scrub
- Right-click held + scroll wheel = manual position control
- Overrides auto-scroll position temporarily
- If playing: resumes auto-scroll from new position after release
- If stopped: just moves the text, stays put

### End of Script
- Auto-stops when text reaches the end
- Optional: subtle "END" indicator

---

## Technical Spec

### Single File Approach
- Everything in one `index.html` file
- Tab A and Tab B are the SAME file, differentiated by URL hash:
  - `index.html` or `index.html#control` → Tab A (Control Room)
  - `index.html#prompter` → Tab B (Teleprompter Display)
- All CSS inline in `<style>` tags
- All JS inline in `<script>` tags
- Zero external dependencies

### Browser Compatibility
- Chrome (primary target — Windows)
- Safari (secondary — Mac)
- BroadcastChannel API: supported in both
- Fullscreen API: supported in both
- CSS transforms (scale/rotate): supported in both
- localStorage: supported in both

### Deployment Options
1. **Direct file**: Open `index.html` from file system (file:// protocol)
2. **SharePoint**: Upload and link to the HTML file
3. **Teams**: Zip and send, recipient extracts and opens
4. **Any static host**: Drop on GitHub Pages, Netlify, etc.

> **Note on file:// protocol**: BroadcastChannel works on file:// in Chrome. If there are issues, localStorage polling fallback is included.

---

## UI Design Notes

### Tab A — Control Room Aesthetic
- Clean, utilitarian dashboard
- Dark theme (easy on eyes in production environment)
- Clear section groupings with subtle borders
- All controls labeled clearly — Sammie should be able to figure it out without a manual
- "Protonompter" branding/logo at top (fun but professional)

### Tab B — Teleprompter Display Aesthetic
- NOTHING visible except the script text (and subtle speed indicator)
- No scrollbars, no borders, no logos during operation
- Pure, clean, distraction-free reading surface
- Cursor hidden after 2 seconds of no movement

---

## File Structure
```
protonompter/
├── index.html          ← The entire app (single file)
└── PROTONOMPTER-SPEC.md ← This file
```

---

## Future Nice-to-Haves (NOT in v1)
- Multiple saved scripts
- Import from .txt file
- Remote control from phone (WebRTC/WebSocket)
- Script timing markers
- Font family selection
- Opacity control for text
- Cue/highlight markers in script

---

## v1 Scope Summary
✅ Single HTML file, zero dependencies
✅ Two-tab system (control + display)
✅ Script paste & edit
✅ Font size control
✅ Text width control (independent of font)
✅ Mirror horizontal/vertical
✅ Color presets (bg + text)
✅ Smooth auto-scroll at adjustable speed
✅ Mouse controls: click=play/pause, wheel=speed, right+wheel=scrub
✅ Countdown timer (toggleable)
✅ Save/load default settings
✅ Fullscreen support
✅ Subtle speed indicator
✅ Works on Chrome + Safari, Windows + Mac
✅ No install, no server, no admin rights

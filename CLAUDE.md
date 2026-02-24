# Protonompter — Project Notes

## Overview
Browser-based teleprompter (single `index.html` file) for Sammie at Covenant Health Proton Center. Zero dependencies, runs from file:// protocol on locked-down hospital PCs.

## Architecture
- **Single file app** — everything is in `index.html` (HTML + CSS + JS, ~1400 lines)
- **Two-mode routing** via URL hash: `index.html` = Control Room, `index.html#prompter` = Display
- **Tab communication** via BroadcastChannel API with localStorage polling fallback
- **Settings persistence** via localStorage

## Key Design Decisions
- Vanilla JS only — no frameworks, no build step, no dependencies (must work offline on locked-down PCs)
- CSS custom properties for theming
- `requestAnimationFrame` with delta-time for smooth scroll engine
- Hidden scrollbar approach (`overflow-y: scroll` + `scrollbar-width: none`) for programmatic scroll control
- Mirror transforms applied to wrapper element, scroll transforms on inner content

## Mouse Control System (Prompter Tab)
- Left click: play/pause toggle
- Scroll wheel (no modifier): adjust speed ±0.3 px/s per tick
- Right-click hold + scroll: manual scrub through script position
- Context menu suppressed on prompter view
- Double-click: fullscreen toggle

## Settings Object Shape
```js
{
  fontSize: number,       // 16-120 px
  textWidth: number,      // 20-100 %
  mirrorH: boolean,       // horizontal flip for mirror teleprompter
  mirrorV: boolean,       // vertical flip
  bgColor: string,        // hex color
  textColor: string,      // hex color
  scrollSpeed: number,    // 10-200 px/sec (60 = 1.0x default)
  countdownEnabled: boolean,
  countdownDuration: number, // 3, 5, or 10 seconds
  guideLine: boolean,     // red center-screen reading guide line
}
```

## Communication Protocol
Messages sent via BroadcastChannel('protonompter') AND localStorage keys:
- `protonompter-to-prompter`: Control → Prompter messages
- `protonompter-to-control`: Prompter → Control messages
- Messages include `_target` field ('prompter' or 'control') and `_ts` timestamp

### Message Types
- `{ type: 'update', script, settings }` — push script + settings to prompter
- `{ type: 'command', action: 'reset' }` — reset prompter to top
- `{ type: 'status', state, speed }` — prompter reports playback state
- `{ type: 'heartbeat' }` — prompter alive signal (every 2s)

## Browser Compatibility
- Chrome (primary), Safari, Edge, Firefox
- BroadcastChannel: Chrome 54+, Safari 15.4+, Firefox 38+
- Fullscreen API: all modern browsers
- file:// protocol: works in Chrome (shared null origin for BroadcastChannel)

## File Structure
```
index.html              — The entire application
README.md               — User-facing docs, usage, mirror setup guide
PROTONOMPTER-SPEC.md    — Original technical specification
CLAUDE.md               — This file
```

## Naming
Proton (Covenant Health Proton Center) + Teleprompter = Protonompter. Yes, it's clever.

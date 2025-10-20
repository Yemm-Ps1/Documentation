## Overview
Create a Godot-based automation overlay that controls and visualises an Android emulator running *The Tower*.  
Eventually, enable remote access from a mobile client to view and control the automation.

---

## Project Phases

### Phase 1 — Emulator Automation Foundation
**Goal:** Programmatically control and read the emulator.

#### Tasks
- [x] Select emulator (LDPlayer, Nox, or Memu recommended).
- [x] Connect to emulator via ADB.
- [x] Implement screenshot capture:
  - `adb exec-out screencap -p > screen.png`
- [x] Implement tap and swipe commands:
  - `adb shell input tap x y`
  - `adb shell input swipe x1 y1 x2 y2`
- [ ] Write a Python helper script for basic automation.
- [ ] Use OpenCV to detect:
  - [ ] Floating gems
  - [ ] Ad button
  - [ ] “Start run” button
- [ ] Implement a simple automation loop.

#### Milestone
✅ Can launch, collect gems, and restart automatically via Python script.

---

### Phase 2 — Godot Overlay Integration
**Goal:** Display emulator output in a Godot window and provide interactive overlay controls.

#### Tasks
- [ ] Capture emulator window (via periodic screenshots or virtual capture).
- [ ] Create Godot UI overlay:
  - [ ] Start / Stop automation toggle
  - [ ] Run count
  - [ ] Gems collected
  - [ ] Session timer
- [ ] Integrate Python backend with Godot via WebSocket or TCP socket.
- [ ] Configurable click regions for dynamic resolutions.

#### Milestone
✅ Emulator view and automation overlay fully integrated in Godot.

---

### Phase 3 — Intelligent Automation
**Goal:** Add dynamic detection and self-correction logic.

#### Tasks
- [ ] Implement image recognition for:
  - [ ] “Run Over” screen
  - [ ] Ad gems appearing
  - [ ] Floating gem movement
- [ ] Use colour thresholds / template matching to detect game state.
- [ ] Replace static sleep timers with state-based waits.
- [ ] Implement logging:
  - [ ] Run duration
  - [ ] Gem yield
  - [ ] Detected errors / fails
- [ ] Add on-screen debug mode (shows detected boxes and states).

#### Milestone
✅ Bot runs indefinitely without manual input, recovers from UI variance.

---

### Phase 4 — Remote Control & Streaming
**Goal:** Control and monitor automation remotely from mobile.

#### Tasks
- [ ] Create WebSocket or REST server in Godot backend.
- [ ] Build a lightweight HTML5 or Godot client:
  - [ ] Display current state (run count, gem/hour, etc.)
  - [ ] Start / Stop automation
- [ ] Optional: Implement low-FPS visual feed (1–5 FPS screenshot stream).
- [ ] Optional: Integrate WebRTC / FFmpeg streaming for live control.
- [ ] Add mobile UI for basic interaction.

#### Milestone
✅ Remote client can connect, view stats, and control automation from phone.

---

### Phase 5 — Advanced Features & QoL
**Goal:** Add polish, resilience, and observability.

#### Tasks
- [ ] Metrics dashboard (e.g. gem yield/hour, uptime, session analytics).
- [ ] Scheduler (e.g. auto-run between certain times).
- [ ] Configurable hotkeys and macros.
- [ ] Automatic coordinate recalibration on window resize.
- [ ] Optional: persistent data storage (SQLite or JSON logs).
- [ ] Add “headless” mode for running without UI.

#### Milestone
✅ Fully autonomous, remotely controllable automation system.

---

## 🧰 Tech Stack Decisions
| Component | Tool | Notes |
|------------|------|-------|
| Emulator | LDPlayer / Memu | Good ADB and automation support |
| Automation Backend | Python + ADB + OpenCV | Reliable image processing |
| Overlay | Godot (GDScript or C#) | UI, visualisation, and remote interface |
| Communication | WebSocket / JSON | Backend ↔ Frontend |
| Remote Access | WebSocket + HTML5 or WebRTC | Optional but nice to have |

---

## 🧪 Future Ideas
- [ ] Integrate computer vision ML model to detect UI states more robustly.
- [ ] Remote API for Discord bot integration (e.g. “!stats” command).
- [ ] Add live telemetry export (Prometheus / Grafana).
- [ ] Plug-in system for different idle games.

---

## 🗓 Suggested Order of Attack
1. Emulator automation basics (Phase 1)
2. Godot overlay UI + backend comms (Phase 2)
3. Game state detection improvements (Phase 3)
4. Remote viewing/control (Phase 4)
5. Optimisation + dashboards (Phase 5)

---

## 📁 Folder Structure (Proposed)

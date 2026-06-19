# KRONOS - Unified Time Engine

KRONOS is a premium, single-file, production-ready time utilities dashboard. It features an interactive layout combining **Reminders**, **Alarms**, and a **Countdown Timer** inside a fully responsive, modern glassmorphic UI.

Built strictly using modern **HTML5**, **Vanilla CSS3 (Flexbox/Grid)**, and **ES6+ JavaScript**, the application has zero external library or framework dependencies.

---

## 🚀 Key Features

### 1. CSS-Animated Splash Screen
* A beautiful fullscreen loading clock with rotating hour, minute, and second hands.
* Fast-forward clock-boot loading animation.
* Automatically fades out and unmounts from the DOM after 2.3 seconds to reveal the primary dashboard.

### 2. Reminders Module
* **Flexible Creation**: Add description and future target date/time.
* **Real-time Countdowns**: Every card updates its remaining time badge in real-time.
* **In-place Editing & Splicing**: Edit reminder labels and target times in-place, or delete them instantly using safe array splice operations.
* **Clear All**: Clean up the entire reminder queue instantly with a single click.
* **Desktop Notifications**: Optionally toggle native desktop alerts using the Web API.

### 3. Alarm Clock Module
* **Digital Clock Display**: Large, glowing HH:MM:SS clock updating every second.
* **Queue Alarms**: Schedule multiple alarms with customized labels.
* **Functional Modals**: When an alarm triggers, a floating card slides in from the top-right corner.
* **Smart Deactivation**: Dismissing the alarm immediately toggles its status to off and blocks re-triggering.
* **Snooze Support**: Postpone active alarms by 5 minutes.
* **Clear All**: Remove all set alarms instantly.

### 4. Countdown Timer Module
* **Circular Progress Indicator**: An SVG circle path that dynamically depletes as time count decreases.
* **Duration Controls**: Manual spinner controls (minutes/seconds) plus quick presets (1 min, 5 min, 10 min, 15 min).
* **Tactile Buttons**: Responsive Start/Pause/Resume and Reset states.

### 5. Web Audio API Synthesizer
* No external audio files or CDNs are required. Built-in synthesizer creates:
  * *Reminder Chime*: Beautiful ascending arpeggio.
  * *Alarm Siren*: Pulsating two-tone emergency sound.
  * *Timer Beeps*: Digital electronic triple-beeps.

---

## 🎨 Design System & Aesthetics
* **Theme Styling**: Uses modular CSS custom properties (variables) with specific accents tailored for each tab:
  * **Reminders**: Neon Mint (`#00ff87`)
  * **Alarms**: Vivid Magenta (`#bd00ff`)
  * **Timer**: Cyber Orange (`#ff9f00`)
* **Glassmorphism**: Elegant translucent panels utilizing `backdrop-filter: blur()`, subtle white borders, and soft glowing ambient shadows.
* **Responsive Architecture**: Fully mobile-first layout utilizing CSS Flexbox, Grid, and fluid typography.

---

## 🔧 Technical Details
* **Single-file Architecture**: All HTML structure, styles, and Javascript logics are self-contained inside `index.html`.
* **State Management**:
  * Persistent database utilizing LocalStorage to preserve Reminders and Alarms configurations across page reloads.
  * Native click events bound to the global `window` scope (`window.deleteReminder`, `window.deleteAlarm`, `window.toggleAlarm`, etc.) to prevent context-loss during DOM refreshes.
* **Engine Tick**: A unified background checker syncs system time, evaluates active alarms, and updates countdown tags every second.

---

## 🧪 How to Verify / Test

### 1. Test Reminders
1. Under the **Schedule Reminder** card, input text and choose a future date/time. Click **Add Reminder**.
2. Click the trash icon next to the reminder card. Verify that it is spliced from the array and removed from the DOM instantly.
3. Add multiple reminders, then click **Clear All** at the top-right of the list container. Verify the entire list flushes and shows the empty state.

### 2. Test Alarms
1. Under the **Queue Alarm** section, select a time exactly 1 minute in the future. Click **Set Alarm**.
2. Wait for the clock to strike the set time. Observe the top-right alert popup sliding in and the synthesizer audio triggering.
3. Click **Dismiss**. The audio stops, the modal disappears, and the alarm is toggled off (disabled) in the list. Verify that it does not fire again.
4. Set multiple alarms, click **Clear All**, and verify all alarms disappear.

### 3. Test Countdown Timer
1. Select the **1 Min** preset or use the manual spinners to configure a duration.
2. Click **Start** (observe the countdown and circle path depletion). Click **Pause** and **Reset** to verify states.
3. Let the timer reach zero. Verify the red-alert pulsing circle displays, beeps start, and the completion modal appears.

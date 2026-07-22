# 📜 Changelog & User Feedback Fixes

All notable changes, enhancements, and bug fixes for **Dynamic Island for Windows** are documented in this file.

---

## [Unreleased / Latest Updates]

### ✨ Fixes & Enhancements

#### 🍏 Native macOS Notch Style Mode (User Feedback / Feature Request)
* **Problem / Request:** Users requested an option similar to the native Windows 11 style, but designed to resemble a MacBook notch where the island sticks flush to the top edge of the upper screen.
* **Fix & Features Added:**
  * **New Mod Setting (`MacOsNotchStyle`):** Added `macOS Notch style` toggle under the Appearance settings block.
  * **Top-Attached Screen Ceilings:** When enabled, the window position automatically anchors flush against the monitor top edge (`y = 0`) instead of floating 8 pixels below it, ensuring a true top-attached notch appearance.
  * **Custom Direct2D Notch Path Geometry:** Implemented `CreateNotchGeometry()` and `CreateIslandMaskGeometry()`, generating an authentic MacBook notch shape with flat top corners and smoothly curved bottom corners (`16.0f` scaled radius).
  * **Right-Click Context Menu Toggle:** Added a convenient right-click menu item ("Use macOS Notch Style" / "Disable macOS Notch Style") to switch seamlessly between Apple floating pill, Windows 11 flyout box, and macOS Notch styles.
  * **Precision Media Click Detection:** Updated window coordinate calculations in `WndProc` so interacting with media buttons and dashboards works with exact precision whether floating or attached in notch style.

#### ❌ Right-Click Menu Dismiss Button Functionality & Media Visibility Fix (Feedback / Issue #32)
* **Problem:** Clicking "Dismiss" from the right-click context menu would cause the Dynamic Island to disappear permanently, even if media (e.g. Spotify, YouTube) was currently playing in the background. The island would remain hidden until a new event (such as a media title change or clipboard copy) occurred.
* **Fix & Features Added:**
  * **Comprehensive Transient State Clearing:** Updated `DismissTransientState()` to reliably clear all transient popups (Clipboard, Notifications, Volume, Progress, Caps Lock, Device, and Battery low alerts) while keeping active media state intact.
  * **Immediate Layout Refresh & Nudge:** Added immediate `g_layoutDirty = true`, `g_clickExpanded = false`, and `TriggerNudge()` calls when the Dismiss menu command is executed.
  * **Instant Media Restoration:** When dismissing an overlaying notification or clipboard popup while media is playing, the island now smoothly and immediately animates back to the active Media pill or dashboard without ever hiding or freezing.

#### 📋 Customizable Clipboard Icon Background Style (Feedback / Issue #30)
* **Problem:** When copying text or images, the clipboard preview displayed a hardcoded gray background behind the icon that could not be modified or removed via settings.
* **Fix & Features Added:**
  * Added **`ClipboardIconBgStyle`** under the **Modules** settings block with 4 customizable modes:
    * `default`: Standard subtle gray background badge.
    * `transparent`: Eliminates the background box entirely for a clean, outline-only floating icon look.
    * `accent`: Uses the island's glowing accent color with soft opacity.
    * `custom`: Uses a custom hex color.
  * Added **`ClipboardIconBgHex`** setting to define the exact hex color when using Custom mode (default `#2E2E38`).
  * Updated `DrawClipboard` rendering logic so both the outer badge box and inner fallback icon plate respect the selected background style.

#### 🚀 High Refresh Rate (360Hz+) Support & Precise Animation Controls (Feedback / Issue #26)
* **Problem:** Animations felt stuttery or buggy on high refresh rate monitors (144Hz, 240Hz, 360Hz+), and users lacked precise control over animation physics.
* **Fix & Features Added:**
  * **Zero-Spin Frame Pacing:** Replaced hardcoded 16ms sleep (~60 FPS) with a CPU-efficient hybrid timing system using 1ms OS timer resolution (`timeBeginPeriod`) and thread yielding. Achieves buttery-smooth presentation on 360Hz/500Hz panels while maintaining **0.00% CPU usage at idle**.
  * **Automatic Monitor Hz Detection:** Implemented `GetMonitorRefreshRate(HWND hwnd)` to detect and match native display frequency automatically when set to `Auto`.
  * **2000Hz Deterministic Physics Sub-Stepping:** Upgraded `SpringValue::Step` to use a fixed timestep (`0.0005s`), ensuring identical spring behavior and stability regardless of framerate.
  * **New Mod Settings (`TargetFPS`, `AnimationStyle`, `AnimationSpeed`):** Added options for target FPS up to 500 FPS, spring styles (`smooth`, `default`, `bouncy`, `snappy`), and 6 granular animation speed levels (0.5x to 2.0x).

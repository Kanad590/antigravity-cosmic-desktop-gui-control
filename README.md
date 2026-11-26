# 🖱️ antigravity-cosmic-desktop-gui-control

> 🚀 **Antigravity Desktop GUI Automation Skill, High-Speed CLI Engine (`ag-gui` v2.1+), and 35-Tool FastMCP Server (`linux-desktop-apps-mcp`)** purpose-built for **Pop!_OS COSMIC (Wayland & Xwayland)**.

Unlike legacy X11 tools (`xdotool`, `PyAutoGUI`) that break under Wayland, this engine controls both **native Wayland apps** (Firefox, Tuta Mail, COSMIC apps) and **Wine/Xwayland apps** (e.g., Jagannatha Hora) directly at the kernel and compositor level.

---

## ✨ Key Capabilities

- 🖱️ **Kernel UInput Pointer (`EV_ABS` / `EV_REL`):** True Wayland + Xwayland mouse clicks, smooth drag-and-drop, and scroll wheel control without `ydotool` daemon issues.
- ⌨️ **Wayland-Native Keyboard (`wtype`):** Stdin-safe typing, XKB key-alias normalization, and multi-key hotkeys.
- 📸 **Zero-Clutter Screencapture (`cosmic-screenshot`):** Fast full-desktop and window-cropped screenshots without leaving `/tmp` clutter.
- 🧠 **Hybrid UI Discovery (AT-SPI + Dark-Mode OCR):**
  - ⚡ Fast AT-SPI accessibility widget lookup (`find_elements`, `click_element`).
  - 🔍 Dark-mode-aware Tesseract OCR (`find_text`, `click_text`) with sliding-window phrase matching.
- 🎯 **Set-of-Mark (SoM) Visual Tagger (`som_inspect` / `click_mark`):** Merges AT-SPI widgets and OCR labels into numbered `[1]`, `[2]`, ... badges with collision-free placement and yellow exact-center dots.
- 🖼️ **OpenCV Multi-Scale Icon Matching (`find_icon` / `click_icon`):** Template matching (`TM_CCOEFF_NORMED`) for textless toolbar icons when no keyboard shortcut exists.
- 🛡️ **Safety & Reliability Guards:**
  - 🔒 **Focus Guard (`--guard` / `guard_window`):** Aborts typing, hotkeys, and pointer actions if focus leaves the target window.
  - 🚨 **Popup Detector (`--stop-on-popup`):** Halts batch execution immediately when unexpected X11 or Wayland modal dialogs appear.
  - ✏️ **Universal Field Replacement (`replace_text`):** Automatically detects Win32/Wine `CEdit` controls (`Home` + `Shift+End` / drag-select) vs modern GTK/Electron (`Ctrl+A`).
  - 🪟 **Idempotent Window Maximize (`maximize_window`):** Checks window bounds before toggling `Super+m` on COSMIC or uses `wmctrl` on Xwayland.
- ⚡ **Single-Call Batch Macro Runner (`batch` / `gui_batch`):** Executes multi-step GUI sequences in-process with zero LLM round-trip lag.

---

## 🖼️ Live Visual Demos

### 🎯 Set-of-Mark (SoM) Visual Tagger (`ag-gui som-inspect`)
Automatic AT-SPI + OCR element tagging with collision-free numbered `[id]` badges and exact click-center dots:

![Set-of-Mark Visual Tagger Demo](assets/som-tagger-demo.png)

### 🦊 Pure Mouse & Keyboard Browser Automation (Firefox Theme Switch)
Automated end-to-end navigation to `about:addons` → `Themes` → `Light` using only `ag-gui` mouse & keyboard control on COSMIC Wayland:

![Firefox Light Theme Automation Demo](assets/firefox-light-theme-demo.png)

---

## 📁 Repository Structure

| Path | Purpose |
| :--- | :--- |
| 📄 `SKILL.md` | Antigravity skill definition, tool routing, and safety rules |
| ⚙️ `bin/ag-gui` | Main Python CLI automation engine |
| 🔌 `bin/linux-desktop-apps-mcp` | 35-tool FastMCP server wrapping `ag-gui` |
| 🧩 `mcp/*.json` | JSON tool schemas for all 35 MCP tools |
| 📧 `scripts/tuta_mailer.py` | Example automated email sender for Tuta Mail Flatpak |
| 🖼️ `assets/` | Visual demo screenshots |

---

## 🛠️ System Requirements (Pop!_OS COSMIC / Linux Wayland)

- 🐍 **Python 3.12+** (`evdev`, `Pillow`, `numpy`, `opencv-python`, `PyGObject` / `Atspi`)
- 🖥️ **System Tools:** `wtype`, `tesseract-ocr`, `cosmic-screenshot`, `wmctrl`, `xdotool`, `wl-clipboard`
- 📦 **MCP Runtime:** `uv` (for running `linux-desktop-apps-mcp` with `mcp<2`)

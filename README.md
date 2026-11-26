# cosmic-desktop-gui-control

Wayland-native + Xwayland Desktop GUI Automation Skill, CLI Engine (`ag-gui` v2.1+), and 35-tool FastMCP Server (`linux-desktop-apps-mcp`) for Pop!_OS COSMIC Wayland.

## Components

- `SKILL.md` — Antigravity skill instructions and safety rules
- `bin/ag-gui` — Core CLI engine (kernel UInput pointer, `wtype` keyboard, `cosmic-screenshot`, AT-SPI, Set-of-Mark visual tagger, OpenCV multi-scale icon matching, Focus Guard, Popup Detector, batch macro runner)
- `bin/linux-desktop-apps-mcp` — 35-tool MCP server wrapping `ag-gui`
- `mcp/` — Tool JSON schemas for all 35 MCP tools
- `scripts/tuta_mailer.py` — Automated Tuta Mail desktop sender example

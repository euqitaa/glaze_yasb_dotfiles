# GlazeWM + YASB — Configuration

A compact, GitHub-ready overview and quick reference for the GlazeWM and YASB configuration files included in this repository.

**Contents**
 - **Overview:** Purpose and layout of the configs.
 - **Files:** Quick links to the configuration and stylesheet.
 - **Features:** Highlights of the defaults and customizations.
 - **Install & Use:** How to apply these configs locally.
 - **Customization:** What to edit for common tweaks (gaps, colors, keybindings, widgets).

**Files**
 - GlazeWM config: [glaze_dot/config.yaml](glaze_dot/config.yaml)
 - YASB config: [yasb_dot/config.yaml](yasb_dot/config.yaml)
 - YASB stylesheet: [yasb_dot/styles.css](yasb_dot/styles.css)

**Overview**
 - **Purpose:** These files provide a ready-to-use GlazeWM tiling/window manager setup paired with a YASB bar/theme. They are tuned for a Nord-inspired palette and Windows usage (YASB runs on Windows).
 - **Layout:** GlazeWM handles window behavior, gaps, workspaces, rules, and keybindings. YASB provides the top bar, widgets, and a matching stylesheet.

**Highlights**
 - **GlazeWM (`glaze_dot/config.yaml`):**
	 - **Startup/Shutdown:** Runs `yasb` on startup and kills it on shutdown.
	 - **Gaps:** Inner gap of `6px`, outer gaps set to keep top `0px` to avoid conflicts with the app bar.
	 - **Window effects:** Focus/other window border colors match the YASB theme.
	 - **Workspaces:** Nine workspaces named `1`..`9`.
	 - **Rules:** Several `ignore` rules for known system/process windows (YASB itself, PowerToys, Lively, Office popups).
	 - **Keybindings:** Comprehensive keybindings for focus, move, resize, workspace navigation, and WM controls (e.g., `alt+t` toggles tiling).

 - **YASB (`yasb_dot/config.yaml` + `yasb_dot/styles.css`):**
	 - **Bar:** A single top bar (`primary-bar`) sized to `30px` and registered as a Windows app bar.
	 - **Widgets included:** `glazewm_workspaces`, `media`, `taskbar`, `active_window`, `clock`, `volume`, `bluetooth`, `wifi`, `power_menu`, `notes`, `wallpapers`, `weather` and more.
	 - **Styling:** `styles.css` defines a Nord-inspired palette (variables like `--bg`, `--text`, `--base2`) and widget layouts for consistent visuals.

**Install & Use**
1. Place the folders in your configuration location or clone this repo.
2. Ensure GlazeWM is installed and configured to load `glaze_dot/config.yaml` (or symlink it to the expected path).
3. Ensure YASB is installed and pointed at `yasb_dot/config.yaml`. The bar expects the stylesheet at `yasb_dot/styles.css`.
4. Start GlazeWM; it will invoke YASB at startup (see `startup_commands` in GlazeWM config).

Example (Windows PowerShell):

```powershell
# start YASB manually (if needed)
yasb.exe --config "path\to\yasb_dot\config.yaml"

# reload GlazeWM config (if your environment exposes a CLI)
glazewm --reload
```

**Quick Customizations**
 - Gaps: Edit `gaps.inner_gap` and `gaps.outer_gap` in [glaze_dot/config.yaml](glaze_dot/config.yaml).
 - Bar height: Adjust `bars -> primary-bar -> dimensions -> height` in [yasb_dot/config.yaml](yasb_dot/config.yaml) and update `--bar-h` in [yasb_dot/styles.css](yasb_dot/styles.css) to match.
 - Colors: Edit the CSS variables at the top of [yasb_dot/styles.css](yasb_dot/styles.css) (e.g., `--bg`, `--text`).
 - Keybindings: Edit the `keybindings` section in [glaze_dot/config.yaml](glaze_dot/config.yaml) to change shortcuts.
 - Widgets: Add/remove or re-order widgets in `bars -> primary-bar -> widgets` inside [yasb_dot/config.yaml](yasb_dot/config.yaml).

**Notes & Tips**
 - The GlazeWM config sets `outer_gap.top: '0px'` because YASB registers as a Windows app bar; adding top gaps would create dead space between the bar and windows.
 - Many widgets provide `callbacks` (left/right click actions) and `options` (truncation, icons, max lengths) — tweak these to fit your workflows.
 - Sensitive values in the example (like API keys) should be rotated or replaced before sharing publicly.

**Contributing**
 - Feel free to open issues or submit PRs to improve the configs or add alternative themes.

**License**
 - These config files are provided as-is. Add a license file if you plan to share or reuse widely.

---

If you'd like, I can:
 - update the README with example screenshots (if you provide images),
 - add a quick install script for Windows, or
 - generate a minimal `install` PowerShell snippet to symlink these configs.

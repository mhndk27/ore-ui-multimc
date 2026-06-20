# Changes from the original (Prism Launcher → MultiMC)

This document lists every technical difference between this port and the original [Ore UI theme pack](https://github.com/ninsent/Ore-UI-theme-pack) by ninsent/maksiuuuuu.

## `theme.json`

- Added `"Window"` to the `colors` block. MultiMC's theme engine reads this palette role; the original Prism format doesn't need it, so it was missing.
- `qssFilePath` and `logColors` kept as-is from the original format.

## `themeStyle.css`

- **Removed Prism-only selectors:** `#scrollAreaWidgetContents` (and its `_2`/`_3` variants), `#taskProgressScrollArea`, `#taskProgressContainer`, `#qswPages > QObject`. None of these widgets exist in MultiMC's UI tree.
- **Renamed `JavaWizardWidget` → `JavaSettingsWidget`.** This is MultiMC's actual Java settings widget class name; Prism uses a different one.
- **Added `#instanceToolBar QToolButton { min-width: 120px; }`** so the sidebar buttons (Launch, Edit Instance, Minecraft Folder, etc.) share a uniform width instead of sizing individually to their text.
- **Added `QMenu::item { padding-left: 26px; }`** to stop menu icons from overlapping their text label.
- **Added explicit `#mainToolBar`, `#newsToolBar`, `#instanceToolBar` rules** so each toolbar gets a defined background/border instead of inheriting the generic `QToolBar` style.
- **Hid the "Support MultiMC" button** on the top toolbar via `#mainToolBar QToolButton[text="Support MultiMC"]`.

## Radio button SVGs (`resources/radiobutton-*.svg`)

All 8 radio button state SVGs (checked/unchecked × default/hover/pressed/disabled) were rebuilt from scratch. The originals used an SVG `<clipPath>` containing a `<rect fill="white">`, which a subset of Qt's SVG renderer draws as a literal white rectangle instead of using it as a clip mask — showing a white box around the indicator. The rebuilt files draw the same shapes directly, without a clip path, avoiding the renderer bug entirely.

## Things that were tried and reverted

- **Hiding unused instance sidebar buttons** (Edit Notes, View Mods, View Worlds, Manage Screenshots, Config Folder, Instance Folder) via `[text="..."]` CSS selectors on `#instanceToolBar`. Unlike the Support MultiMC button above, this did not work in practice — none of the targeted sidebar buttons were actually hidden — and the attempt was removed from all variant CSS files.
- **A "White" chrome variant family** (true white window/toolbar backgrounds) was prototyped but dropped — color contrast and consistency issues across different OS rendering meant the result needed more design work than the project's scope.

## Known issues

- **The server icon does not render** in MultiMC's instance list, regardless of theme. This is in MultiMC's own icon-loading code, not something a theme/QSS file can fix.
- **Some instance/version icons can disappear** after the icon theme from `iconthemes/` is applied, for reasons not yet identified. Replacement instance icons are distributed separately — see [INSTALL.md](INSTALL.md#3-instance-icons-pack).

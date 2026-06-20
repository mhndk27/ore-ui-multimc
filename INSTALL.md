# Installation

This project is distributed as **three separate packs** on the [Releases page](../../releases). Download whichever ones you want — they don't depend on each other.

1. [Themes Pack](#1-themes-pack)
2. [Icon Pack](#2-icon-pack)
3. [Instance Icons Pack](#3-instance-icons-pack)

---

## 1. Themes Pack

**Ore UI (MultiMC port) – Themes Pack** contains all 6 color variants. Each variant folder inside the ZIP has a preview image and a `themes` folder you copy directly.

MultiMC supports only **one** custom color theme at a time, and it must live in a folder named exactly `custom`.

1. Extract the Themes Pack ZIP.
2. Pick a variant (e.g. `ore-dark-emerald`). Inside it you'll find:
   ```
   ore-dark-emerald/
   ├── preview-dark-emerald.png
   └── themes/
       └── custom/
           ├── theme.json
           ├── themeStyle.css
           └── resources/
   ```
3. Copy (or merge) that variant's `themes` folder directly into your MultiMC directory:
   - **Windows:** `%APPDATA%\MultiMC\` (or wherever `MultiMC.exe` is, if portable)
   - **Linux:** `~/.local/share/multimc/`
   - **macOS:** `~/Library/Application Support/MultiMC/`
4. Restart MultiMC.
5. Go to **Settings → User Interface → Theme → Colors** and select the variant name.

**To switch variants later:** delete the contents of `themes/custom/` and repeat steps 2–4 with a different variant.

---

## 2. Icon Pack

**Ore UI – Icon Pack** contains the icon set for MultiMC's own interface — toolbar icons, settings page icons, etc. (Not the icons shown next to each instance — that's part 3.)

1. Extract the Icon Pack ZIP — it contains an `iconthemes` folder:
   ```
   iconthemes/
   └── custom/
       ├── index.theme
       ├── 16x16/
       ├── 24x24/
       ├── 32x32/
       ├── 48x48/
       ├── 64x64/
       └── 96x96/
   ```
2. Copy the `iconthemes` folder directly into your MultiMC directory, next to `themes/`.
3. Restart MultiMC.
4. Go to **Settings → User Interface → Theme → Icons** and select **custom**.

If an icon is missing from this pack, MultiMC automatically falls back to its own built-in icon for that spot — you won't see a blank/broken icon, just the default MultiMC look for that one item. This fallback is configured by the `Inherits=flat_white` line in `index.theme`.

> The server icon not rendering is a separate, unrelated MultiMC limitation — it isn't fixed by any of these packs and isn't something this theme can change.

---

## 3. Instance Icons Pack

**Ore UI – Instance Icons Pack** contains replacement icons for the icons shown on each Minecraft instance in your list (e.g. the grass-block icon, version-specific icons) — separate from the program icon theme in part 2. This set exists because some of MultiMC's built-in instance icons can disappear after the Icon Pack from part 2 is applied, for reasons not yet identified.

1. Extract the Instance Icons Pack ZIP — it contains an `icons` folder.
2. Copy that `icons` folder directly into your MultiMC directory, next to `themes/` and `iconthemes/`, overwriting if prompted.
3. Restart MultiMC.

---

## Troubleshooting

| Problem | Fix |
|---|---|
| Color theme doesn't appear in the dropdown | Make sure the folder is named exactly `custom` and sits directly inside `themes/`, not nested deeper. Restart MultiMC — themes are only scanned at launch. |
| Icon set doesn't appear | Same as above, but for `iconthemes/custom/`. |
| An instance icon looks wrong or is missing | See [Instance Icons Pack](#3-instance-icons-pack) above. |

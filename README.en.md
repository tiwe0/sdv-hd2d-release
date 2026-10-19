> [!WARNING]
> **🚧 Early testing**
>
> **Expect frequent updates. Many bugs are still being fixed, and features are still being improved.**
>
> **🔓 The project will be open sourced once all features are stable.**

---

<div align="center">

# 🌾 SDV-HD2D

**A familiar pixel world, a new dimension of light.**

Stardew Valley's pixel art on a 3D stage with lighting, shadows and atmosphere.

[![Release](https://img.shields.io/github/v/release/tiwe0/sdv-hd2d-release?style=for-the-badge&color=79b86c&label=RELEASE)](https://github.com/tiwe0/sdv-hd2d-release/releases)
[![Downloads](https://img.shields.io/github/downloads/tiwe0/sdv-hd2d-release/total?style=for-the-badge&color=e7ad55)](https://github.com/tiwe0/sdv-hd2d-release/releases)
[![Stars](https://img.shields.io/github/stars/tiwe0/sdv-hd2d-release?style=for-the-badge&logo=github&color=f2cf66)](https://github.com/tiwe0/sdv-hd2d-release)

**[📸 Screenshots](#screenshots) · [📦 Download](https://github.com/tiwe0/sdv-hd2d-release/releases/latest) · [📖 Install](#installation-en) · [🐛 Report a bug](https://github.com/tiwe0/sdv-hd2d-release/issues) · [⚡ Support](https://afdian.com/a/sdv-hd2d)**

[简体中文](README.md) · **English**

</div>

---

<a id="screenshots"></a>

## 📸 Screenshots

![SDV-HD2D screenshot 1](images/preview-1.png)

<table>
<tr><td width="50%"><a href="images/preview-2.png"><img src="images/preview-2.png" alt="SDV-HD2D screenshot 2" width="100%" /></a></td><td width="50%"><a href="images/preview-3.png"><img src="images/preview-3.png" alt="SDV-HD2D screenshot 3" width="100%" /></a></td></tr>
<tr><td width="50%"><a href="images/preview-4.png"><img src="images/preview-4.png" alt="SDV-HD2D screenshot 4" width="100%" /></a></td><td width="50%"><a href="images/preview-5.png"><img src="images/preview-5.png" alt="SDV-HD2D screenshot 5" width="100%" /></a></td></tr>
<tr><td width="50%"><a href="images/preview-6.png"><img src="images/preview-6.png" alt="SDV-HD2D screenshot 6" width="100%" /></a></td><td width="50%"><a href="images/preview-7.png"><img src="images/preview-7.png" alt="SDV-HD2D screenshot 7" width="100%" /></a></td></tr>
</table>

## ✨ Features

| Lighting & atmosphere | Camera & materials |
|---|---|
| Sun, cloud and contact shadows | Orthographic and perspective cameras, rotation and depth of field |
| Streetlights, firelight, dynamic lights and bloom | HDR lighting, PBR materials and water reflections |
| 3D rain and snow, fireflies and distant fog | In-game settings with immediate visual feedback |

> Changes rendering only, never gameplay, and never writes your save.

---

## 📖 Installation and usage

[Requirements](#requirements-en) · [Install](#installation-en) · [Usage](#usage-en) · [Report a bug](#feedback-en) · [Troubleshooting](#faq-en) · [Known limits](#limits-en)

Version 0.9.0 (public beta).

SDV-HD2D renders Stardew Valley in the Octopath Traveler HD-2D style: the game's own pixel art on a lit 3D stage, with shadows, glowing lamps, bloom, depth of field, cloud shadows and 3D weather. It changes rendering only, never gameplay, and never writes your save.

> [!CAUTION]
> **Before you install**
>
> Version 0.9.0 is an early public beta. Visual glitches, performance fluctuations, inaccurate mouse targeting and mod conflicts may occur.
>
> - Only Windows has been tested. Linux, macOS, multiplayer and split screen are untested.
> - Other lighting or shader mods may conflict. Custom maps and mods that draw their own world graphics may have missing or misplaced details. Start with a minimal mod setup.
> - Fishing, combat damage numbers, heart events and festivals need more testing. Mouse targeting may be offset near cliffs or slopes with a perspective or rotated camera.
> - Press **F8** to compare with the original rendering, or **F9** to return to an orthographic camera. If problems persist, quit the game and temporarily remove the mod.
> - Report issues with the mod version, location, in-game time, screenshots and a [SMAPI log](https://smapi.io/log). Press **F11** for tile coordinates.

<a id="requirements-en"></a>

### 1. Requirements

| What | Version | Where | Notes |
|---|---|---|---|
| Stardew Valley (PC) | 1.6.15 | Steam / GOG | required |
| SMAPI | 4.5.2 or later | [smapi.io](https://smapi.io) | required: the mod loader |
| StardewUI (by focustense) | 0.6.1 or later | [Nexus Mods #28870](https://www.nexusmods.com/stardewvalley/mods/28870), [GitHub releases](https://github.com/focustense/StardewUI/releases) | required: draws the settings page |

- Nothing else is needed. Keep SMAPI's own Console Commands and Save Backup.
- Developed and tested on Windows with SMAPI 4.5.2 and StardewUI 0.6.1. Linux, macOS and community forks of StardewUI (such as StardewUI Continued) are untested.
- Without StardewUI, SMAPI reports the missing dependency at launch and does not load this mod.

<a id="installation-en"></a>

### 2. Install

1. **Install SMAPI** (skip if you have it)
   1. Launch the game once, then quit.
   2. Download SMAPI from [smapi.io](https://smapi.io), unzip it, run `install on Windows.bat` and follow the prompts.
   3. On Steam, the installer prints a launch option like `"…\Stardew Valley\StardewModdingAPI.exe" %command%`. Paste the whole line, quotes and `%command%` included, into Steam: Library → right-click Stardew Valley → Properties → General → Launch Options. For GOG, Xbox and others, follow [smapi.io/install](https://smapi.io/install).
2. **Install StardewUI**: unzip it into the game's `Mods` folder, so that `Mods/StardewUI/manifest.json` exists.
3. **Install SDV-HD2D**: unzip `SDV-HD2D-0.9.0.zip` into `Mods`, so that `Mods/SDV-HD2D/manifest.json` exists.
4. **Start the game** from Steam as usual, or run `StardewModdingAPI.exe` in the game folder. The SMAPI console lists `SDV-HD2D 0.9.0 by ivory` and `StardewUI 0.6.1`.

**Update**: quit the game and unzip the new version over `Mods`. The zip holds no `config.json`, so your settings stay.

**Uninstall**: delete `Mods/SDV-HD2D`. Saves are not affected.

<a id="usage-en"></a>

### 3. Use

#### Controls

| Key | Action |
|---|---|
| F10 | open or close the HD2D settings (also the sun tab beside Options in the game menu) |
| F8 | 3D on or off, to compare with the original game |
| F9 | switch orthographic / perspective camera |
| F11 | cell grid: every map cell on screen labelled `x,y`, to report a problem |
| F7 | world grid (a debugging aid) |
| F6 | performance overlay: CPU and GPU time per render stage |

#### Settings

Press F10 to open the settings page. Five sections:

- Sunlight & Shadows;
- Local & Dynamic Lights;
- Atmosphere;
- HDR, Bloom & Depth of Field;
- Camera & Entities: pitch, yaw, perspective camera, field of view (5–30°, perspective only), entity height correction with its fit-to-pitch button, and fading what hides a character.

Changes apply at once. **Save** writes `Mods/SDV-HD2D/config.json` only, never your save; **Reset** restores the page's defaults. The page follows the game's language (English, Chinese).

#### Camera and mouse

- The default orthographic camera (pitch 40°, yaw 0°) lays the 3D world exactly where the game draws it.
- A perspective camera, a wider field of view or a turned camera look more three-dimensional, but show more ground and cost more.
- The mouse targets what you see: clicking the ground, a crop, a chest or a character acts on what is under the cursor in the 3D picture.
  - On flat ground this is exact under every camera.
  - A perspective or turned camera can be a tile off at cliff edges and on slopes.
  - In split screen the mouse keeps the game's own screen layout.

#### Performance

On the development PC (2560×1440 borderless, vsync on, everything enabled):

- Default camera: 60 FPS everywhere measured; the heaviest spots (the farm, the Saloon at night) take about 13 ms of CPU per frame.
- Perspective, field of view 12°: 60 FPS as well.
- Perspective, field of view 30°: the farm about 54 FPS, the Forest in the morning about 58, Town and the Saloon 60.

The game's own VSync option caps the frame rate at the display's refresh rate. If the frame rate drops, try in order:

1. lower Render scale;
2. turn off Cast shadows or Point projection shadows;
3. turn off Depth of field;
4. with a perspective camera, narrow the field of view.

#### Configuration file

**config.json** is written at first launch. The settings page covers every visual setting; you can also edit the file while the game is closed. Other fields:

- `ShowFrameRate`: the FPS counter at the top left, on by default; set `false` to hide it.
- `StageEnabled`: the 3D stage (as F8).
- `DebugGridEnabled`, `DebugCellsEnabled`, `DebugGroupsEnabled`: debugging overlays, off by default.
- `AutoLoadSaveFolder`: development only; a normal launch ignores it.

<a id="feedback-en"></a>

### 4. Reporting a problem

- Press F11 and note the `x,y` of the cell that looks wrong, with the location and the time of day. A screenshot helps.
- For performance, press F6, or run `hd2d_profile dump` in the SMAPI console; it writes `Mods/SDV-HD2D/.dev/screenshots/frame-profile.json`.
- Upload `%appdata%\StardewValley\ErrorLogs\SMAPI-latest.txt` at [smapi.io/log](https://smapi.io/log) and share the link.
- Console commands:
  - `hd2d_shot [name]` saves a screenshot to `Mods/SDV-HD2D/.dev/screenshots`;
  - `hd2d_settings reset` restores the defaults, `hd2d_settings save` keeps them;
  - `hd2d_stage` and `hd2d_cells` do the same as F8 and F11.

<a id="faq-en"></a>

### 5. Troubleshooting

- **SMAPI says StardewUI is missing**: install it (section 1) and check that `Mods/StardewUI/manifest.json` exists, with no extra folder level.
- **F10 shows no settings page**: StardewUI did not load. Look for `StardewUI` and `SDV-HD2D` errors in the SMAPI console or log.
- **The picture is back to the original 2D**: F8 may have been pressed; press it again. Overnight farm events (the witch, the fairy, meteorites) and an event's own custom scene keep the game's drawing by design.
- **The mouse is a tile off**: most likely a perspective or turned camera at a cliff edge or on a slope. The orthographic camera (F9, or Perspective camera off) is exact.
- **Low frame rate**: see Performance.

<a id="limits-en"></a>

### 6. Known limits (beta)

- Fishing, combat damage numbers, heart events and festivals are staged in 3D but not yet verified in real play. Please report anything odd.
- Overnight farm events and an event's own custom scene keep the game's 2D drawing; a few special lighting cases keep the game's lighting for that frame.
- A few terrain spots are still read imperfectly from the map art, for example two small waterfalls with no cliff under them, in the Forest and on the Mountain.
- Other mods:
  - mods that change art work normally;
  - mods that change maps get the generic scene, without hand-tuned details;
  - mods that draw world graphics their own way may show them flat or out of place;
  - mods with their own lighting or shaders may conflict;
  - mods that read the cursor themselves still use the game's screen layout.
- Multiplayer and split screen are untested.

---

## 🗺️ Roadmap

### Current priorities

- [ ] **Better configuration UI and interactions**: improve settings organization, parameter descriptions and interaction feedback to make visual adjustments, previews, saving settings and restoring defaults more intuitive.
- [ ] **Mod compatibility framework (key priority)**: provide shared integration interfaces and compatibility configuration so other mod authors can quickly integrate custom maps, assets and scenes, supported by documentation, examples and debugging tools.
- [ ] **Manual terrain fixes**: progressively correct terrain inferred inaccurately from map art and refine scene details.
- [ ] **Seasonal lighting**: tune sunlight color, intensity and ambient light for spring, summer, fall and winter, and improve transitions across times of day and weather conditions.
- [ ] **Camera and interaction fixes**: improve mouse targeting and occlusion near cliffs and slopes with perspective or rotated cameras.
- [ ] **Special scene testing**: test fishing, combat damage numbers, heart events and festivals more thoroughly, and fix visual and interaction issues.

### Further exploration and improvements

- [ ] **Performance and quality presets**: reduce the cost of complex scenes and multiple light sources, and explore quality presets for different hardware.
- [ ] **Mod compatibility**: progressively test custom maps, art replacements and other rendering mods, and document compatibility and recommended settings.
- [ ] **Broader environment testing**: evaluate Linux, macOS, multiplayer and split screen, and determine the scope of support based on test results.
- [ ] **Open-source preparation**: release the source code once all features are stable, with build instructions and contribution guidelines.

Plans may change based on testing feedback. Support for exploratory items will depend on validation results.

## 🙏 Acknowledgments

Thanks to **[SDV-Radiance](https://github.com/PHUICMT/SDV-Radiance)**. This project uses some data from that mod.

## 💜 Support development

Enjoying SDV-HD2D? Support ongoing development and maintenance on [Afdian](https://afdian.com/a/sdv-hd2d). Thank you to everyone who plays, reports issues and supports the project!

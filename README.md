# sdv-hd2d-release

# SDV-HD2D 安装与使用说明

版本 0.9.0（公测版）。[English version below](#sdv-hd2d-installation-and-usage).

SDV-HD2D 把星露谷物语的画面变成八方旅人式的 HD-2D：游戏原有的像素美术立在有光照的 3D 舞台上，有阴影、发光的灯、泛光、景深、云影和 3D 天气。它只改渲染，不改玩法，也不写存档。

## 1. 需要什么

| 项目 | 版本 | 从哪里下载 | 说明 |
|---|---|---|---|
| 星露谷物语（PC 版） | 1.6.15 | Steam / GOG | 必需 |
| SMAPI | 4.5.2 或更高 | [smapi.io](https://smapi.io) | 必需：模组加载器 |
| StardewUI（作者 focustense） | 0.6.1 或更高 | [Nexus Mods #28870](https://www.nexusmods.com/stardewvalley/mods/28870)、[GitHub Releases](https://github.com/focustense/StardewUI/releases) | 必需：设置页面用它绘制 |

- 没有其他依赖。SMAPI 自带的 Console Commands 和 Save Backup 保留即可。
- 在 Windows、SMAPI 4.5.2、StardewUI 0.6.1 上开发和测试；Linux、macOS 未测试。StardewUI 的社区分支（如 StardewUI Continued）也未测试。
- 缺少 StardewUI 时，SMAPI 会在启动时提示依赖缺失，并且不加载本模组。

## 2. 安装

1. **安装 SMAPI**（已经装过就跳过）
   1. 先正常启动一次游戏，再退出。
   2. 从 [smapi.io](https://smapi.io) 下载 SMAPI，解压后运行 `install on Windows.bat`，按提示完成安装。
   3. Steam 用户：安装器最后会打印一行启动选项，形如 `"…\Stardew Valley\StardewModdingAPI.exe" %command%`。把整行（包括引号和 `%command%`）粘贴到 Steam：库 → 右键星露谷物语 → 属性 → 通用 → 启动选项。GOG、Xbox 等版本按 [smapi.io/install](https://smapi.io/install) 的说明操作。
2. **安装 StardewUI**：下载压缩包，解压到游戏目录的 `Mods` 文件夹，得到 `Mods/StardewUI/manifest.json`。
3. **安装 SDV-HD2D**：把 `SDV-HD2D-0.9.0.zip` 解压到 `Mods`，得到 `Mods/SDV-HD2D/manifest.json`。
4. **启动游戏**：Steam 里正常点「开始」即可，或直接运行游戏目录里的 `StardewModdingAPI.exe`。SMAPI 控制台里应能看到 `SDV-HD2D 0.9.0 by ivory` 和 `StardewUI 0.6.1`。

装好后的目录：

```text
Stardew Valley/
├─ StardewModdingAPI.exe
└─ Mods/
   ├─ ConsoleCommands/     （SMAPI 自带）
   ├─ SaveBackup/          （SMAPI 自带）
   ├─ StardewUI/
   │  └─ manifest.json
   └─ SDV-HD2D/
      ├─ manifest.json
      ├─ SDV-HD2D.dll
      ├─ assets/  data/  i18n/  docs/
      └─ config.json       （第一次启动后生成，保存你的设置）
```

**更新**：退出游戏，把新版压缩包解压到 `Mods` 覆盖即可。压缩包里没有 `config.json`，你的设置会保留。

**卸载**：删除 `Mods/SDV-HD2D`。存档不受影响。

## 3. 使用

### 按键

| 按键 | 作用 |
|---|---|
| F10 | 打开或关闭 HD2D 设置（游戏菜单里「选项」旁的太阳图标也可以） |
| F8 | 开关 3D 画面，与原版对照 |
| F9 | 切换正交 / 透视镜头 |
| F11 | 格子网格：屏幕上每个地图格都标出坐标 `x,y`，报告问题时用 |
| F7 | 世界网格（调试用） |
| F6 | 性能面板：各渲染阶段的 CPU 和 GPU 耗时 |

### 设置页面

按 F10 打开。共五个分区：

- **阳光与阴影**：统一 HDR 光照、PBR 材质、环境反射、水面倒影、白天/夜晚/室内亮度、太阳投影、云影、接触阴影。
- **局部光与动态光**：路灯、火光等点光源的强度、范围、反弹光和投影。
- **氛围**：远景雾、粒子（萤火虫、火星、雨雪）、地面薄雾。
- **HDR、泛光与景深**：曝光、泛光、调色、暗角、景深、渲染比例。
- **镜头与实体**：
  - 俯视角、水平旋转；
  - 透视镜头（关闭时为正交镜头，与原版画面布局一致）；
  - 视野角度（5–30°，只对透视镜头生效）；
  - 实体高度修正，以及「按当前俯视角设为原始像素高度」按钮；
  - 人物被挡住时淡出前方的遮挡物。

改动立即生效。「保存设置」只写入 `Mods/SDV-HD2D/config.json`，不会改动存档；「恢复默认」把整页设置恢复为默认值。界面文字跟随游戏语言（中文、英文）。

### 镜头与鼠标

- 默认是正交镜头，俯视角 40°、水平旋转 0°：3D 画面与原版画面的位置完全重合。
- 打开透视镜头、加大视野角度或转动镜头，立体感更强，但能看到的地面更多，开销也更大。
- 鼠标指向的就是画面上看到的东西：点地面、作物、箱子或人物，作用的都是 3D 画面里光标下的那个。
  - 平地上，任何镜头都是精确的；
  - 透视或转动镜头时，在悬崖边和斜坡上可能偏一格；
  - 分屏时鼠标按原版的屏幕布局。

### 性能

在开发机上（2560×1440 无边框全屏，垂直同步开），全部效果开启时：

- 默认镜头：所有测过的地点都是 60 FPS，最重的农场和夜晚的沙龙每帧 CPU 约 13 ms。
- 透视镜头、视野 12°：同样 60 FPS。
- 透视镜头、视野 30°：农场约 54 FPS，早晨的森林约 58 FPS，Town 和沙龙 60 FPS。

帧率上限由游戏自己的「垂直同步」选项决定（开启时等于显示器刷新率）。帧率不够时，依次尝试：

1. 调低「渲染比例」；
2. 关闭「太阳投影」或「点光投影阴影」；
3. 关闭「景深」；
4. 透视镜头时调小视野角度。

### 设置文件

`Mods/SDV-HD2D/config.json` 在第一次启动时生成。设置页面覆盖了所有画面设置；游戏关闭时也可以直接编辑这个文件。另外几项：

- `ShowFrameRate`：左上角的 FPS 数字，默认开启，设为 `false` 关闭。
- `StageEnabled`：3D 画面总开关（等同 F8）。
- `DebugGridEnabled`、`DebugCellsEnabled`、`DebugGroupsEnabled`：调试叠加层，默认关闭。
- `AutoLoadSaveFolder`：仅开发用，普通启动不读取。

## 4. 报告问题

- 按 F11 记下出问题的格子坐标 `x,y`，以及地点和游戏时间，最好附截图。
- 性能问题：按 F6 看各阶段耗时，或在 SMAPI 控制台输入 `hd2d_profile dump`，结果写到 `Mods/SDV-HD2D/.dev/screenshots/frame-profile.json`。
- 附上 SMAPI 日志：打开 [smapi.io/log](https://smapi.io/log)，上传 `%appdata%\StardewValley\ErrorLogs\SMAPI-latest.txt`，把生成的链接发给作者。
- 控制台命令：
  - `hd2d_shot [名字]`：截图到 `Mods/SDV-HD2D/.dev/screenshots`；
  - `hd2d_settings reset`：恢复默认设置，`hd2d_settings save` 保存；
  - `hd2d_stage`、`hd2d_cells`：同 F8、F11。

## 5. 常见问题

- **启动时提示缺少 StardewUI**：按第 1 节安装 StardewUI，并确认 `Mods/StardewUI/manifest.json` 存在（不要多套一层文件夹）。
- **按 F10 没有设置页面**：StardewUI 没有加载。在 SMAPI 控制台或日志里搜索 `StardewUI` 和 `SDV-HD2D` 的报错。
- **画面变回原版的 2D**：可能误按了 F8，再按一次即可。夜间农场事件（女巫、仙子、陨石）和事件自带的特殊场景本来就保持原版画法。
- **鼠标偏了一格**：多半是在透视或转动的镜头下、悬崖边或斜坡上。切回正交镜头（F9，或在设置页关闭「透视镜头」）即可精确。
- **帧率低**：见「性能」一节。

## 6. 已知限制（公测）

- 钓鱼小游戏、战斗伤害数字、心事件和节日已经做成 3D，但还没在实际游玩中充分验证，遇到异常请反馈。
- 夜间农场事件和事件自带的特殊场景保持原版 2D；少数特殊光照情况会在那一帧使用原版光照。
- 少数地形位置从地图美术推导得还不够准确，例如森林和山区两道下面没有崖壁的小瀑布。
- 其他模组：
  - 修改美术素材的模组正常生效；
  - 修改地图的模组会得到通用场景，没有手工调整的细节；
  - 用自己方式绘制世界图像的模组，这些图像可能显得扁平或错位；
  - 自带光照或着色器的模组可能冲突；
  - 自己读取光标的模组仍按原版的屏幕布局。
- 多人联机和分屏未测试。

---

# SDV-HD2D installation and usage

Version 0.9.0 (public beta).

SDV-HD2D renders Stardew Valley in the Octopath Traveler HD-2D style: the game's own pixel art on a lit 3D stage, with shadows, glowing lamps, bloom, depth of field, cloud shadows and 3D weather. It changes rendering only, never gameplay, and never writes your save.

## 1. Requirements

| What | Version | Where | Notes |
|---|---|---|---|
| Stardew Valley (PC) | 1.6.15 | Steam / GOG | required |
| SMAPI | 4.5.2 or later | [smapi.io](https://smapi.io) | required: the mod loader |
| StardewUI (by focustense) | 0.6.1 or later | [Nexus Mods #28870](https://www.nexusmods.com/stardewvalley/mods/28870), [GitHub releases](https://github.com/focustense/StardewUI/releases) | required: draws the settings page |

- Nothing else is needed. Keep SMAPI's own Console Commands and Save Backup.
- Developed and tested on Windows with SMAPI 4.5.2 and StardewUI 0.6.1. Linux, macOS and community forks of StardewUI (such as StardewUI Continued) are untested.
- Without StardewUI, SMAPI reports the missing dependency at launch and does not load this mod.

## 2. Install

1. **Install SMAPI** (skip if you have it)
   1. Launch the game once, then quit.
   2. Download SMAPI from [smapi.io](https://smapi.io), unzip it, run `install on Windows.bat` and follow the prompts.
   3. On Steam, the installer prints a launch option like `"…\Stardew Valley\StardewModdingAPI.exe" %command%`. Paste the whole line, quotes and `%command%` included, into Steam: Library → right-click Stardew Valley → Properties → General → Launch Options. For GOG, Xbox and others, follow [smapi.io/install](https://smapi.io/install).
2. **Install StardewUI**: unzip it into the game's `Mods` folder, so that `Mods/StardewUI/manifest.json` exists.
3. **Install SDV-HD2D**: unzip `SDV-HD2D-0.9.0.zip` into `Mods`, so that `Mods/SDV-HD2D/manifest.json` exists.
4. **Start the game** from Steam as usual, or run `StardewModdingAPI.exe` in the game folder. The SMAPI console lists `SDV-HD2D 0.9.0 by ivory` and `StardewUI 0.6.1`.

**Update**: quit the game and unzip the new version over `Mods`. The zip holds no `config.json`, so your settings stay.

**Uninstall**: delete `Mods/SDV-HD2D`. Saves are not affected.

## 3. Use

| Key | |
|---|---|
| F10 | open or close the HD2D settings (also the sun tab beside Options in the game menu) |
| F8 | 3D on or off, to compare with the original game |
| F9 | switch orthographic / perspective camera |
| F11 | cell grid: every map cell on screen labelled `x,y`, to report a problem |
| F7 | world grid (a debugging aid) |
| F6 | performance overlay: CPU and GPU time per render stage |

**Settings page** (F10). Five sections:
- Sunlight & Shadows;
- Local & Dynamic Lights;
- Atmosphere;
- HDR, Bloom & Depth of Field;
- Camera & Entities: pitch, yaw, perspective camera, field of view (5–30°, perspective only), entity height correction with its fit-to-pitch button, and fading what hides a character.

Changes apply at once. **Save** writes `Mods/SDV-HD2D/config.json` only, never your save; **Reset** restores the page's defaults. The page follows the game's language (English, Chinese).

**Camera and mouse**
- The default orthographic camera (pitch 40°, yaw 0°) lays the 3D world exactly where the game draws it.
- A perspective camera, a wider field of view or a turned camera look more three-dimensional, but show more ground and cost more.
- The mouse targets what you see: clicking the ground, a crop, a chest or a character acts on what is under the cursor in the 3D picture.
  - On flat ground this is exact under every camera.
  - A perspective or turned camera can be a tile off at cliff edges and on slopes.
  - In split screen the mouse keeps the game's own screen layout.

**Performance**, on the development PC (2560×1440 borderless, vsync on, everything enabled):
- Default camera: 60 FPS everywhere measured; the heaviest spots (the farm, the Saloon at night) take about 13 ms of CPU per frame.
- Perspective, field of view 12°: 60 FPS as well.
- Perspective, field of view 30°: the farm about 54 FPS, the Forest in the morning about 58, Town and the Saloon 60.

The game's own VSync option caps the frame rate at the display's refresh rate. If the frame rate drops, try in order:
1. lower Render scale;
2. turn off Cast shadows or Point projection shadows;
3. turn off Depth of field;
4. with a perspective camera, narrow the field of view.

**config.json** is written at first launch. The settings page covers every visual setting; you can also edit the file while the game is closed. Other fields:
- `ShowFrameRate`: the FPS counter at the top left, on by default; set `false` to hide it.
- `StageEnabled`: the 3D stage (as F8).
- `DebugGridEnabled`, `DebugCellsEnabled`, `DebugGroupsEnabled`: debugging overlays, off by default.
- `AutoLoadSaveFolder`: development only; a normal launch ignores it.

## 4. Reporting a problem

- Press F11 and note the `x,y` of the cell that looks wrong, with the location and the time of day. A screenshot helps.
- For performance, press F6, or run `hd2d_profile dump` in the SMAPI console; it writes `Mods/SDV-HD2D/.dev/screenshots/frame-profile.json`.
- Upload `%appdata%\StardewValley\ErrorLogs\SMAPI-latest.txt` at [smapi.io/log](https://smapi.io/log) and share the link.
- Console commands:
  - `hd2d_shot [name]` saves a screenshot to `Mods/SDV-HD2D/.dev/screenshots`;
  - `hd2d_settings reset` restores the defaults, `hd2d_settings save` keeps them;
  - `hd2d_stage` and `hd2d_cells` do the same as F8 and F11.

## 5. Troubleshooting

- **SMAPI says StardewUI is missing**: install it (section 1) and check that `Mods/StardewUI/manifest.json` exists, with no extra folder level.
- **F10 shows no settings page**: StardewUI did not load. Look for `StardewUI` and `SDV-HD2D` errors in the SMAPI console or log.
- **The picture is back to the original 2D**: F8 may have been pressed; press it again. Overnight farm events (the witch, the fairy, meteorites) and an event's own custom scene keep the game's drawing by design.
- **The mouse is a tile off**: most likely a perspective or turned camera at a cliff edge or on a slope. The orthographic camera (F9, or Perspective camera off) is exact.
- **Low frame rate**: see Performance.

## 6. Known limits (beta)

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

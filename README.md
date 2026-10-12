# DZToolbench

A Windows toolbench for DayZ modding. Build your mod and join a local test
server in one click, read the game's logs as they're written, check your
scripts with DayZ's own compiler, and edit layouts, stringtables and
types.xml. It also makes textures, materials and colour variants, all in
one window.

It only uses plain text files and Bohemia's own tools (DayZ Tools'
AddonBuilder, ImageToPAA...). It never writes into your published mods or
Steam's Workshop folder.

---

## What's inside

**Home**
- Your mod at a glance: when it was last built, files changed since then, and problems from the last session.
- A mod switcher for every mod on your P:\ drive.
- **New mod**, which makes a ready-to-build mod folder.

**Logs**
- Follows DayZ's script, RPT and crash logs live.
- Groups repeats, so one crash happening 30,000 times is one row with a count.
- Shows stack traces, and opens the file at the right line in VS Code.
- Filters by severity, source and text.
- A Windows notification when DayZ crashes while you're in game.

**Script Check**
- Compiles your mod with DayZ's real script compiler (a hidden DayZ Server, about 20 seconds).
- Shows each module as it compiles: GameLib, Game, World, Mission.
- When an override doesn't match, it shows your method and vanilla's one under each other.
- Warns about files that start with a BOM before you even pack.

**Build & Launch**
- One click packs your mod with AddonBuilder, starts a local test server with BattlEye off, and starts DayZ connected to it. About a minute from click to in game.
- A checklist of server mods that edits your `TestServer.bat` mod list directly.
- Shows each PBO's `$PBOPREFIX$` and can create missing ones.

**Layouts**
- A visual editor for `.layout` files, previewed at 1920x1080 with DayZ's own fonts and translated text.
- Drag, resize and snap.
- Add, copy, paste, duplicate and rename widgets.
- Colours (with a colour picker), fonts, text, images and switches.
- Undo.
- Saving changes only the lines you edited and checks the result before writing.

**Strings**
- Edit `stringtable.csv` in a table with every language.
- Saving keeps everything you didn't touch exactly as it was.

**Textures**
- **_smdi converter:** turns PBR (BaseColor/Metallic/Roughness) or Spec/Gloss maps into DayZ's `_smdi.paa`, with a preview before converting. One texture or a whole folder.
- **View .paa:** look inside any `.paa`: colours, each channel, alpha and size. Save it as PNG.
- **Make .rvmat:** writes a material the way vanilla does, with presets taken from vanilla's own materials and optional `_damage` / `_destruct` versions.
- **Make variant:** a colour variant of an item (yours or vanilla's) as a ready-to-paste config.cpp class, written like vanilla's own `M4A1_Green` or `Mosin9130_Camo`.

**Types**
- A types.xml editor that knows your mod. It finds your spawnable items in your config.cpp files and adds them with your default numbers.
- Templates (Very rare ... Very common), and editing many entries at once.
- Category, usage, value and tag chips from the server's own limits file.
- Checks for typos, duplicates and base classes that never spawn.
- Each mod keeps its own types.xml.

**Settings**
- UI size, DayZ / DayZ Server folders (it finds them in your Steam libraries), what it keeps on disk, keyboard shortcuts, version and updates.

---

## What you need

- Windows 10 or 11, 64-bit.
- **DayZ** and **DayZ Tools** from Steam, with the **P:\ work drive** mounted (DayZ Tools' Work Drive) and the game data extracted to it.
- **DayZ Server** from Steam, for Build & Launch and Script Check.
- Optional:
  - **VS Code** with its `code` command, for "Open in VS Code" from the logs.
  - A `TestServer.bat` and `TestServer.cfg` in your DayZ Server folder. If they're there, DZToolbench uses their mod list and settings. If not, it uses `serverDZ.cfg` and the mods you list in Build & Launch.

You don't need to install .NET: the download is one self-contained `.exe`.

---

## Getting started

1. Download `DZToolbench.exe` from the [Releases](../../releases) page.
2. Put it anywhere and run it. The first start is a moment slower while Windows unpacks it.
3. It finds DayZ, DayZ Server and DayZ Tools by itself. Check **Settings** if something shows a red cross.
4. Pick your mod on **Home** (or make one with **New mod**), then press **Build & Launch**.

---

## Good to know

- **It never writes into `@PublishedMods` or `!Workshop`.** Test builds go to DZToolbench's own folder.
- **BattlEye is turned off only for the local test server it starts,** in its own copy of your server config. Your config files aren't changed.
- **Your settings and backups** live in `%LOCALAPPDATA%\DZToolbench`. That includes a copy of every layout, types.xml and TestServer.bat before DZToolbench changes it.
- **Update check:** when it starts, DZToolbench asks GitHub for the newest release of this repository. If there's a newer one, the version under its name says so, and a click opens the download page. Only that one request is made, with nothing about you or your mods in it. Nothing is downloaded or installed automatically.

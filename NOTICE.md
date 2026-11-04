# KAMEN RIDER - PC

PC port by **Indra Sundanese**.

A PC runtime and launcher for two PlayStation 4 games: **KAMEN RIDER memory of heroez** (CUSA17374)
and **KAMEN RIDER Climax Fighters** (CUSA09534, local multiplayer for up to 4 players).
The game's own x86-64 code runs directly on the PC's processor; the PS4 system libraries are
implemented on the PC; the GPU commands and shaders are translated to Vulkan.

No game files are included. You need dumps of the games from your own console.

## What this project adds

- A dedicated build of the shadPS4 core for these games (`bin\kmoh-core.exe`), with these changes
  (patch files in the source repository):
  - `patches/0001-window-title-from-env.patch`: the window is named after the game.
  - `patches/0002-game-icon-and-version-info.patch`: the game's icon and name in the exe
    (the icon is made from the game's own `sce_sys\icon0.png`).
  - `patches/0003-cache-dir-from-env.patch`: the shader / pipeline cache folder can be chosen in the launcher.
  - `patches/0004-keyboard-players-from-env.patch`: the launcher can log in players 2-4 at start, so players
    without a controller can join with the keyboard.
  - `patches/0005-log-path-of-failed-stat.patch`: failed file lookups name the file in the log.
  - `patches/0006-libc-mspace-and-cxa-guards.patch`: the system C library's private heaps (sceLibcMspace*)
    and C++ static-initialisation guards; without them the PSN toolkit cannot start and Climax Fighters
    stays on a black screen after the Unity logo.
  - `patches/0007-trophy-placeholders-without-trophy-key.patch`: when the trophy files cannot be read,
    trophy queries get neutral placeholder answers (all locked) instead of empty data, so games that
    wait for them (Climax Fighters) can finish booting.
  Everything is linked into one exe (Visual Studio / clang-cl build), so there are no separate library DLLs.
- The KAMEN RIDER PC launcher (dark theme, by Indra Sundanese): game choice, game folders, control mapping
  for keyboard (per player) and controller, players and player names, shader cache folder, window mode and size, render resolution (up to the PS4's 1080p),
  AMD FSR 1 upscaling and RCAS sharpening, 30 / 60 FPS, VSync, FPS counter, language, confirm button,
  and the save, log and cache folders. Settings are kept in `user\` (portable).
- 60 FPS for memory of heroez: the game waits two display refreshes per frame (30 FPS on PS4); the runtime's virtual display
  runs at 120 Hz instead of 60 Hz. No game file is changed. Experimental. (Climax Fighters already runs at
  60 FPS and keeps the 60 Hz display.)

## What this project is built on

| Work | Author | License |
|---|---|---|
| **shadPS4**: the whole runtime - loader, PS4 system libraries, GPU command processor, shader recompiler (GCN to SPIR-V) and the Vulkan renderer, including FSR 1 / RCAS | shadPS4 team and contributors | GPL-2.0-or-later |
| SDL3, Vulkan headers and loader, Vulkan Memory Allocator, glslang, sirit, Dear ImGui, FFmpeg, OpenAL Soft, LibAtrac9, fdk-aac, fmt, spdlog, nlohmann json, toml11, zlib-ng, zstd, xbyak, Zydis, magic_enum, robin-map, half, xxHash, Boost, LibreSSL, and the other libraries in shadPS4's `externals` | their authors | their own licenses |
| AMD FidelityFX Super Resolution 1 (FSR 1) | AMD | MIT |

Approach inspired by the native PC ports of Bloodborne (bloodborne_pc), God of War III (SpartanPort)
and Sengoku Basara 4 Sumeragi (Basara 4 PC by Razz), which also build on shadPS4.

## License

GNU General Public License, version 2 or (at your option) any later version. See `LICENSE`.
Anyone who receives a build of this project is entitled to its source code, including the changes.

"KAMEN RIDER", "memory of heroez" and "Climax Fighters" are trademarks of their owners (Ishimori Production, Toei,
Bandai Namco Entertainment). This project is not affiliated with them or with Sony Interactive Entertainment.

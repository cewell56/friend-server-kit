# Legacy tools (reference only)

The kit starts as a port of PowerShell tools that already run on Chandler's PC under `C:\Users\Chand\source\autopilot-team\tools`. They are **not** copied into this repo: they carry his server addresses, friend names and local paths. Port the behavior, not the files.

| Script | What it does | Lands in |
| --- | --- | --- |
| `pack_plan.ps1` | Modrinth slugs + version → resolved plan (TSV) with `@server`/`@both` side hints | `Kit.Core.Packs` |
| `pack_install.ps1` | Applies a plan to a mods folder per side, moves strays aside | `Kit.Core.Packs` |
| `mrpack_public.ps1` | Builds a `.mrpack` with sha1/sha512 and a `servers.dat` override | `Kit.Core.Packs` |
| `lynx_server.ps1` / `public_server.ps1` | Fabric server install, properties, JVM flags, start/stop, fresh world | `Kit.Core.Server` |
| `rcon_lib.ps1` | RCON client (`Connect-Rcon`, `Send-Rcon`) | `Kit.Core.Server` |
| `run_manager.ps1`, `build_board.ps1`, `reset_levers.ps1` | Hardcore run lifecycle, pregen wait, lever board | later |
| `tunnel_diag.ps1`, `playit_*.ps1` | playit agent state, real Minecraft status ping through the tunnel | `Kit.Core.Tunnel` |
| `friend_exe_public.ps1`, `friend_pack_public.ps1` | Self-extracting join exe, friend zip, last-good address | `FriendServerKit join` |
| `public_profile_me.ps1` | Launcher profile creation and server-list entry | `Kit.Core.Launcher` |

Known gotchas learned the hard way, keep them: `launcher_profiles.json` must be written without a UTF-8 BOM or the launcher resets to defaults; a TCP-open on a playit tunnel proves nothing, do the handshake; Fabric API is not needed by Baritone but is by most mods; CurseForge-only mods can be opted out of third-party download.

# Backlog

Ordered. Each item has acceptance criteria; an item is done when they all pass on this PC. Tick with the date.

## Week 1 — one installer that does what the scripts do

- [ ] **1. Solution skeleton.** `src/FriendServerKit.sln`: a .NET 10 self-contained single-file WinForms (or WPF) app `FriendServerKit`, a class library `Kit.Core`, and `Kit.Tests` (xunit). `dotnet build` and `dotnet test` green. GitHub Actions workflow on `windows-latest` builds and uploads the exe as an artifact on every push to `dev`.
- [ ] **2. Pack planner port.** `Kit.Core.Packs`: given a list of Modrinth slugs (with `@server`/`@both` side hints) and a Minecraft version, resolve the newest compatible version of each, pull dependencies, read every jar's `fabric.mod.json` for `depends`/`breaks`, and fail loudly on a conflict. Output a plan (JSON) and an `.mrpack`. Tests cover: a clean plan, a missing 26.3 build, a `breaks` conflict. Reference: `pack_plan.ps1`, `pack_install.ps1`, `mrpack_public.ps1` in the legacy tools folder.
- [ ] **3. Server setup port.** `Kit.Core.Server`: install Fabric for a chosen version into a folder, write `server.properties` (online-mode on by default, whitelist on, RCON on with a generated password), JVM flags by RAM, start/stop/status, RCON client. Smoke test: a throwaway server starts and answers a status ping. Reference: `lynx_server.ps1`, `rcon_lib.ps1`, `public_server.ps1`.
- [ ] **4. Tunnel.** Detect the playit agent, show the assigned hostname, run the real Minecraft status ping through it (handshake + status request, not just a TCP open). Reference: `tunnel_diag.ps1`, `playit_*.ps1`. If playit is missing, link to its installer; never install it silently.
- [ ] **5. First exe.** The app walks: pick a pack → RAM → start server → tunnel → whitelist names → "share this". Pre-release `v0.1.0-alpha` with the exe attached.

## Week 2 — friends join, packs published, people see it

- [ ] **6. Join mode.** `FriendServerKit.exe join <code or link>`: installs the Fabric loader for the launcher, downloads the pack's mods from the Modrinth CDN into a dedicated profile folder, adds the launcher profile (`launcher_profiles.json`, written without a BOM, launcher closed check) and the server entry (`servers.dat`), launches. Also exports the `.mrpack` for Prism / Modrinth App users. Reference: `friend_exe_public.ps1`, `friend_pack_public.ps1`, the launcher-profile scripts.
- [ ] **7. Two packs, published.** Build and publish under Chandler's accounts (tokens in his secrets file, see `AGENT.md`): "Vanilla+ Hardcore Co-op" (the list in `docs/PLAN.md`) and a shader-ready performance pack. Each description links the kit. Draft the Modrinth descriptions first in `drafts/`.
- [ ] **8. Landing page.** `site/` static page for Netlify: what it is, a 60-second clip placeholder, download button to the latest release, Discord invite placeholder, no "AI". Chandler deploys.
- [ ] **9. Launch drafts.** `drafts/reddit-feedthebeast.md`, `drafts/reddit-admincraft.md`, `drafts/modrinth-discord.md`, `drafts/video-script.md` — in Chandler's voice, "I made something" tone, honest about alpha status.

## Weeks 3–4 — harden, measure, hosting hook

- [ ] **10. Stranger-proofing.** Fix every issue from the first testers: Java detection, launcher not installed, antivirus/SmartScreen notes, non-ASCII Windows usernames, OneDrive-redirected AppData.
- [ ] **11. Numbers.** A `kit stats` command and a report script: release download counts (GitHub API), pack downloads (Modrinth API), and a counter for hosting-button clicks (a Netlify redirect with a count, no tracking of users). Numbers go in every daily entry.
- [ ] **12. Hosting hook.** "Want it up 24/7? Move this server to a host" button that exports the server folder as a zip and opens the partner link. Partner code only once a program accepts Chandler; until then the button opens a plain comparison page.
- [ ] **13. Day-30 report.** 2026-10-31: the four numbers against the gate, in `DAILY.md`, the doc, and a push notification.

## Later (not before day 30)

- Public chat builder behind a per-user cap; CurseForge import; pack sync for a group; scheduled hardcore resets and the run board; white-label pitch for independent hosts.

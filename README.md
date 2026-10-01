# Friend-Server Kit

Turn a gaming PC into a modded Minecraft server for your friend group in one click.

- **Pack**: a compatibility-checked Fabric modpack, resolved from Modrinth (CurseForge import later). Every mod's `depends`/`breaks` is verified before it ships; nothing is bundled, mods download from the platforms' own CDNs at install time.
- **Server**: Fabric server on this PC with sane JVM flags, optional pregen, whitelist, RCON ops, hardcore run resets.
- **Tunnel**: friends connect without port forwarding (playit.gg), or over Tailscale for a private group.
- **Join**: one link or exe for the friends — it installs the loader, pulls the mods, adds the launcher profile and the server entry, and launches.

Free. Windows first. Open source (MIT).

## Status

Day 0 — repo seeded, plan written, daily build agent scheduled. See `STATUS.md`, `BACKLOG.md`, and `DAILY.md`.

## Layout

```
AGENT.md      how the daily agent operates (rules, limits, reporting)
BACKLOG.md    the ordered work list with acceptance criteria
STATUS.md     where things stand right now
DAILY.md      one entry per run, newest first
docs/         plan summary and design notes
drafts/       public posts written by the agent for a human to post
src/          the .NET app (kit, join, builder)
legacy/       notes on the PowerShell tools this started from (not the scripts themselves)
```

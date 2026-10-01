# Plan (summary)

The full market check, wedge, validation gate and build plan live in the doc **"Modpack SaaS — Market Check and Wedge"**: https://claude.ai/code/artifact/fcb8042e-1571-4395-a27d-c1f275154aea — its **Daily log** tab is where Chandler and the agent talk.

## The one-paragraph version

A chat-to-modpack SaaS is not the business: CurseForge has it marked Planned, a free open-source copy has zero stars, the community hates "AI packs", and Fiverr does a custom pack for $5. The money in modded Minecraft is hosting. So the product is a **free Friend-Server Kit** — a gaming PC becomes a modded server for a friend group in one click (checked pack, tunnel, whitelist, one-click join for friends) — monetized through hosting referrals, published packs, and a small Pro tier only once people ask. The chat builder is the engine room, not the storefront.

## The 30-day gate (2026-10-02 → 2026-10-31)

Go if three of four: 1,000+ combined pack downloads · 100+ kit installs · 10+ custom-pack or feature requests · 3+ hosting clicks per 100 installs.
No if: under 200 downloads and under 25 installs, or the launch threads turn on it, or CurseForge ships free self-hosting of custom packs, or week 1 slips past two weekends.

## Vanilla+ co-op pack (the first published pack)

Client: iris, sodium, lithium, ferrite-core, krypton, entityculling, immediatelyfast, moreculling, badoptimizations, dynamic-fps, scalablelux, better-block-entities, ixeris, modmenu, veinminer, veinminer-client, flashback, day-counter, fabric-api. Server-only: servercore, chunky. Distant Horizons is an optional add-on (heavy). Pin to the Minecraft version the stock launcher defaults to on release day.

## Design rules

- Never bundle mod files; resolve from Modrinth (CurseForge import later) and respect third-party-download opt-outs.
- Launcher profile injection: write `launcher_profiles.json` without a BOM, only when the launcher is closed, always with a backup beside it.
- Online mode on by default; whitelist on by default; RCON password generated per server.
- "AI" never appears in the product name or the pitch.

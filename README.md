<p align="center">
  <img src="frontend/static/logo/256.png" alt="Huntarr Revisited Logo" width="120">
</p>

<h1 align="center">Huntarr Revisited</h1>

<p align="center">
  Automatically hunt missing media and clear stuck downloads for your <em>arr</em> stack.
</p>

<p align="center">
  <a href="https://discord.com/invite/ExSFH64kVn"><img src="https://img.shields.io/discord/1370922258247454821?color=7289DA&label=Discord&style=flat&logo=discord" alt="Discord"></a>
  <a href="https://github.com/mrjacobarussell/huntarr/releases"><img src="https://img.shields.io/github/v/release/mrjacobarussell/huntarr?style=flat&label=Release" alt="Release"></a>
  <a href="https://buymeacoffee.com/jacobrussell_medic"><img src="https://img.shields.io/badge/Support-Buy%20Me%20a%20Coffee-yellow?style=flat&logo=buymeacoffee" alt="Support"></a>
</p>

---

> [!IMPORTANT]
> **This fork is no longer under active development.**
>
> Huntarr Revisited served as a maintained fork of [plexguide/Huntarr.io](https://github.com/plexguide/Huntarr.io) with several additions (Swaparr quality-rejection handling, Lidarr low-match clearing, mount-aware import retry, and more). Development has concluded here.
>
> The successor project is **Sniparr** — a ground-up rewrite that keeps everything you relied on here and builds it on a modern, async-first foundation. Follow along or contribute at [github.com/mrjacobarussell/sniparr](https://github.com/mrjacobarussell/sniparr).
>
> This repository remains available as a reference and for anyone still running the existing Docker image. No further updates, bug fixes, or feature additions are planned.

---

## What It Does

Your *arr apps (Sonarr, Radarr, etc.) monitor RSS feeds for new releases — but they don't go back and search for content already in your library that never downloaded. Huntarr fills that gap.

**Missing content** — Huntarr scans your entire library, finds episodes and movies marked as missing, and triggers searches in small controlled batches so you don't hammer your indexers.

**Quality upgrades** — Finds items below your quality cutoff and queues upgrades, again in batches you control.

**Stuck downloads (Swaparr)** — Monitors your download clients for stalled or slow torrents/NZBs. After a configurable number of strikes, it removes the dead download and lets your *arr app find a replacement automatically. Also detects downloads that finished but were rejected for import due to a quality/match mismatch — these get struck and removed so a better release can be found.

---

## Supported Apps

| App | Missing | Upgrades | Swaparr |
|-----|:-------:|:--------:|:-------:|
| Sonarr | ✅ | ✅ | ✅ |
| Radarr | ✅ | ✅ | ✅ |
| Lidarr | ✅ | ✅ | ✅ |
| Readarr | ✅ | ✅ | ✅ |
| Whisparr v2 | ✅ | ✅ | ✅ |
| Whisparr v3 | ✅ | ✅ | ✅ |
| Sportarr | — | — | ✅ |

**Seed queue torrent clients:** qBittorrent · Transmission · Deluge

---

## Installation

Docker is the only supported installation method.

```yaml
services:
  huntarr:
    image: mrjacobarussell/huntarr-revisited:latest
    container_name: huntarr
    restart: unless-stopped
    ports:
      - "9705:9705"
    volumes:
      - /your/config/path:/config
      - /etc/localtime:/etc/localtime:ro
```

**Unraid**: Install via Community Applications — search for **Huntarr Revisited** or use the template URL from the repo.

---

## How It Works

1. **Connect** — Point Huntarr at your *arr instances with an API key.
2. **Configure** — Set how many missing items and upgrades to hunt per cycle, and your sleep interval between cycles.
3. **Run** — Huntarr loops continuously: scan → search → wait → repeat.
4. **Swaparr** (optional) — Enable to automatically remove stalled downloads after N strikes so your queue never stays stuck.

Hourly API caps and queue size limits are built in to keep your indexers happy.

---

## Notable Features

**Swaparr quality-rejection handling** — Downloads that complete but won't import because they don't meet the quality cutoff are no longer ignored. Swaparr detects them via `trackedDownloadState` and `statusMessages`, applies strikes over time, then removes and re-searches once the threshold is exceeded.

**Lidarr low-match queue clearing** — Per-instance toggle to bulk-remove and blacklist `importPending` queue items with warning/error status before each search cycle, so Lidarr re-searches for a better release immediately rather than leaving them stuck.

**Mount-aware import retry** — When a container starts before NFS/SMB mounts are ready, failed imports are queued and retried in the background (up to ~2 hours) instead of being permanently lost.

---

## Links

- [GitHub Issues](https://github.com/mrjacobarussell/huntarr/issues)
- [Discord](https://discord.com/invite/ExSFH64kVn)
- [Buy Me a Coffee](https://buymeacoffee.com/jacobrussell_medic)
- [Changelog](CHANGELOG.md)

---

*A fork of [plexguide/Huntarr.io](https://github.com/plexguide/Huntarr.io), originally maintained by [MrJacobarussell](https://github.com/mrjacobarussell). Archived — see [Sniparr](https://github.com/mrjacobarussell/sniparr) for the successor project.*

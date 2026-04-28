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

## What It Does

Your *arr apps (Sonarr, Radarr, etc.) monitor RSS feeds for new releases — but they don't go back and search for content already in your library that never downloaded. Huntarr fills that gap.

**Missing content** — Huntarr scans your entire library, finds episodes and movies marked as missing, and triggers searches in small controlled batches so you don't hammer your indexers.

**Quality upgrades** — Finds items below your quality cutoff and queues upgrades, again in batches you control.

**Stuck downloads (Swaparr)** — Monitors your download clients for stalled or slow torrents/NZBs. After a configurable number of strikes, it removes the dead download and lets your *arr app find a replacement automatically.

---

## Supported Apps

| App | Missing | Upgrades |
|-----|:-------:|:--------:|
| Sonarr | ✅ | ✅ |
| Radarr | ✅ | ✅ |
| Lidarr | ✅ | ✅ |
| Readarr | ✅ | ✅ |
| Whisparr v2 | ✅ | ✅ |
| Whisparr v3 | ✅ | ✅ |

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

## Links

- [GitHub Issues](https://github.com/mrjacobarussell/huntarr/issues)
- [Discord](https://discord.com/invite/ExSFH64kVn)
- [Buy Me a Coffee](https://buymeacoffee.com/jacobrussell_medic)
- [Changelog](CHANGELOG.md)

---

*A fork of [plexguide/Huntarr.io](https://github.com/plexguide/Huntarr.io), maintained by [MrJacobarussell](https://github.com/mrjacobarussell).*

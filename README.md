<h2 align="center">Huntarr - Find Missing & Upgrade Media Items</h2> 

<p align="center">
  <img src="frontend/static/logo/128.png" alt="Huntarr Logo" width="100" height="100">
</p>

<a href="https://buymeacoffee.com/jacobrussell_medic">
  <img src="https://img.shields.io/badge/Support%20Huntarr-Buy%20Me%20a%20Coffee-yellow?style=flat&logo=buymeacoffee" alt="Support Huntarr" />
</a>

---

<h2 align="center">Want to Help? Click the Star in the Upper-Right Corner! ⭐</h2> 

<img src="https://github.com/user-attachments/assets/1ea6ca9c-0909-4b6a-b573-f778b65af8b2" width="100%"/>

#### ⭐ Show Your Support for Open Source!

If Huntarr has been helpful to you and you appreciate the power of open-source software, please consider giving this repository a star. Your gesture will greatly support our efforts and help others discover Huntarr!

<div align="center">

| **Sonarr** | **Radarr** | **Lidarr** | **Readarr** |
|:----------:|:----------:|:----------:|:-----------:|
| <img src="https://img.shields.io/badge/Status-Ready-green?style=flat" alt="Ready" /> | <img src="https://img.shields.io/badge/Status-Ready-green?style=flat" alt="Ready" /> | <img src="https://img.shields.io/badge/Status-Ready-green?style=flat" alt="Ready" /> | <img src="https://img.shields.io/badge/Status-Ready-green?style=flat" alt="Ready" /> |

| **Whisparr v2** | **Whisparr v3** | **Bazarr** |
|:---------------:|:---------------:|:----------:|
| <img src="https://img.shields.io/badge/Status-Ready-green?style=flat" alt="Ready" /> | <img src="https://img.shields.io/badge/Status-Ready-green?style=flat" alt="Ready" /> | <img src="https://img.shields.io/badge/Status-Not%20Ready-red?style=flat" alt="Not Ready" /> |

</div>


## ℹ️ Overview

[![Discord](https://img.shields.io/discord/1370922258247454821?color=7289DA&label=Discord&style=for-the-badge&logo=discord)](https://discord.com/invite/PGJJjR5Cww)

This application continually searches your media libraries for missing content and items that need quality upgrades. It automatically triggers searches for both missing items and those below your quality cutoff. It's designed to run continuously while being gentle on your indexers, helping you gradually complete your media collection with the best available quality.


## ❓ Why You Need Huntarr

Huntarr is an automatic missing content hunter for Sonarr, Radarr, Lidarr, Readarr, and Whisparr.  
Think of it as the missing piece that actually completes your media automation setup by finding and downloading all the content your *arr apps aren't actively searching for.

**The problem**: Your *arr apps only monitor RSS feeds for new releases. They don't go back and search for missing episodes/movies already in your library. It's also a hard concept for many to understand the gap this creates.

**The solution**: Huntarr systematically scans your entire library, finds all missing content, and searches for it in small batches that won't overwhelm your indexers or get you banned. It's the difference between having a "mostly complete" library and actually having everything you want.


## ⬇️ Installation Methods

- 🐋 **[Docker Installation](https://plexguide.github.io/Huntarr.io/getting-started/installation.html#docker-installation)** (Recommended)
- 🔵 **[Unraid Installation](https://plexguide.github.io/Huntarr.io/getting-started/installation.html#unraid-installation)**
- 🪟 **[Windows Installation](https://plexguide.github.io/Huntarr.io/getting-started/installation.html#windows-installation)**
- 🍏 **[macOS Installation](https://plexguide.github.io/Huntarr.io/getting-started/installation.html#macos-installation)**
- 🐧 **[Linux Installation](https://plexguide.github.io/Huntarr.io/getting-started/installation.html#linux-installation)**
- 🔧 **[Alternative Methods](https://plexguide.github.io/Huntarr.io/getting-started/installation.html#alternative-methods)**


## ⚙️ How It Works

### 🔄 Continuous Automation Cycle

<i class="fas fa-1"></i> **Connect & Analyze** - Huntarr connects to your Sonarr/Radarr/Lidarr/Readarr/Whisparr/Eros instances and analyzes your media libraries to identify both missing content and potential quality upgrades.

<i class="fas fa-2"></i> **Hunt Missing Content** - Efficiently refreshes by skipping metadata to reduce disk I/O and database load, automatically skips content with future release dates, provides precise control over how many items to process per cycle, and focuses only on content you've marked as monitored.

<i class="fas fa-3"></i> **Hunt Quality Upgrades** - Finds content below your quality cutoff settings for improvement, uses batch processing to set specific numbers of upgrades per cycle, automatically pauses when download queue exceeds your threshold, and waits for commands to complete with consistent timeouts.

<i class="fas fa-4"></i> **API Management** - Implements hourly caps to prevent overloading your indexers, uses consistent API timeouts (120s) across all applications, identifies as Huntarr to all Arr applications with consistent headers, and provides visual indicators showing API usage limits.

<i class="fas fa-5"></i> **Repeat & Rest** - Huntarr waits for your configured interval (adjustable in settings) before starting the next cycle, ensuring your indexers aren't overloaded while maintaining continuous improvement of your library.

---

## 📜 Change Log
See [CHANGELOG.md](CHANGELOG.md) for the full history of changes.

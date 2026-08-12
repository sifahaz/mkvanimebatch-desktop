# MKV Anime Batch — Desktop Release

[![Latest Release](https://img.shields.io/github/v/release/sifahaz/mkvanimebatch-desktop?style=flat-square&color=blue)](https://github.com/sifahaz/mkvanimebatch-desktop/releases/latest)
[![License: GPL v3](https://img.shields.io/badge/License-GPLv3-blue?style=flat-square)](LICENSE)
[![Source Repository](https://img.shields.io/badge/Source_Code-mkvanimebatch-purple?style=flat-square&logo=github)](https://github.com/sifahaz/mkvanimebatch)

> **Official Desktop Standalone & Installer Release Repository** for [MKV Anime Batch](https://github.com/sifahaz/mkvanimebatch)  
> Streamline your anime collection with intelligent subtitle scoring, 10-tier audio filtering, font extraction & deduplication, timestamp offset shifting, and multi-threaded parallel remuxing powered by Tauri v2.

---

## Quick Downloads

Download pre-compiled standalone executables and package installers for your operating system:

| Operating System | Format | Download Link | File Name | Description |
| :--- | :--- | :--- | :--- | :--- |
| **Windows** | Standalone `.exe` | [Download .exe](https://github.com/sifahaz/mkvanimebatch-desktop/releases/latest) | `mkv-anime-batch.exe` | Single portable executable — launch directly without installation |
| **Windows** | Portable `.zip` | [Download .zip](https://github.com/sifahaz/mkvanimebatch-desktop/releases/latest) | `MKV_Anime_Batch_Portable_win64.zip` | Standalone portable zip archive |
| **Linux** | Universal `.AppImage` | [Download AppImage](https://github.com/sifahaz/mkvanimebatch-desktop/releases/latest) | `MKV.Anime.Batch_1.0.0_amd64.AppImage` | Compatible with all modern Linux distributions |
| **Linux** | Debian `.deb` | [Download .deb](https://github.com/sifahaz/mkvanimebatch-desktop/releases/latest) | `MKV.Anime.Batch_1.0.0_amd64.deb` | Package for Ubuntu, Debian, and Linux Mint |
| **Linux** | RedHat `.rpm` | [Download .rpm](https://github.com/sifahaz/mkvanimebatch-desktop/releases/latest) | `MKV.Anime.Batch-1.0.0-1.x86_64.rpm` | Package for Fedora, RHEL, CentOS, and openSUSE |

> [!NOTE]
> All desktop releases are built directly from the open-source source code at [sifahaz/mkvanimebatch](https://github.com/sifahaz/mkvanimebatch).

---

## Core Features

- **Modern Tauri v2 GUI**: Lightweight native interface featuring dark/light theme, custom processing presets, batch inspection, and live stdout/stderr log streaming.
- **Intelligent Subtitle Scoring**: Scores Advanced SubStation Alpha (`.ass`) over SubRip (`.srt`), prioritizes language preferences (Indonesian `ind`/`id`, English `eng`), evaluates format variants without premature candidate dropping, and isolates commentary tracks.
- **10-Tier Audio Selection**: Favors multi-channel Japanese dialogue tracks while isolating commentaries into secondary fallback pools.
- **Timestamp Offset Shifting**: Shift subtitle timing (e.g. `--sub-offset 5.0`) with UTF-8 BOM preservation (`utf-8-sig`) and filename encoding (`[+5s]`) for instant skip checks.
- **Atomic Operations & Crash Recovery**: Remuxes into isolated temporary working directories and moves completed output atomically upon zero exit codes to prevent corrupted files.
- **Parallel High-Throughput Engine**: Multi-threaded extraction and remuxing routines (`mkv_extract`, `mkv_remux`) with persistent JSON probe caching (`.mkv_inspect_cache.json`).

---

## System Requirements

The desktop application requires the following command-line tools installed and accessible via your system `PATH`:

1. **[MKVToolNix](https://mkvtoolnix.download/)** (`mkvmerge`, `mkvextract`) — Required for container probing, track extraction, and remuxing.
2. **[ffmpeg](https://ffmpeg.org/download.html)** — Required for audio transcoding (Opus / AAC).

---

## Installation & Setup Guide

### Windows Setup

1. Download [MKVToolNix](https://mkvtoolnix.download/#windows) and [ffmpeg](https://ffmpeg.org/download.html).
2. Ensure `mkvmerge.exe` and `ffmpeg.exe` are added to your System Environment Variables (`PATH`).
3. Download `mkv-anime-batch.exe` or `MKV_Anime_Batch_Portable_win64.zip` from the [Latest Release](https://github.com/sifahaz/mkvanimebatch-desktop/releases/latest).
4. Run `mkv-anime-batch.exe` directly.

---

### Linux Setup

#### 1. Debian / Ubuntu / Linux Mint (`.deb`)

Installing via `apt` resolves all GTK and WebKit system runtime dependencies automatically:

```bash
# 1. Install CLI prerequisites
sudo apt update
sudo apt install -y mkvtoolnix ffmpeg

# 2. Install package
sudo apt install ./MKV.Anime.Batch_1.0.0_amd64.deb
```

#### 2. Fedora / RedHat / RHEL (`.rpm`)

```bash
# 1. Install CLI prerequisites
sudo dnf install -y mkvtoolnix ffmpeg

# 2. Install package
sudo dnf install ./MKV.Anime.Batch-1.0.0-1.x86_64.rpm
```

#### 3. Universal Linux (`.AppImage`)

Works on any modern Linux distribution:

```bash
# 1. Install CLI prerequisites (e.g. Debian/Ubuntu)
sudo apt update && sudo apt install -y mkvtoolnix ffmpeg

# 2. Grant execution permission and launch
chmod +x MKV.Anime.Batch_1.0.0_amd64.AppImage
./MKV.Anime.Batch_1.0.0_amd64.AppImage
```

---

## Frequently Asked Questions

<details>
<summary><b>Why is processing failing or missing tracks?</b></summary>

Ensure both `mkvmerge` and `ffmpeg` are installed and available on your environment `PATH`. Verify by running:
```bash
mkvmerge --version
ffmpeg -version
```
in your terminal or command prompt.
</details>

<details>
<summary><b>How does subtitle timestamp shifting work?</b></summary>

Subtitles are extracted and timing offsets (e.g. `+5.0s` or `-2.5s`) are applied directly to `.ass`/`.srt` timestamp blocks while preserving original UTF-8 BOM encoding. Video and audio streams are preserved without re-encoding.
</details>

<details>
<summary><b>Where is the main source code?</b></summary>

The core Python library, CLI commands, test suites, and Tauri frontend source code are hosted in the main repository:  
👉 **[github.com/sifahaz/mkvanimebatch](https://github.com/sifahaz/mkvanimebatch)**
</details>

---

## License

Distributed under the **GNU General Public License v3.0**. See [LICENSE](LICENSE) for details.

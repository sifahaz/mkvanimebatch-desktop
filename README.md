# MKV Anime Batch — Desktop Release

> **Automated High-Performance Anime MKV Batch Processing Suite & Tauri GUI**  
> Streamline your anime collection with intelligent subtitle scoring, 10-tier audio filtering, font deduplication, timestamp offset shifting, and multi-threaded parallel remuxing.

---

## Quick Downloads

Download pre-compiled standalone executables for your operating system:

| Operating System | Package Type | Download Link | Notes |
| :--- | :--- | :--- | :--- |
| **Windows** | Portable `.exe` | [Download mkv-anime-batch.exe](https://github.com/sifahaz/mkvanimebatch-desktop/releases/latest) | Standalone portable executable (no installer required) |
| **Linux** | Universal `.AppImage` | [Download AppImage](https://github.com/sifahaz/mkvanimebatch-desktop/releases/latest) | Compatible with all modern Linux distributions |
| **Linux** | Debian `.deb` | [Download .deb Package](https://github.com/sifahaz/mkvanimebatch-desktop/releases/latest) | Package for Ubuntu, Debian, and Linux Mint |

---

## Core Features

- **Modern Tauri GUI**: Built with Tauri v2 featuring responsive dark/light theme, real-time stdout/stderr log streaming, and custom processing presets.
- **Intelligent Subtitle Selection**: Scores Advanced SubStation Alpha (`.ass`) over SubRip (`.srt`), supports language priorities (Indonesian `ind`/`id`, English `eng`), evaluates format variants without premature candidate discarding, and excludes commentary tracks.
- **10-Tier Audio Picker**: Favors multi-channel Japanese dialogue tracks while isolating commentary into fallback pools.
- **Timestamp Offset Shifting**: Shift subtitle timing (`--sub-offset 5.0`) with UTF-8 BOM preservation (`utf-8-sig`) and filename offset encoding (`[+5s]`) for instant skip checks.
- **Atomic Operations & Recovery**: All jobs execute within isolated temporary working directories and move output files atomically upon zero exit codes to prevent corrupted files.
- **Parallel Engine**: Multi-threaded extraction and remuxing routines (`mkv_extract_fast`, `mkv_remux_fast`) with persistent JSON probe caching (`.mkv_inspect_cache.json`).

---

## System Requirements

The desktop application requires the following command-line tools installed and accessible via your system `PATH`:

1. **[MKVToolNix](https://mkvtoolnix.download/)** (`mkvmerge`, `mkvextract`) — Required for container probing, track extraction, and remuxing.
2. **[ffmpeg](https://ffmpeg.org/download.html)** — Required for audio transcoding (Opus / AAC).

---

## Installation Guide

### Windows Setup

1. Download and install [MKVToolNix](https://mkvtoolnix.download/#windows) and [ffmpeg](https://ffmpeg.org/download.html).
2. Ensure `mkvmerge.exe` and `ffmpeg.exe` are added to your System Environment Variables (`PATH`).
3. Download `mkv-anime-batch.exe` from the latest release and run it directly.

---

### Linux Setup (Debian / Ubuntu / Linux Mint)

#### Option A: `.deb` Package (Recommended)
Installing via `apt` resolves all GTK and WebKit system runtime dependencies automatically:

```bash
# 1. Install CLI prerequisites
sudo apt update
sudo apt install -y mkvtoolnix ffmpeg

# 2. Install package
sudo apt install ./MKV_Anime_Batch_0.1.0_amd64.deb
```

#### Option B: `.AppImage` (Universal)
```bash
# 1. Install CLI prerequisites
sudo apt update
sudo apt install -y mkvtoolnix ffmpeg

# 2. Grant execution permission and launch
chmod +x MKV_Anime_Batch_0.1.0_amd64.AppImage
./MKV_Anime_Batch_0.1.0_amd64.AppImage
```

---

## Frequently Asked Questions

<details>
<summary><b>Why is processing failing or missing tracks?</b></summary>

Ensure both `mkvmerge` and `ffmpeg` are installed and available on your environment `PATH`. Verify by running `mkvmerge --version` and `ffmpeg -version` in terminal/command prompt.
</details>

<details>
<summary><b>How does subtitle shifting work?</b></summary>

Subtitles are extracted and timing offsets (e.g. `+5.0s` or `-2.5s`) are applied directly to `.ass`/`.srt` timestamp blocks while preserving original UTF-8 BOM encoding. Video and audio streams are preserved without re-encoding.
</details>

---

## License

Distributed under the **MIT License**.

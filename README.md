# 🎬 MKV Anime Batch — Desktop Release

> **Automated High-Performance Anime MKV Batch Processing Suite & Tauri GUI**  
> Streamline your anime collection with intelligent subtitle scoring, 10-tier audio filtering, font deduplication, timestamp offset shifting, and ultra-fast parallel remuxing.

---

## ⚡ Quick Download

Download the latest pre-compiled standalone executable for your operating system:

| Operating System | Package Type | Download Link | Quick Note |
| :--- | :--- | :--- | :--- |
| 🪟 **Windows** | Portable `.exe` | [**Download mkv-anime-batch.exe**](https://github.com/sifahaz/mkvanimebatch-release/releases/latest) | Standalone, no installation required |
| 🐧 **Linux** | Universal `.AppImage` | [**Download AppImage**](https://github.com/sifahaz/mkvanimebatch-release/releases/latest) | Works on all modern Linux distributions |
| 🐧 **Linux** | Debian `.deb` | [**Download .deb Package**](https://github.com/sifahaz/mkvanimebatch-release/releases/latest) | Native install for Ubuntu / Debian / Mint |

---

## 🔥 Key Features

- 🎨 **Modern Liquid Glass GUI**: Built with Tauri v2 featuring dynamic dark mode, real-time stdout/stderr log streaming, and preset toggles.
- 💬 **Intelligent Subtitle Engine**: Automatic scoring for `.ass` typesetting over `.srt`, language fallback (Indonesian `ind` / `id` & English `eng`), format variant coexistence, and commentary filtering.
- 🔊 **10-Tier Audio Picker**: Favors multi-channel Japanese dialogue tracks while safely isolating voice-actor/director commentary into secondary fallback pools.
- ⏱️ **Timestamp Offset Shifting**: Shift subtitle timing (`--sub-offset 5.0`) with UTF-8 BOM preservation and filename encoding (`[+5s]`) for instant skip checks.
- 🛡️ **Atomic & Safe Recovery**: Work is isolated in temporary job folders; outputs are atomically moved only on successful exit codes to prevent corrupted files.
- 🚀 **Parallel Performance**: Multi-threaded execution (`mkv_extract_fast`, `mkv_remux_fast`) with persistent JSON inspect caching (`.mkv_inspect_cache.json`).

---

## 🛠️ System Prerequisites

For **MKV Anime Batch** to process video files, ensure the following command-line tools are installed on your system and accessible via `PATH`:

1. **[MKVToolNix](https://mkvtoolnix.download/)** (`mkvmerge`, `mkvextract`) — Required for MKV inspection, extraction, and remuxing.
2. **[ffmpeg](https://ffmpeg.org/download.html)** — Required for audio transcoding (Opus / AAC).

---

## 💻 Installation & Setup Guide

### 🪟 Windows Setup

1. **Install Prerequisites**:
   - Download and install [MKVToolNix](https://mkvtoolnix.download/#windows) and [ffmpeg](https://ffmpeg.org/download.html).
   - Ensure `mkvmerge.exe` and `ffmpeg.exe` are added to your System Environment Variables (`PATH`).
2. **Run the App**:
   - Download `mkv-anime-batch.exe`.
   - Double-click to launch the GUI.

---

### 🐧 Linux Setup (Debian / Ubuntu / Mint)

#### Method 1: `.deb` Package (Recommended)
Installing via `apt` automatically resolves system UI dependencies (`libwebkit2gtk-4.1`, `libgtk-3-0`):

```bash
# 1. Install prerequisites
sudo apt update
sudo apt install -y mkvtoolnix ffmpeg

# 2. Install the package
sudo apt install ./MKV_Anime_Batch_0.1.0_amd64.deb
```

#### Method 2: `.AppImage` (Universal)
```bash
# 1. Install prerequisites
sudo apt update
sudo apt install -y mkvtoolnix ffmpeg

# 2. Make executable & run
chmod +x MKV_Anime_Batch_0.1.0_amd64.AppImage
./MKV_Anime_Batch_0.1.0_amd64.AppImage
```

---

## ❓ Frequently Asked Questions (FAQ)

<details>
<summary><b>Q: Why is the application not processing any files?</b></summary>

> **A:** Make sure `mkvmerge` and `ffmpeg` are correctly installed and added to your system `PATH`. You can verify this by opening a Command Prompt / Terminal and running `mkvmerge --version` and `ffmpeg -version`.
</details>

<details>
<summary><b>Q: How does the subtitle shifting work?</b></summary>

> **A:** When you enter a shift offset (e.g., `5.0` seconds or `-2.5` seconds), the app rewrites all event timestamps in the extracted `.ass`/`.srt` files without altering video or audio streams.
</details>

---

## 📄 License

Distributed under the **GNU General Public License v3.0**.

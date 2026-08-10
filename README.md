# GStreamer2 (Wayland-Free)

```bash
   ___________ __                                      ___ 
  / ____/ ___// /_________  ____ _____ ___  ___  _____/__ \
 / / __ \__ \/ __/ ___/ _ \/ __ `/ __ `__ \/ _ \/ ___/__/ /
/ /_/ /___/ / /_/ /  /  __/ /_/ / / / / / /  __/ /   / __/ 
\____//____/\__/_/   \___/\__,_/_/ /_/ /_/\___/_/   /____/

```

Patched, Wayland-free, GStreamer2 core framework.

A strictly Wayland-free compilation of the GStreamer multimedia framework, optimized for the GNU Operating System / H-Linux environment.

---

## 📌 Overview
This repository provides the blueprint to compile a custom `2.00.1` version of the GStreamer monorepo on H-Linux  systems.

It bypasses standard packaging limitations to deliver a highly specific build that strips out unwanted and broken dependencies, 
neutralizes strict version-checking scripts, and disables Wayland at the compiler level.

---

## 🛠️ Key Modifications
* **Forced Versioning:** Bumps the root `meson.build` and all interconnected subproject components to `2.00.1`.
* **Strictly Wayland-Free:** Wayland is explicitly disabled via Meson (`-Dwayland=disabled`), and leftover ghost wrapper plugins (`libgstwaylandsink.so`, `libgstgtkwayland.so`) have been purged.
* **Neutered Metadata Scrapers:** Overrides the `extract-release-date-from-doap-file.py` script to prevent Meson from crashing on custom version strings.
* **Targeted Plugin Bypasses:** Explicitly disables `faac` and `opencv` to streamline the build and rely on superior modern alternatives (via FFmpeg).
* **Automated Orchestration:** Wrapped in a custom `INSTALL.hash` script utilizing `ccache`, preserving pre-build source modifications.

---

## 📂 Core Repository Contents
* `INSTALL.hash` - The automated orchestration script (requires the `h-linux-env.hash` library).
* `PKGBUILD` - The modified packaging manifest.

---

## 🚀 Installation

If you are running the H-Linux environment, simply execute the orchestrator script. It will automatically apply the `sed` version corrections and launch the build:
```bash
> gh repo clone fpucore/gstreamer2

> goto gstreamer2

> ./INSTALL.hash
```

---

## ⚖️ License

The GStreamer2 framework and standard plugins are licensed under the LGPL-2.1-or-later.

See individual source components for specific plugin licensing.

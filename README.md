# Fontra Flatpak
## Flatpak repository for Fontra

![Fontrapak Screenshot](screenshots/screenshot_02_dark.png)

### Key Features

* **Supported File Formats:**
  * **Read & Write:** Fontra (`.fontra`), Unified Font Object (`.ufo`), DesignSpace (`.designspace`), and RoboFont Component Format (`.rcjk`).
  * **Partial Read & Write:** Glyphs (`.glyphs`, `.glyphspackage`).
  * **Read-Only (Import):** TrueType (`.ttf`), OpenType (`.otf`), WOFF (`.woff`), WOFF2 (`.woff2`), and TTX XML (`.ttx`).
* **Variable Font Native:** Designed from the ground up for multi-axis variable font design, interpolation, and axis management.
* **Modern Vector Editing:** Non-destructive path operations, full component support, custom anchors, and multi-layer editing.
* **Text Shaping & Live Preview:** Real-time text shaping engine with OpenType feature testing.
* **Extensible & Web-Native:** Runs seamlessly in the browser or as a standalone local application via Flatpak.

### Installation

There is no hosted Flatpak repository for this test copy yet, so the app is built and installed locally.

* If Flatpak is not already enabled on your Linux distribution, follow [these instructions](https://flatpak.org/setup/) for your distribution to enable it.
* Install `flatpak-builder` and add Flathub (the KDE runtime and the PyQt BaseApp come from there):

```bash
flatpak remote-add --user --if-not-exists flathub https://dl.flathub.org/repo/flathub.flatpakrepo
```

* Clone this repository and build:

```bash
git clone -b source-build https://github.com/t4rik/fontrax-flatpak.git
cd fontrax-flatpak
flatpak-builder --user --install --install-deps-from=flathub --force-clean build-dir io.github.t4rik.FontraXPak.yml
```

* The build takes a while (cffsubr is compiled from source). Fontra Pak with all its dependencies is installed for your user.

### Update

There is no remote to update from, so pull and rebuild:

```bash
git pull
flatpak-builder --user --install --force-clean build-dir io.github.t4rik.FontraXPak.yml
```

### Running Fontra Flatpak

* In terminal, start the application by typing
```bash
flatpak run io.github.t4rik.FontraXPak
```
* Alternatively, open your app menu app menu and click on the Fontra icon <img src="https://fontra.xyz/fontra-icon.svg" alt="Fontra icon" height="32">

### Known Issues 

* **GNOME Wayland Titlebar Decorations:** On GNOME Wayland sessions, window titlebar controls (close, minimize, maximize) may be missing or lack native Adwaita styling depending on your distribution and GNOME version. See [fontra-pak#271](https://github.com/fontra/fontra-pak/issues/271).
* **Performance on Debian Trixie:** The Flatpak build has been reported to run slower on some distributions like Debian 13 (Trixie) compared to the base standalone binary. We are currently investigating the cause.

---

### Reporting Issues

* **Flatpak packaging or runtime issues:** Open an issue on [fontrax-flatpak/issues](https://github.com/t4rik/fontrax-flatpak/issues).
* **General Linux bugs or application crashes:** Open an issue on [fontrax-pak/issues](https://github.com/t4rik/fontrax-pak/issues).

# MeowVault

**English** | [简体中文](README.zh-CN.md)

> Release repository: installers and version metadata only. Source code is not published here.

MeowVault keeps document work, web capture and account credentials in one place, and
stores everything in an encrypted vault on your own machine — no cloud account, no sync
service, no telemetry.

## What it does

| Capability | Description |
|---|---|
| Document processing | Convert, split, merge and extract text from Word / PDF / HTML / Markdown |
| Web capture | Pull the text, images, videos and files behind a URL |
| Account manager | Category tree + entry table for credentials; passwords always masked |
| Encrypted vault | All app data lives in one encrypted `vault.img` on disk (Argon2id-derived key) |
| Bilingual UI | Chinese / English, switchable any time |
| Cross-platform | macOS, Windows, Debian-based Linux |

## Download

| Platform | Direct download |
|---|---|
| macOS (Apple silicon) | [MeowVault-macos-arm64.dmg](https://github.com/Love-PaoPao/MeowVault/releases/latest/download/MeowVault-macos-arm64.dmg) |
| macOS (Intel) | [MeowVault-macos-x64.dmg](https://github.com/Love-PaoPao/MeowVault/releases/latest/download/MeowVault-macos-x64.dmg) |
| Windows (x64) | [MeowVault-win-x64-setup.exe](https://github.com/Love-PaoPao/MeowVault/releases/latest/download/MeowVault-win-x64-setup.exe) |
| Windows (ARM64) | [MeowVault-win-arm64-setup.exe](https://github.com/Love-PaoPao/MeowVault/releases/latest/download/MeowVault-win-arm64-setup.exe) |
| Linux (amd64) | [meowvault_amd64.deb](https://github.com/Love-PaoPao/MeowVault/releases/latest/download/meowvault_amd64.deb) |
| Linux (arm64) | [meowvault_arm64.deb](https://github.com/Love-PaoPao/MeowVault/releases/latest/download/meowvault_arm64.deb) |

All links point to the newest stable release. Alternative mirror:
[gitee.com/Love-PaoPao/MeowVault/releases](https://gitee.com/Love-PaoPao/MeowVault/releases)

## Install

**macOS** — open the dmg and drag MeowVault into Applications. Builds are not notarized
yet; if macOS refuses to open it, right-click the app → Open, or run:

```bash
xattr -dr com.apple.quarantine /Applications/MeowVault.app
```

**Windows** — run the setup and follow the wizard. If SmartScreen blocks it, choose
"More info → Run anyway".

**Linux**

```bash
sudo dpkg -i meowvault_amd64.deb
sudo apt -f install
```

**Upgrading** — an existing install is upgraded in place, never installed twice: on macOS drag
the new MeowVault from the dmg into Applications and confirm **Replace**; on Windows run the
new setup (same AppId, same folder); on Linux run `sudo dpkg -i` with the new deb. User data
stays in `~/Library/Application Support/MeowVault/` (macOS), `%APPDATA%\MeowVault\` (Windows)
or `~/.local/share/MeowVault/` (Linux) and is never wiped by an upgrade. It is a fresh install
only when no copy existed before.

## System requirements

| OS | Architectures |
|---|---|
| Windows 10 or later | x64, ARM64 |
| macOS | Apple silicon, Intel |
| Debian / Ubuntu | amd64, arm64 |

## Data & privacy

Data is stored in `data/` under `~/Library/Application Support/MeowVault/` (macOS),
`%APPDATA%\MeowVault\` (Windows) or `~/.local/share/MeowVault/` (Linux). Nothing is
uploaded; network access happens only when you capture a URL, sign in to a site, or press
**Check updates**, which reads this repository's `version.json`. Delete `data/` to reset
the app.

## Third-party components

MeowVault bundles these open-source components, each distributed under its own license:

| License | Components |
|---|---|
| MIT | FluentQt, argon2-cffi, argon2-cffi-bindings, beautifulsoup4, brotli, cffi, charset-normalizer, et_xmlfile, markdown-it-py, markdownify, mdurl, msoffcrypto-tool, ntplib, openpyxl, pdfminer.six, pdfplumber, Pillow, python-docx, pyzipper, six, soupsieve, texttable, urllib3 |
| BSD | idna, lxml, olefile, psutil, pycparser, pycryptodomex, pypdf, pypdfium2, reportlab |
| LGPL-3.0 | Qt / PySide6 / shiboken6 |
| LGPL-2.1+ | inflate64, multivolumefile, py7zr, pybcj, pyppmd |
| Apache-2.0 | cryptography (or BSD-3-Clause), requests, websocket-client |
| MPL-2.0 | certifi |
| OFL-1.1 | the UI typeface FluentQt embeds (an Inter derivative) |
| PSF-2.0 | backports.zstd, typing_extensions |
| BSD / MIT / zlib / IJG / FTL | native libraries shipped inside the wheels: CPython, OpenSSL, XZ, libtiff, libjpeg-turbo, libwebp, libavif + libaom, FreeType, HarfBuzz, Little CMS 2, OpenJPEG, libpng, zlib-ng, Brotli, libXau / libxcb, PCRE2, PDFium / ICU, PyInstaller bootloader |

Qt / PySide6 is used unmodified and dynamically linked under LGPL-3.0. FluentQt compiles two
typefaces into its native module: `FluentQt UI Text` (an Inter derivative, OFL-1.1) and
`FluentQt Icons` (from Microsoft Fluent UI System Icons, MIT). Both licenses ship in
`licenses/FluentQt/`.

The verbatim license text of every native library listed above is in
`licenses/native/` (see `licenses/native/NOTICE.md` for which file belongs to which
library). This software is based in part on the work of the Independent JPEG Group.

## License

Released under the MIT License, Copyright (c) 2026 Love-PaoPao. Every installer ships:

- `LICENSE.txt` — the full MIT text (Windows: `MeowVault\LICENSE.txt`; macOS: `MeowVault.app/Contents/Resources/LICENSE.txt`; Linux deb: `/usr/share/doc/meowvault/LICENSE.txt`)
- `licenses/` — license texts for all bundled components plus `THIRD_PARTY_NOTICES.md` (Windows: `MeowVault\licenses\`; same folder on macOS and Linux)

Only installers are distributed, never source code. Full texts for the LGPL components
(Qt / PySide6 / shiboken6 and the py7zr family), the instructions for replacing and
relinking the Qt libraries, and the source-acquisition route are in
`licenses/THIRD_PARTY_NOTICES.md` and `licenses/PySide6/QT-LGPL-COMPLIANCE.md`; the embedded
font licensing is in `licenses/FluentQt/`.

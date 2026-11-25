# 喵守匣 MeowVault

[English](README.md) | **简体中文**

> 发布仓库：只放安装包与版本信息，不含源码。

喵守匣把文档处理、网页抓取和账号密码保管收在一处，数据全部加密存在你自己的电脑上——
没有云端账号、没有同步服务、不采集使用数据。

## 功能

| 能力 | 说明 |
|---|---|
| 文档处理 | 格式转换、拆分合并、正文抽取，覆盖 Word / PDF / HTML / Markdown |
| 网页抓取 | 从网址抓正文、图片、视频与文件 |
| 账号管理 | 分类树 + 条目表保管账号密码，密码始终以掩码显示 |
| 加密保险箱 | 全部数据存在一个加密镜像 `vault.img` 里（Argon2id 派生密钥） |
| 双语界面 | 中文 / English，随时切换 |
| 跨平台 | macOS、Windows、Debian 系 Linux |

## 下载

| 平台 | 直接下载 |
|---|---|
| macOS（Apple 芯片） | [MeowVault-macos-arm64.dmg](https://github.com/Love-PaoPao/MeowVault/releases/latest/download/MeowVault-macos-arm64.dmg) |
| macOS（Intel） | [MeowVault-macos-x64.dmg](https://github.com/Love-PaoPao/MeowVault/releases/latest/download/MeowVault-macos-x64.dmg) |
| Windows（x64） | [MeowVault-win-x64-setup.exe](https://github.com/Love-PaoPao/MeowVault/releases/latest/download/MeowVault-win-x64-setup.exe) |
| Windows（ARM64） | [MeowVault-win-arm64-setup.exe](https://github.com/Love-PaoPao/MeowVault/releases/latest/download/MeowVault-win-arm64-setup.exe) |
| Linux（amd64） | [meowvault_amd64.deb](https://github.com/Love-PaoPao/MeowVault/releases/latest/download/meowvault_amd64.deb) |
| Linux（arm64） | [meowvault_arm64.deb](https://github.com/Love-PaoPao/MeowVault/releases/latest/download/meowvault_arm64.deb) |

以上链接均指向最新正式版。备用镜像：
[gitee.com/Love-PaoPao/MeowVault/releases](https://gitee.com/Love-PaoPao/MeowVault/releases)

## 安装

**macOS**：双击挂载 dmg，把 MeowVault 拖进「应用程序」。当前版本未做公证，如果 macOS 不让
打开，右键点 App →「打开」，或在终端执行：

```bash
xattr -dr com.apple.quarantine /Applications/MeowVault.app
```

**Windows**：运行安装程序跟随向导。若被 SmartScreen 拦下，点「更多信息 → 仍要运行」。

**Linux**

```bash
sudo dpkg -i meowvault_amd64.deb
sudo apt -f install
```

**升级**：已装过的话不是「再装一套」，而是覆盖升级 —— macOS 把新 dmg 里的 MeowVault 拖进
「应用程序」并在提示中选「替换」；Windows 直接运行新安装包（同一 AppId，装回原目录）；
Linux 用 `sudo dpkg -i` 装新版 deb。用户数据始终在
`~/Library/Application Support/MeowVault/`（macOS）、`%APPDATA%\MeowVault\`（Windows）、
`~/.local/share/MeowVault/`（Linux），升级不会清空；只有从没装过时才是首次安装。

## 系统要求

| 系统 | 架构 |
|---|---|
| Windows 10 及以上 | x64、ARM64 |
| macOS | Apple 芯片、Intel |
| Debian / Ubuntu | amd64、arm64 |

## 数据与隐私

数据存在 `data/` 下：macOS `~/Library/Application Support/MeowVault/`、
Windows `%APPDATA%\MeowVault\`、Linux `~/.local/share/MeowVault/`。软件不上传任何内容；
联网只发生在你抓取网址、登录站点，以及设置页的「检查更新」（只读取本仓库的
`version.json`）。删掉 `data/` 即恢复出厂。

## 第三方组件

安装包内含下列开源组件，各自按其许可证分发：

| 许可证 | 组件 |
|---|---|
| MIT | FluentQt、argon2-cffi、argon2-cffi-bindings、beautifulsoup4、brotli、cffi、charset-normalizer、et_xmlfile、markdown-it-py、markdownify、mdurl、msoffcrypto-tool、ntplib、openpyxl、pdfminer.six、pdfplumber、Pillow、python-docx、pyzipper、six、soupsieve、texttable、urllib3 |
| BSD | idna、lxml、olefile、psutil、pycparser、pycryptodomex、pypdf、pypdfium2、reportlab |
| LGPL-3.0 | Qt / PySide6 / shiboken6 |
| LGPL-2.1+ | inflate64、multivolumefile、py7zr、pybcj、pyppmd |
| Apache-2.0 | cryptography（也可按 BSD-3-Clause）、requests、websocket-client |
| MPL-2.0 | certifi |
| OFL-1.1 | FluentQt 内嵌的 UI 字体（Inter 衍生） |
| PSF-2.0 | backports.zstd、typing_extensions |
| BSD / MIT / zlib / IJG / FTL | wheel 内随包的原生库：CPython、OpenSSL、XZ、libtiff、libjpeg-turbo、libwebp、libavif + libaom、FreeType、HarfBuzz、Little CMS 2、OpenJPEG、libpng、zlib-ng、Brotli、libXau / libxcb、PCRE2、PDFium / ICU、PyInstaller bootloader |

Qt / PySide6 以未修改、动态链接的方式按 LGPL-3.0 使用。FluentQt 把两套字体编译进原生模块：
`FluentQt UI Text`（Inter 衍生，OFL-1.1）与 `FluentQt Icons`（Microsoft Fluent UI System
Icons，MIT），授权全文随包放在 `licenses/FluentQt/`。

上表每个原生库的许可证正文都在 `licenses/native/`（哪个文件对应哪个库见
`licenses/native/NOTICE.md`）。本软件部分基于 Independent JPEG Group 的工作。

## 许可证

本项目以 MIT 许可证发布，Copyright (c) 2026 Love-PaoPao。安装包内附带：

- `LICENSE.txt` —— MIT 全文（Windows：`MeowVault\LICENSE.txt`；macOS：`MeowVault.app/Contents/Resources/LICENSE.txt`；Linux deb：`/usr/share/doc/meowvault/LICENSE.txt`）
- `licenses/` —— 全部随包组件的许可证文本与 `THIRD_PARTY_NOTICES.md`（Windows：`MeowVault\licenses\`，macOS 与 Linux 同上路径下的 `licenses/`）

本项目只发布安装包，不发布源码。LGPL 组件（Qt / PySide6 / shiboken6、py7zr 系列）的许可证全文、
Qt 库的替换与重链接说明、源码获取方式见 `licenses/THIRD_PARTY_NOTICES.md` 与
`licenses/PySide6/QT-LGPL-COMPLIANCE.md`；内嵌字体的授权见 `licenses/FluentQt/`。

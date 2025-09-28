
---

## 2) `README.md` for GitHub repo (complete, step-by-step)

```
# hoi4-dowser-wrapper
**Unofficial workaround** to make the Paradox HOI4 launcher run under certain Windows 11 setups by launching the original `dowser.exe` with `--in-process-gpu`.

> ⚠️ **Disclaimer:** This is an unsupported community workaround. Use at your own risk. Always backup original files. Do not redistribute the original `dowser.exe`. Share only scripts/source/wrapper code.

---

## Overview
Some users have reported that the Hearts of Iron IV Paradox launcher (`dowser.exe`) refuses to open correctly on Windows 11 after an update, while launching `hoi4.exe` directly works (but without Steam/mod integration). This repo documents a practical workaround: replace the `dowser.exe` file with a small wrapper that executes the original `dowser_original.exe` with the `--in-process-gpu` argument. This often makes the launcher initialize correctly via Steam and restores mod/Steam functions.

---

## Table of contents
- [Prerequisites](#prerequisites)
- [How it works](#how-it-works)
- [Option A: Inno Setup wrapper (used by author)](#option-a-inno-setup-wrapper-used-by-author)
- [Option B: C# single-file wrapper (recommended)](#option-b-c-single-file-wrapper-recommended)
- [Install steps](#install-steps)
- [Rollback / restore original files](#rollback--restore-original-files)
- [Troubleshooting & tips](#troubleshooting--tips)
- [Logs & diagnostics to collect](#logs--diagnostics-to-collect)
- [License & credits](#license--credits)

---

## Prerequisites
- Windows 10/11 PC with HOI4 installed via Steam.
- Admin rights to modify files in the game folder.
- One of:
  - [Inno Setup](https://jrsoftware.org/isdl.php) (to compile the `.iss` script), **or**
  - [.NET SDK (6/7/8+)](https://dotnet.microsoft.com/) to compile the C# wrapper.

---

## How it works
1. You rename the original `dowser.exe` to `dowser_original.exe`.
2. You replace `dowser.exe` with a wrapper executable.
3. When Steam executes `dowser.exe`, the wrapper immediately starts `dowser_original.exe` with `--in-process-gpu` and exits.
4. The original launcher runs with the extra parameter and (in many reported cases) initializes correctly, giving full Steam/mod functionality.

---

## Option A: Inno Setup wrapper (author’s method)

**Script (`dowser.iss`):**
```pascal
[Setup]
AppName=HOI4 Dowser Launcher
AppVersion=1.0
DefaultDirName={src}
DisableStartupPrompt=true
DisableDirPage=true
DisableProgramGroupPage=true
Uninstallable=false
OutputDir=.
OutputBaseFilename=dowser
Compression=lzma
SolidCompression=true

[Run]
Filename: "{src}\dowser_original.exe"; Parameters: "--in-process-gpu"; WorkingDir: "{src}"; Flags: shellexec postinstall nowait runhidden

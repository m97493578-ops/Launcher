# 🎮 Open Launcher

A lightweight, high-performance, and **100% portable** gaming hub and application launcher. Built using Python 3.14 and PyQt6, Open Launcher is fully compiled into native AOT machine instructions to guarantee total source code security, hardware-level startup speeds, and a zero-system-bloat footprint.

---

## ✨ Key Features

*   **Zero Registry Pollution:** Open Launcher operates completely inside its own isolated folder ecosystem. It writes absolutely zero background configuration keys to the Windows Registry, making it entirely sandboxed and safe.
*   **True Machine-Code Compilation:** Compiled natively via Nuitka and the `ziglang` compiler backend. All structural Python source code is stripped and translated directly into optimized C binaries, completely neutralizing basic automated bytecode decompilers.
*   **Self-Healing Database (`game.json`):** Tracks and manages your entire available game library dynamically. If `game.json` is deleted or missing, the local application backend automatically generates a fresh, default layout file on startup to eliminate runtime crashes.
*   **Decoupled Maintenance Engine (`updater.exe`):** Features an independent, single-file background update manager that securely communicates with GitHub's live database to deploy software upgrades seamlessly without manual user intervention.

---

## 📂 Production Distribution Layout

When extracted, the application maintains a hyper-efficient, self-contained portable directory matrix:

```text
📁 Open Launcher/
├── ⚙️ Launcher.exe     # The main compiled PyQt6 application binary
├── ⚙️ updater.exe      # Self-contained, single-file upgrade engine
├── 📄 game.json       # Dynamic library database (auto-generates if missing)
└── 📁 PyQt6/          # Streamed native graphics binaries and core DLLs
```

---

## 🚀 Installation & Usage

Because Open Launcher is fully portable, deployment requires zero traditional installation steps:

1.  Navigate to the [Latest Releases](https://github.com/m97493578-ops/Launcher/releases) page.
2.  Download the compiled **Release ZIP package** (meant for standard distribution).
3.  Extract the compressed archive anywhere on your machine (e.g., Desktop, Documents, or a portable USB Flash Drive).
4.  Launch **`Launcher.exe`** to start managing your game library.

---

## 🛰️ Independent Update Cycle

You do not need to interact with `updater.exe` during standard operation. If a system-wide patch or launcher feature upgrade is pushed to this repository, simply double-click **`updater.exe`** once. 

The maintenance engine will execute the following automated workflow:
1.  Forcibly kills any active `Launcher.exe` process hooks to release system file memory handles.
2.  Queries the GitHub REST API (`/releases/latest`) to pull down secure update definitions.
3.  Streams the newest production payload directly into a protected `.tmp` download buffer.
4.  Atomically swaps the outdated binary file and automatically boots your fresh launcher client back up.

---

## 🛠️ Compilation Blueprint (For Developers)

These source code files are now open source; how ever you should read the [License](LICENSE) File for Rules

If You Would Like to give us the compiled Launcher with the dlls and other things please fork this repo and give m97493578-ops access to it by going to the issues page and give us the link to the repo

To compile this project locally from the source files using the identical portable development environment, initialize your environment path and execute the Nuitka compilation matrices:


### 1. Compile Core Application (Standalone Folder Output)
```cmd
python -m nuitka --standalone --enable-plugin=pyqt6 --windows-console-mode=disable main.py
```
*(Note: Rename the compiled executable inside the output `.dist` folder from `main.exe` to `Launcher.exe` to match ecosystem process maps).*

### 2. Compile Core Maintenance Engine (Single Executable Output)
```cmd
python -m nuitka --onefile --windows-console-mode=disable updater.py
```
PS If you dont have python added to PATH then you will need to do

```cmd
set PATH=PATH TO YOUR PYTHON FOLDER;%PATH%
```


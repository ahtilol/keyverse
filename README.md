<div align="center">

  <img src="https://kommodo.ai/i/FUWAHZFSMK6LkuAK8bnW" alt="Keyverse Logo" width="96" height="96"/>

  # ◆ KEYVERSE OPEN SOURCE

  **Next-generation, zero-telemetry Minecraft Java Edition launcher — engineered for speed, privacy, and full customizability.**

  [![License: MIT](https://img.shields.io/badge/License-MIT-green.svg?style=for-the-badge)](https://opensource.keyverse.ahti.lol/terms)
  [![Electron](https://img.shields.io/badge/Electron-32.0-blue.svg?style=for-the-badge&logo=electron)](https://www.electronjs.org/)
  [![React](https://img.shields.io/badge/React-18.3-61dafb.svg?style=for-the-badge&logo=react)](https://reactjs.org/)
  [![TypeScript](https://img.shields.io/badge/TypeScript-5.5-3178c6.svg?style=for-the-badge&logo=typescript)](https://www.typescriptlang.org/)
  [![Zero Telemetry](https://img.shields.io/badge/Telemetry-ZERO-success.svg?style=for-the-badge)](https://opensource.keyverse.ahti.lol/privacy)

  [**Live Website**](https://opensource.keyverse.ahti.lol/) · [**Documentation**](https://opensource.keyverse.ahti.lol/docs) · [**Privacy Policy**](https://opensource.keyverse.ahti.lol/privacy) · [**Terms & License**](https://opensource.keyverse.ahti.lol/terms)

</div>

---

## ⚡ Overview

**Keyverse Open Source Edition** is a privacy-first desktop launcher for Minecraft Java Edition. Built from the ground up with Electron, Vite, React, and TypeScript, Keyverse combines raw launching performance with a sleek, minimalist UI.

Unlike traditional launchers, Keyverse puts full control back in your hands: **100% local profile data**, **built-in offline account support**, **custom skin management**, and **zero background telemetry**.

> 💡 *“Faster, smoother, and completely transparent Minecraft — zero telemetry, zero bloat.”*

---

## 🔥 Key Features

| Feature | Description |
| :--- | :--- |
| 🎮 **All Mod Loaders** | Full support for **Vanilla**, **Fabric**, **Quilt**, **Forge**, and **NeoForge** with single-click installation. |
| 👤 **Offline Accounts & Skins** | Play offline without Microsoft login. Local custom skin PNG storage with automatic **SkinsRestorer** mod integration. |
| 🛡️ **Microsoft OAuth 2.0** | Official device-code authentication flow for online accounts. Password-free and secure. |
| 🧩 **Live Mod Search & Install** | Native Modrinth API & CurseForge API integration for live mod browsing, dependency resolution, and updates. |
| ⚙️ **Automatic JVM Tuning** | Hardware-aware **Aikar's G1GC flags** recommendation engine for minimal GC stutter and max FPS. |
| 🎨 **Custom Themes & Splash** | Customizable dots/minimal splash screens, custom color accents, and Nyan Cat ears cosmetics. |
| 🚀 **Byte-Level Download Pool** | Concurrent HTTP downloads with SHA1 hash verification and automatic byte resume. |
| 🔒 **100% Zero Telemetry** | No tracking, no diagnostic pingers, no analytics. All tokens and profiles stay on your disk. |

---

## 🏗️ Architecture & Codebase Map

Keyverse separates Electron main process operations, preload security boundaries, and the React frontend renderer cleanly:

```mermaid
graph TD
    subgraph Main Process (Node.js)
        A[App Lifecycle / Index] --> B[IPC Handlers]
        B --> C[Microsoft OAuth]
        B --> D[Mojang Manifest & Assets]
        B --> E[Mod Loaders & Installers]
        B --> F[Java Runtime & JVM Tuning]
        B --> G[Offline Skin Manager]
        F --> H[Game Process Spawning]
    end

    subgraph Security Boundary
        I[Preload IPC Bridge]
    end

    subgraph Renderer (React + Vite)
        J[Zustand Store] --> K[Home View]
        J --> L[Versions & Mod Loaders]
        J --> M[Modrinth & CurseForge Mods]
        J --> N[Account & Skin Changer]
        J --> O[Settings & Themes]
    end

    B <==> I <==> J
```

---

## 🚀 Quickstart (Development)

### Prerequisites
- **Node.js 18+**
- **npm 9+** (or `pnpm` / `yarn`)
- **Git**

### Install & Run

```bash
# 1. Clone the repository
git clone https://github.com/ahtilol/keyverse.git
cd keyverse

# 2. Install dependencies
npm install

# 3. Start development server (HMR enabled)
npm run dev
```

> 🛠️ The Vite dev server will launch with hot module replacement at `http://localhost:5173` while Electron automatically boots the desktop shell.

---

## 📦 Building Distribution Packages

All production installers and binaries are generated using `electron-builder`:

```bash
# Type check TypeScript files
npm run typecheck

# Build production bundle (.exe / .dmg / .AppImage)
npm run build
```

| Platform | Output Target | Target Command |
| :--- | :--- | :--- |
| 🪟 **Windows** | NSIS Installer (`.exe`) | `npm run package:win` |
| 🍎 **macOS** | Universal DMG (`Intel + Apple Silicon`) | `npm run package:mac` |
| 🐧 **Linux** | AppImage (`.AppImage`) & Debian (`.deb`) | `npm run package:linux` |

---

## 👤 Offline Accounts & SkinsRestorer Integration

Keyverse includes native support for local **Offline Accounts**:
1. **Local Account Generation**: Generates deterministic UUIDs without contacting external authentication servers.
2. **Local Skin Directory**: Stores custom skin PNG files locally at `~/.keyverse/skins/`.
3. **SkinsRestorer Mod**: Automatically integrates with SkinsRestorer (Modrinth ID: `J8uh92yL`) so your custom skin renders seamlessly when playing on offline/multiplayer servers.

---

## 🛠️ Technology Stack

- **Shell & Engine**: [Electron](https://www.electronjs.org/) + [electron-vite](https://electron-vite.org/)
- **UI Framework**: [React 18](https://reactjs.org/) + [TypeScript](https://www.typescriptlang.org/)
- **State Management**: [Zustand](https://github.com/pmndrs/zustand)
- **Styling & Design**: Vanilla CSS Design Tokens (Glassmorphism, Spring Curves, Pixelify & Silkscreen Typography)
- **APIs**: Mojang Services, Modrinth REST API v2, CurseForge Developer API

---

## 🤝 Contributing

Contributions, issues, and feature requests are welcome!

1. Fork the Project
2. Create your Feature Branch (`git checkout -b feature/AmazingFeature`)
3. Commit your Changes (`git commit -m 'Add some AmazingFeature'`)
4. Verify your Build (`npm run build`)
5. Push to the Branch (`git push origin feature/AmazingFeature`)
6. Open a Pull Request

---

## 📄 License & Disclaimer

Distributed under the **MIT License**. See `LICENSE` for more information.

> [!NOTE]
> Minecraft is a registered trademark of Mojang Synergies AB and Microsoft Corporation. Keyverse Open Source Edition is an independent open-source project and is not affiliated with or endorsed by Mojang or Microsoft.

---

<div align="center">
  <sub>Built with ❤️ by Ahti & Kiki.</sub>
</div>

<p align="center">
  <img src="https://raw.githubusercontent.com/ai-desktop-lab/XLaunch/main/assets/designs/xlaunch/amber-classic-selected.png" alt="XLaunch classic amber design concept, not a runtime screenshot" width="100%" />
</p>

<h1 align="center">ai-desktop-lab</h1>
<p align="center"><strong>Classic Desktop Interaction · AI Workspace Entry Points · Local & Remote Desktops</strong></p>

<p align="center">
  <a href="https://github.com/ai-desktop-lab"><img src="https://img.shields.io/badge/GitHub-Organization-181717?style=for-the-badge&logo=github" alt="GitHub Organization" /></a>
  <a href="https://github.com/ai-desktop-lab/XLaunch"><img src="https://img.shields.io/badge/XLaunch-AI%20Launcher-D99A32?style=for-the-badge" alt="XLaunch" /></a>
  <a href="https://github.com/ai-desktop-lab/XDock"><img src="https://img.shields.io/badge/XDock-Qt%20Quick-41CD52?style=for-the-badge&logo=qt&logoColor=white" alt="XDock" /></a>
  <a href="https://github.com/ai-desktop-lab/isobuilder"><img src="https://img.shields.io/badge/Images-ISO%20%7C%20QCOW2%20%7C%20OCI-0B5C7A?style=for-the-badge&logo=linux&logoColor=white" alt="Image build formats" /></a>
</p>

<p align="center"><a href="https://github.com/ai-desktop-lab/.github/blob/main/profile/README.md">🇨🇳 简体中文</a> ｜ <strong>🌐 English Version</strong></p>

---

## 🌐 Organization Overview

`ai-desktop-lab` focuses on desktop interaction, system images, and remote desktop development within the AI Workspace ecosystem. Starting with a classic amber visual language, we develop application launchers, an independent dock, Linux image builders, and remote desktop transport as separately evolving components, exploring a consistent experience from local application entry points to remote AI workspaces.

### Mission & Development Principles

- **Classic interaction, AI-oriented**: Preserve intuitive application menus, search, and shortcuts while progressively introducing natural-language Agent commands.
- **Independent components, layered adapters**: XDock works without XLaunch or an Agent runtime; dedicated adapters handle platform differences.
- **Reproducible builds, multiple formats**: Distribution profiles and scripts define OCI, cloud VM, and installation ISO build paths.
- **Validation first, transparent boundaries**: Distinguish native implementations, experimental builds, and roadmap items. Design targets are not verified compatibility claims.

### Quick Links

- **Desktop projects**: [XLaunch](https://github.com/ai-desktop-lab/XLaunch) · [XDock](https://github.com/ai-desktop-lab/XDock)
- **Images & remote access**: [isobuilder](https://github.com/ai-desktop-lab/isobuilder) · [Remote Desktop](https://github.com/ai-desktop-lab/xworkmate-remote-desktop)
- **Related ecosystem**: [AI Workspace Lab](https://github.com/ai-workspace-lab) · [AI Workspace Infra](https://github.com/ai-workspace-infra)

---

## 🏛️ Four Core Pillars

<table>
<tr>
<td width="25%" align="center" valign="top">
  <h3>🚀<br/>Native Launcher</h3>
  <p><strong>XLaunch</strong></p>
  <p align="left"><sub>Native app discovery and launching, a compact menu and fullscreen grid, with an AI command entry point as a design direction.</sub></p>
</td>
<td width="25%" align="center" valign="top">
  <h3>⚓<br/>Classic Dock</h3>
  <p><strong>XDock</strong></p>
  <p align="left"><sub>Independent C++17 + Qt Quick/QML implementation for pinned apps, launching, themes, host status, and calendar interaction.</sub></p>
</td>
<td width="25%" align="center" valign="top">
  <h3>📦<br/>OS Packaging</h3>
  <p><strong>isobuilder</strong></p>
  <p align="left"><sub>Profiles and build definitions for Debian, Ubuntu, Fedora, and Rocky Linux, covering OCI, QCOW2, and installation ISO formats.</sub></p>
</td>
<td width="25%" align="center" valign="top">
  <h3>🌐<br/>Remote Desktop</h3>
  <p><strong>WebRTC transport</strong></p>
  <p align="left"><sub>An extraction baseline from XWorkmate: X11 capture, H.264 RTP, Pion WebRTC, input injection, and Flutter client adapter code.</sub></p>
</td>
</tr>
</table>

---

## 🔄 Desktop Architecture & Evolution

```mermaid
flowchart LR
    P[Distribution profiles and component packages] --> B[isobuilder]
    B --> O[OCI container image]
    B --> V[QCOW2 cloud image]
    B --> I[Installation ISO]
    L[XLaunch native launcher] <-->|Desktop IPC| D[XDock independent dock]
    O -.-> S[Local / virtual desktop session]
    V -.-> S
    I -.-> S
    S -.-> L
    S -.-> D
    S -.-> R[X11 capture and input injection]
    R --> W[H.264 RTP / Pion WebRTC]
    W --> F[Flutter client adapter baseline]
    L -.-> A[AI Agent command entry point]

    style B fill:#DBEAFE,stroke:#3B82F6
    style L fill:#FEF3C7,stroke:#D99A32
    style D fill:#FEF3C7,stroke:#D99A32
    style W fill:#ECFDF5,stroke:#10B981
    style A fill:#F3E8FF,stroke:#8B5CF6
```

> Solid lines describe component relationships documented in the repositories; dashed lines indicate integration directions or roadmap items. This is not a claim of a delivered, validated end-to-end solution.

---

## 📦 Core Repository Matrix (4 Core Projects)

| Repository | Role | Features & Current Boundaries |
| :--- | :--- | :--- |
| [`XLaunch`](https://github.com/ai-desktop-lab/XLaunch) | `Native Launcher` | Native macOS and Linux/X11 launcher with app discovery, launching, menus, and a fullscreen grid. Broader desktop adapters and Agent commands remain part of the project roadmap. |
| [`XDock`](https://github.com/ai-desktop-lab/XDock) | `Classic Dock` | Independent C++17 + Qt Quick/QML dock with pinned apps, themes, status panel, and calendar. Linux X11/Wayland integration needs live validation; running-window state and system tray services remain follow-up work. |
| [`isobuilder`](https://github.com/ai-desktop-lab/isobuilder) | `OS Image Builder` | Debian / Ubuntu / Fedora / Rocky profiles for OCI, QCOW2, and ISO outputs. Not a collection of released images; RPM ISO is an experimental installer scaffold, and a complete desktop requires compatible component packages. |
| [`xworkmate-remote-desktop`](https://github.com/ai-desktop-lab/xworkmate-remote-desktop) | `Remote Transport` | Server, protocol, and Flutter adapter baseline extracted from XWorkmate App / Bridge. Not a production replacement; standalone signaling, authentication, client packaging, and deployment boundaries remain incomplete. |

### Platform & Delivery Status

- **Desktop targets**: macOS 26+, GNOME, KDE Plasma, Xfce, and DDE are development targets, not verified universal support. Current native Linux interaction includes an X11 / ICEWM focus.
- **Remote capture**: The current backend uses X11 and `xdotool`; PipeWire / portal capture and libei input are future directions.
- **Image acceptance**: Debian / Ubuntu default to LightDM + ICEWM. Fedora / Rocky Live desktop acceptance, native component RPM packaging, and cloud template availability still need validation.
- **Source of truth**: Consult each project's README, implementation documentation, and Releases for build instructions, compatibility, and version status.

---

## 🤝 Contributing

Contribute through the relevant repository's Issues and Pull Requests: platform adapters, interaction design, image builds, and remote protocol tests are welcome. For bug reports, include your OS, desktop environment, display protocol (X11 / Wayland), component version, and reproduction steps.

<p align="center"><strong>Classic · Modular · Reproducible · Open · AI-Oriented</strong></p>

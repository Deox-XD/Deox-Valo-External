<div align="center">

# 🔥 Deox - Valorant External

[![C++](https://img.shields.io/badge/Language-C++-blue.svg)](https://isocpp.org/)
[![Platform](https://img.shields.io/badge/Platform-Windows-0078d7.svg)](https://www.microsoft.com/windows)
[![DirectX](https://img.shields.io/badge/DirectX-9-red.svg)](https://www.microsoft.com/en-us/download/details.aspx?id=35)
[![License](https://img.shields.io/badge/License-MIT-green.svg)](LICENSE)

**Advanced external overlay with kernel-level bypass for Valorant**

*Educational purposes only. Use at your own risk.*

</div>

---

## 📋 Table of Contents

- [Features](#-features)
- [Preview](#-preview)
- [Requirements](#-requirements)
- [Installation](#-installation)
- [Usage](#-usage)
- [Configuration](#-configuration)
- [How It Works](#-how-it-works)
- [Contributing](#-contributing)
- [Disclaimer](#-disclaimer)
- [Credits](#-credits)

---

## ✨ Features

### 🎯 Visual ESP
- **2D Box ESP** - Clean rectangular boxes around enemies
- **Cornered Box ESP** - Modern corner-style boxes
- **Snaplines** - Lines drawn from screen center to enemies
- **Distance Indicator** - Real-time distance measurements
- **Health Bars** - Visual health status with color coding

### 🛡️ Protection
- ✅ Guarded region bypass
- ✅ External overlay (non-invasive)
- ✅ Kernel-level driver support
- ✅ Memory protection evasion

### 🎨 Interface
- Modern ImGui-based overlay
- Customizable colors and themes
- Easy-to-use menu (INSERT key)
- Minimal performance impact
- Clean and responsive design

---

## 🔧 Requirements

### Software
- **Operating System:** Windows 10/11 (64-bit)
- **Visual Studio:** 2019 or newer (with C++ Desktop Development)
- **DirectX:** DirectX 9 SDK (included in project)
- **Driver:** Deox kernel driver ([Download here](https://github.com/Deox-XD/Deox-Shadow))

### Game
- Valorant (latest version)
- Game must be running in **windowed** or **borderless windowed** mode

---

## 📦 Installation

### Step 1: Clone the Repository
```bash
git clone 
cd deox-valorant
```

### Step 2: Setup the Driver
1. Download the kernel driver from [Deox](https://github.com/Deox-XD/Deox-Shadow)
2. Load the driver before starting the cheat
3. Ensure driver is properly signed or test signing is enabled

### Step 3: Build the Project
1. Open `UnrealEngine.sln` in Visual Studio
2. Set build configuration to **Release** and **x64**
3. Build the solution (`Ctrl+Shift+B`)
4. Executable will be in `x64/Release/`

### Step 4: Run
1. **Important:** Start the driver first
2. Launch Valorant
3. Run `Valorant.exe` from the Release folder
4. Wait for the overlay to attach

---

## 🎮 Usage

### Keybinds
| Key | Action |
|-----|--------|
| `INSERT` | Toggle menu visibility |
| `END` | Exit the cheat |

### Menu Controls
- Navigate using mouse
- Click checkboxes to enable/disable features
- All settings apply instantly

### Tips
- Start the cheat **after** Valorant is fully loaded
- Use windowed/borderless mode for best results
- Adjust your in-game graphics for optimal ESP visibility

---

## ⚙️ Configuration

### Default Settings
```cpp
// Visuals
Snaplines: ✅ Enabled
Distance: ❌ Disabled
2D Box: ✅ Enabled
Cornered Box: ❌ Disabled
Health Bar: ❌ Disabled
```

### Customization
Edit `Valorant/Game/globals.hpp` to modify default settings:
```cpp
namespace Settings::Visuals
{
    inline bool bSnaplines = true;
    inline bool bDistance = true;
    inline bool bBox = true;
    inline bool bBoxOutlined = false;
    inline bool bHealth = true;
    inline float BoxWidth = 1.0f;
}
```

---

## 🔬 How It Works

### Architecture Overview

```
┌─────────────────┐
│   Deox Overlay  │ ← DirectX9 transparent overlay
└────────┬────────┘
         │
    ┌────▼─────────────────┐
    │  Memory Reading      │ ← External process memory access
    │  (Kernel Driver)     │
    └────┬─────────────────┘
         │
    ┌────▼─────────────────┐
    │  Valorant Process    │ ← Target game
    │  (VALORANT-Win64-    │
    │   Shipping.exe)      │
    └──────────────────────┘
```

### Key Components

1. **Kernel Driver** - Bypasses Windows memory protection and anti-cheat guards
2. **External Overlay** - DirectX9 transparent window rendered over the game
3. **Actor Enumeration** - Iterates through game objects to find players
4. **ESP Rendering** - Draws visual indicators based on player positions
5. **World-to-Screen** - Converts 3D coordinates to 2D screen positions

### Security Features
- External process (not injecting into game)
- Guarded region bypass for protected memory areas
- Kernel-mode memory operations
- No pattern scanning (using static offsets)

---

## 🤝 Contributing

Contributions are welcome! Here's how you can help:

1. **Fork** the repository
2. **Create** a new branch (`git checkout -b feature/amazing-feature`)
3. **Commit** your changes (`git commit -m 'Add amazing feature'`)
4. **Push** to the branch (`git push origin feature/amazing-feature`)
5. **Open** a Pull Request

### Development Guidelines
- Follow existing code style and formatting
- Comment complex logic and algorithms
- Test thoroughly before submitting
- Update documentation if needed

---

## ⚠️ Disclaimer

```
This project is for EDUCATIONAL PURPOSES ONLY.

Using cheats/hacks in online games violates the Terms of Service of most games
and can result in permanent bans. The developers of this project do not condone
cheating in online games and are not responsible for any consequences resulting
from the use of this software.

Use at your own risk. You have been warned.
```

### Legal Notice
- This software is provided "as is" without warranty of any kind
- The authors are not liable for any damages or bans
- Reverse engineering may violate EULAs and local laws
- Check your local laws before using

---

## 🙏 Credits

### Development
- **Deox** - Current maintainer and rebrand
- Original concept and implementation base

### Dependencies
- [ImGui](https://github.com/ocornut/imgui) - Immediate mode GUI
- [DirectX SDK](https://www.microsoft.com/en-us/download/details.aspx?id=6812) - Graphics rendering
- [Deox Driver](https://github.com/Deox-XD/Deox-Shadow) - Kernel driver

### Special Thanks
- UnknownCheats community for research and documentation
- All contributors who help improve this project

---

<div align="center">

### 🌟 Star this repository if you found it helpful!

**Made with 💀 by Deox**

*Last Updated: October 2026*

</div>

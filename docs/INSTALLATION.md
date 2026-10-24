# 📦 Deox Installation Guide

Complete step-by-step installation instructions for **Deox**.

---

## ⚠️ Before You Start

### Legal Warning
This software is for **educational purposes only**. Using it in online games violates Terms of Service and can result in permanent bans. Proceed at your own risk.

### Prerequisites Checklist
- [ ] Windows 10/11 (64-bit)
- [ ] Visual Studio 2019 or newer
- [ ] DirectX 9 SDK (included in project)
- [ ] Valorant installed
- [ ] Administrator privileges
- [ ] Test signing enabled (for driver)

---

## 📥 Part 1: Download Deox

### Option A: Git Clone (Recommended)
```bash
git clone https://github.com/yourusername/deox-valorant.git
cd deox-valorant
```

### Option B: Download ZIP
1. Go to the GitHub repository
2. Click the green "Code" button
3. Select "Download ZIP"
4. Extract to your desired location

---

## 🔧 Part 2: Setup Development Environment

### Install Visual Studio

1. **Download Visual Studio**
   - Get [Visual Studio 2022 Community](https://visualstudio.microsoft.com/downloads/) (Free)

2. **Select Workloads**
   - ✅ Desktop development with C++
   - ✅ Windows 10/11 SDK

3. **Individual Components** (verify these are selected)
   - MSVC v142 or newer
   - Windows 10 SDK (10.0.19041.0 or newer)
   - C++ ATL for latest build tools

4. **Complete Installation**
   - This may take 20-30 minutes

---

## 🛡️ Part 3: Setup Kernel Driver

The kernel driver is **required** for bypassing memory protection.

### Download the Driver

1. Visit [UCMiraka Driver Repository](https://github.com/Chase1803/UCMiraka-ValorantExternal)
2. Download the latest release
3. Extract to a safe location

### Enable Test Signing

> **Note:** Required for loading unsigned drivers

1. **Open Command Prompt as Administrator**
   - Press `Win + X`
   - Select "Terminal (Admin)" or "Command Prompt (Admin)"

2. **Enable Test Signing**
   ```cmd
   bcdedit /set testsigning on
   ```

3. **Restart Your Computer**
   ```cmd
   shutdown /r /t 0
   ```

4. **Verify Test Mode**
   - After restart, you should see "Test Mode" watermark in bottom-right corner

### Load the Driver

1. **Run Driver Loader as Administrator**
   - Right-click `load_driver.exe`
   - Select "Run as administrator"

2. **Verify Driver Loaded**
   - Open Device Manager
   - Look for the driver in "Kernel" section
   - Or check with: `sc query <driver_name>`

3. **Keep Driver Running**
   - Driver must be loaded before starting Deox
   - Don't close the driver loader

---

## 🔨 Part 4: Build Deox

### Open the Project

1. Navigate to the extracted Deox folder
2. Double-click `UnrealEngine.sln`
3. Visual Studio will open the solution

### Configure Build Settings

1. **Set Configuration**
   - Top toolbar: Select **"Release"**
   - Platform: Select **"x64"**

2. **Verify DirectX SDK**
   - Project already includes DirectX headers
   - No additional setup needed

### Build the Solution

1. **Start Build**
   - Menu: `Build > Build Solution`
   - Or press: `Ctrl + Shift + B`

2. **Wait for Completion**
   - Build output will appear in the Output window
   - Should complete without errors

3. **Locate Executable**
   - Path: `x64\Release\Valorant.exe`
   - This is your compiled Deox executable

### Troubleshooting Build Errors

**Error: SDK Not Found**
```
Solution: Install Windows 10 SDK via Visual Studio Installer
```

**Error: Missing DirectX Libraries**
```
Solution: DirectX libs are in /Includes/Direct3d/ - verify they exist
```

**Error: Cannot open include file**
```
Solution: Right-click solution > Properties > VC++ Directories
Verify Include Directories and Library Directories are correct
```

---

## 🎮 Part 5: Configure Valorant

### Game Settings

1. **Launch Valorant**
2. **Go to Settings > Video**
3. **Set Display Mode**
   - Select: **Windowed** or **Borderless Windowed**
   - ❌ Do NOT use Fullscreen
4. **Recommended Graphics Settings**
   - Resolution: Native resolution
   - Frame Rate Limit: Unlimited or 240+ FPS
   - Anti-Aliasing: Your preference

### Why Windowed Mode?

Deox uses an overlay that renders on top of the game window. Fullscreen exclusive mode prevents overlays from displaying.

---

## 🚀 Part 6: Run Deox

### Launch Order (Important!)

1. ✅ **Load kernel driver** (if not already running)
2. ✅ **Launch Valorant** and get into the game
3. ✅ **Run Deox** (`Valorant.exe` from Release folder)

### First Run

1. **Run as Administrator**
   - Right-click `Valorant.exe`
   - Select "Run as administrator"

2. **Watch Console Output**
   ```
   [Deox] Waiting for Valorant...
   [Deox] Process found! Initializing...
   [Deox] Driver initialized
   [Deox] Overlay ready
   ```

3. **Overlay Appears**
   - Transparent overlay should appear over Valorant
   - Press `INSERT` to open menu

### Verify It's Working

1. **Open Menu** - Press `INSERT`
2. **Enable Features**
   - Enable "2D Box"
   - Enable "Snaplines"
3. **Check ESP**
   - Enemy players should have boxes
   - Lines should draw to enemies

---

## 🎯 Part 7: Configuration

### Keybinds

| Key | Action |
|-----|--------|
| `INSERT` | Toggle menu |
| `END` | Exit Deox |

### Menu Options

**Visual ESP**
- ☑ Enable 2D Box - Rectangular boxes around players
- ☑ Enable Cornered Box - Corner-style boxes (alternative)
- ☑ Enable Snaplines - Lines from screen center
- ☑ Enable Distance - Distance in meters
- ☑ Enable HealthBar - Visual health indicator

### Colors

Currently colors are hardcoded. To customize:

1. Edit `Valorant/Overlay/render.hpp`
2. Find the `ImColor` definitions
3. Modify RGB values: `ImColor(R, G, B, Alpha)`

**Example:**
```cpp
// Change ESP color to blue
ImColor espColor = ImColor(0, 100, 255, 255);
```

---

## ❗ Troubleshooting

### Overlay Doesn't Appear

**Cause:** Game in fullscreen mode
- **Solution:** Change to Windowed/Borderless

**Cause:** Driver not loaded
- **Solution:** Run driver loader as admin first

**Cause:** Wrong process
- **Solution:** Ensure Valorant is fully loaded into a match

### ESP Not Showing Players

**Cause:** Outdated offsets
- **Solution:** Check for offset updates after game patches

**Cause:** Driver communication failed
- **Solution:** Restart driver and Deox

### Crashes Immediately

**Cause:** Missing DirectX runtime
- **Solution:** Install [DirectX End-User Runtime](https://www.microsoft.com/en-us/download/details.aspx?id=35)

**Cause:** Anti-virus blocking
- **Solution:** Add Deox folder to exclusions

### "Test Mode" Watermark Annoying

**After testing, you can disable test signing:**
```cmd
bcdedit /set testsigning off
```
Then restart. Driver won't load anymore until test signing is re-enabled.

---

## 🔄 Updating Deox

### After Game Updates

1. **Check for Offset Updates**
   - Visit GitHub Issues
   - Look for offset update posts

2. **Update Offsets**
   - Edit `Valorant/Game/globals.hpp`
   - Replace old offsets with new ones

3. **Rebuild Project**
   - Clean solution
   - Rebuild in Release x64

### Pulling Latest Changes

```bash
cd deox-valorant
git pull origin main
```

---

## 🛑 Uninstallation

### Remove Deox

1. Delete the Deox folder
2. Remove from Windows Defender exclusions (if added)

### Disable Test Signing

```cmd
bcdedit /set testsigning off
shutdown /r /t 0
```

### Unload Driver

1. Open Command Prompt as Admin
2. Run: `sc stop <driver_name>`
3. Run: `sc delete <driver_name>`

---

## 📞 Support

Having issues? Check these resources:

1. **GitHub Issues** - Search existing issues
2. **README.md** - Review main documentation
3. **CONTRIBUTING.md** - Development guidelines

---

<div align="center">

**Installation complete! Happy gaming! 🎮**

*Remember: Educational purposes only*

</div>

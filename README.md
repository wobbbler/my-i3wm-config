<div align="center">
  <img src="https://raw.githubusercontent.com/wobbbler/my-i3wm-config/main/rice.png" alt="My i3 Desktop" width="800">
  
  # 🖥️ My i3WM Configuration

  ![i3wm](https://img.shields.io/badge/i3wm-Config-blueviolet?style=for-the-badge&logo=i3)
  ![Linux](https://img.shields.io/badge/Linux-WM-1793D1?style=for-the-badge&logo=linux)
  ![License](https://img.shields.io/badge/License-MIT-green?style=for-the-badge)

  > My personalized i3 window manager config with beautiful effects and convenient utilities

</div>

## ✨ Features

- 🎨 **Aesthetic Appearance** - Shadows, transparency, and rounded corners
- ⚡ **Fast Performance** - Optimized i3 configuration
- 🛠 **Convenient Management** - Custom hotkeys and settings
- 🌈 **Unified Color Scheme** - Consistent colors across all applications
- 🚀 **Full Integration** - Rofi, ranger and other must-have utilities

---

## 🚀 Quick Start

### 📦 Clone Repository
```bash
git clone https://github.com/wobbbler/my-i3wm-config.git ~/all-configs
cd ~/all-configs
```

### 📁 Directory Structure
```
~/all-configs/
├── alacritty.toml
├── config.jsonc
├── picom.conf
├── config.ini
├── rc.conf
├── config (i3wm config)
└── README.md
```

### ⚡ Apply Configuration
```bash
# Create config directories
mkdir -p ~/.config/{alacritty,fastfetch,picom,polybar,ranger,i3}

# Copy config files
cp ~/all-configs/alacritty.toml ~/.config/alacritty/
cp ~/all-configs/config.jsonc ~/.config/fastfetch/
cp ~/all-configs/picom.conf ~/.config/picom/
cp ~/all-configs/config.ini ~/.config/polybar/
cp ~/all-configs/rc.conf ~/.config/ranger/
cp ~/all-configs/config ~/.config/i3/config

# Edit i3 config (optional)
nvim ~/.config/i3/config

# Reload i3
i3-msg reload
```

---

## 📦 Included Utilities

| Category | Packages |
|----------|----------|
| **Window Manager** | `i3-gaps`, `i3status`, `i3lock` |
| **Terminals** | `alacritty`, `kitty` |
| **Launchers** | `rofi`, `dmenu` |
| **System Utilities** | `dex`, `networkmanager`, `network-manager-applet` |
| **Compositors** | `picom` |
| **Desktop** | `nitrogen` |
| **Screenshots** | `flameshot` |
| **File Manager** | `ranger` |
| **Audio** | `pulseaudio`, `pulseaudio-alsa`, `pavucontrol` |
| **Status Bars** | `polybar` |
| **Xorg** | `xorg-server`, `xorg-xinit`, `xorg-xsetroot` |
| **Text Editor** | `neovim` |
| **Version Control** | `git`, `lazy-git` |

---

## 🅰️ Required Fonts

| Font Name | Purpose |
|-----------|---------|
| **JetBrains Mono** | Primary monospace font |
| **Font Awesome** | Icons & symbols |
| **Noto Sans** | Fallback font |
| **Noto Emoji** | Emoji support |
| **Nerd Fonts** | Additional icons |
| **DejaVu Sans** | Fallback font |
| **Liberation** | Free alternative |

---

## ⌨️ Keybindings Cheat Sheet

### 🎯 Basic Operations
| Shortcut | Action |
|----------|---------|
| `Alt + Enter` | Open terminal |
| `Alt + D` | Application launcher |
| `Alt + Shift + Q` | Close window |
| `Print Screen` | Screenshot |

### 🖱️ Navigation (Vim-style)
| Shortcut | Action |
|----------|---------|
| `Alt + J/K/L/;` | Focus windows |
| `Alt + Shift + J/K/L/;` | Move windows |

### 🏢 Workspaces
| Shortcut | Action |
|----------|---------|
| `Alt + 1-0` | Switch workspace |
| `Alt + Shift + 1-0` | Move window to workspace |

### 🧩 Layout Management
| Shortcut | Action |
|----------|---------|
| `Alt + H/V` | Split horizontal/vertical |
| `Alt + F` | Toggle fullscreen |
| `Alt + R` | Resize mode |

---

## 🚀 AstroNvim Setup

### 📦 Installation
```bash
# Backup existing config
mv ~/.config/nvim ~/.config/nvim.bak
mv ~/.local/share/nvim ~/.local/share/nvim.bak

# Install AstroNvim
git clone https://github.com/AstroNvim/AstroNvim ~/.config/nvim

# Start Neovim (auto-setup)
nvim
```

### 🎨 Rofi Theme Selection
```bash
# Change rofi themes
rofi-theme-selector

# Manual theme application
rofi -show drun -theme theme-name
```

---

## ⚙️ Configuration Management

### 📁 Create Config Directories
```bash
mkdir -p ~/.config/{alacritty,fastfetch,picom,polybar,ranger}
```

### 🔧 Useful Commands
```bash
# Reload i3
i3-msg reload

# Restart i3
i3-msg restart

# Check config errors
i3 -c ~/.config/i3/config -C
```

---

## 💡 Pro Tips

- Press `$mod + Shift + R` to restart i3
- Use `$mod + Shift + C` to reload config
- Backup configs before major changes
- Check `man` pages for each utility

---

## 📄 License

**MIT License** - feel free to use and modify this configuration

---

<div align="center">

⭐ **If you find this config useful, please give it a star!** ⭐

</div>

<div align="center">
  <img src="https://raw.githubusercontent.com/wobbbler/my-i3wm-config/main/rice.png" alt="My i3 Desktop" width="800">
</div>
```markdown



# 🖥️ My i3WM Configuration

![i3wm](https://img.shields.io/badge/i3wm-Config-blueviolet?style=for-the-badge&logo=i3)
![Linux](https://img.shields.io/badge/Linux-WM-1793D1?style=for-the-badge&logo=linux)
![License](https://img.shields.io/badge/License-MIT-green?style=for-the-badge)

> My personalized i3 window manager config with beautiful effects and convenient utilities

## ✨ Features

- 🎨 **Aesthetic Appearance** - Shadows, transparency, and rounded corners
- ⚡ **Fast Performance** - Optimized i3 configuration
- 🛠 **Convenient Management** - Custom hotkeys and settings
- 🌈 **Unified Color Scheme** - Consistent colors across all applications
- 🚀 **Full Integration** - Rofi, Dunst and other must-have utilities

## 📦 Included Utilities

| Utility | Purpose |
|---------|------------|
| **i3lock** | Screen locker |
| **Flameshot** | Screenshots |
| **Picom** | Compositor with effects |
| **Polybar** | Status bar |
| **Mediacontrol** | Media control |
| **Fastfetch** | System information |
| **Alacritty** | Terminal |
| **Neovim** | Text editor |
| **Rofi** | Application launcher |
| **Dunst** | Notifications |

## 🚀 Quick Installation

### Installing All Dependencies

```bash
# Main utilities
sudo apt install i3 polybar picom flameshot alacritty rofi dunst playerctl

# Fonts (required!)
sudo apt install fonts-jetbrains-mono fonts-font-awesome fonts-nerd-font

# Install AstroNvim (optional)
git clone https://github.com/AstroNvim/AstroNvim ~/.config/nvim
```

### Creating Configuration Files

1. **Create directories:**
```bash
mkdir -p ~/.config/{i3,polybar,picom,alacritty,fastfetch,rofi,dunst}
```

2. **Add i3 config (~/.config/i3/config):**
```bash
# CUSTOM ###################################

# Screen lock
bindsym $mod+Shift+x exec ~/.config/i3/lock.sh 

# Flameshot with editor (main command)
bindsym Print exec --no-startup-id flameshot gui

# Launch Rofi
bindsym $mod+d exec rofi -show drun

# Gaps in i3-gaps (work independently of Picom)
gaps inner 15
gaps outer 15

# Autostart utilities
exec_always --no-startup-id picom --config ~/.config/picom/picom.conf --daemon
exec_always --no-startup-id ~/.config/polybar/launch.sh
exec_always --no-startup-id dunst

# Window border width
for_window [class=".*"] border pixel 3

# Change language
exec --no-startup-id setxkbmap -layout us,ru -option grp:alt_space_toggle

# END #######################################
```

3. **Add Alacritty config (~/.config/alacritty/alacritty.toml):**
```bash
# Main settings
[window]
dimensions = { columns = 120, lines = 30 }
padding = { x = 10, y = 10 }
decorations = "full"
startup_mode = "Windowed"

[scrolling]
history = 10000
multiplier = 3

[font]
size = 16.0
normal = { family = "Hack Nerd Font", style = "Regular" }
bold = { family = "Hack Nerd Font", style = "Bold" }
italic = { family = "Hack Nerd Font", style = "Italic" }

# Cursor
[cursor]
style = { shape = "Block" }
blink_interval = 0
unfocused_hollow = true

# Mouse
[mouse]
hide_when_typing = false

[colors]
primary = { background = "#2E3440", foreground = "#D8DEE9" }
cursor = { text = "#2E3440", cursor = "#D8DEE9" }
selection = { text = "#D8DEE9", background = "#434C5E" }
```

4. **Add Fastfetch config (~/.config/fastfetch/fastfetch.jsonc):**
```json
{
    "$schema": "https://github.com/fastfetch-cli/fastfetch/raw/dev/doc/json_schema.json",
    "logo": {
        "type": "small"
    },
    "display": {
        "separator": " ",
        "key": {
            "type": "both"
        },
        "bar": {
            "border": {
                "left": "\uee00",
                "leftElapsed": "\uee03",
                "right": "\uee02",
                "rightElapsed": "\uee05"
            },
            "char": {
                "total": "\uee01",
                "elapsed": "\uee04"
            },
            "color": {
                "total": null
            }
        },
        "percent": {
            "type": [
                "bar",
                "bar-monochrome"
            ]
        }
    },
    "modules": [
        "title",
        "separator",
        {
            "type": "memory",
            "key": "MEM ",
            "keyColor": "green"
        },
        {
            "type": "swap",
            "key": "SWP ",
            "keyColor": "green"
        },
        {
            "type": "disk",
            "folders": "/",
            "key": "DSK ",
            "keyColor": "green"
        },
        {
            "type": "disk",
            "folders": "/home",
            "key": "DSKH",
            "keyColor": "green"
        },
        {
            "type": "colors",
            "paddingLeft": 7,
            "symbol": "circle"
        }
    ]
}
```

5. **Add Polybar config (~/.config/polybar/config):**
```ini
[colors]
background = #2E3440
background-alt = #434C5E
foreground = #D8DEE9
primary = #88C0D0
secondary = #f29c00
alert = #BF616A
blue = #81A1C1
green = #A3BE8C

[bar/mybar]
width = 100%
height = 27
offset-x = 0
offset-y = 0
radius = 0  
fixed-center = true

background = ${colors.background}
foreground = ${colors.foreground}

border-size = 0
border-color = #00000000

padding-left = 0
padding-right = 0

module-margin-left = 1
module-margin-right = 1

font-0 = "JetBrains Mono Nerd Font:size=12;3"
font-1 = "Font Awesome 6 Free:style=Solid:size=12;3"
font-2 = "Font Awesome 6 Brands:size=12;3"
font-3 = "Nerd Font:size=12;3"
font-4 = "Symbols Nerd Font:size=12;3"

modules-left = i3 xwindow 
modules-center = date
modules-right = xkeyboard media pulseaudio brightness battery

tray-position = right
tray-padding = 2
tray-background = ${colors.background}

wm-restack = i3

[module/i3]
type = internal/i3
format = <label-state> <label-mode>
index-sort = true
wrapping-scroll = false
pin-workspaces = true

label-mode-padding = 2
label-mode-foreground = #000
label-mode-background = ${colors.primary}

label-focused =  %name%
label-focused-background = ${colors.background-alt}
label-focused-foreground = ${colors.primary}
label-focused-padding = 2

label-unfocused =  %name%
label-unfocused-padding = 2
label-unfocused-foreground = ${colors.foreground}

label-visible =  %name%
label-visible-background = ${colors.background-alt}
label-visible-padding = 2
label-visible-foreground = ${colors.green}

label-urgent =  %name%
label-urgent-background = ${colors.alert}
label-urgent-padding = 2
label-urgent-foreground = #000

[module/xwindow]
type = internal/xwindow
label = %title:0:60:...%
label-foreground = ${colors.blue}
label-font = 1

[module/date]
type = internal/date
interval = 1

date = %Y-%m-%d
time = %H:%M:%S

label =  %date%  %time%
label-font = 1
label-foreground = ${colors.secondary}

[module/media]
type = custom/script
interval = 2
format = <label>
format-prefix = " "
format-prefix-foreground = ${colors.green}

exec = playerctl metadata --format "{{ artist }} - {{ title }}" 2>/dev/null || echo "No media"
exec-if = playerctl status 2>/dev/null

click-left = playerctl play-pause
click-middle = playerctl stop
click-right = playerctl next

tail = true

[module/pulseaudio]
type = internal/pulseaudio

format-volume = <label-volume> <bar-volume>
label-volume =  %percentage%%
label-volume-foreground = ${colors.primary}

format-muted =  muted
format-muted-foreground = #666

bar-volume-width = 8
bar-volume-foreground-0 = #55aa55
bar-volume-foreground-1 = #55aa55
bar-volume-foreground-2 = #55aa55
bar-volume-foreground-3 = #f5a70a
bar-volume-foreground-4 = #ff5555
bar-volume-gradient = false
bar-volume-indicator = |
bar-volume-indicator-font = 2
bar-volume-fill = ─
bar-volume-fill-font = 2
bar-volume-empty = ─
bar-volume-empty-font = 2
bar-volume-empty-foreground = ${colors.foreground}

click-left = pavucontrol &
click-right = pactl set-sink-mute @DEFAULT_SINK@ toggle
scroll-up = pactl set-sink-volume @DEFAULT_SINK@ +5%
scroll-down = pactl set-sink-volume @DEFAULT_SINK@ -5%

[module/brightness]
type = internal/backlight
card = intel_backlight

format = <label> <bar-brightness>
label = 
label-foreground = ${colors.secondary}

bar-brightness-width = 8
bar-brightness-foreground-0 = #f5a70a
bar-brightness-foreground-1 = #f5a70a
bar-brightness-foreground-2 = #f5a70a
bar-brightness-foreground-3 = #f5a70a
bar-brightness-foreground-4 = #f5a70a
bar-brightness-gradient = false
bar-brightness-indicator = |
bar-brightness-indicator-font = 2
bar-brightness-fill = ─
bar-brightness-fill-font = 2
bar-brightness-empty = ─
bar-brightness-empty-font = 2
bar-brightness-empty-foreground = ${colors.foreground}

scroll-up = xbacklight -inc 5%
scroll-down = xbacklight -dec 5%

[module/network]
type = internal/network
interface = wlan0
interval = 3.0

format-connected = <ramp-signal> <label-connected>
format-disconnected = ⚠ Disconnected
format-disconnected-foreground = ${colors.alert}

label-connected = %essid% %local_ip%
label-connected-foreground = ${colors.primary}

ramp-signal-0 = 
ramp-signal-1 = 
ramp-signal-2 = 
ramp-signal-3 = 
ramp-signal-4 = 
ramp-signal-foreground = ${colors.green}

[module/xkeyboard]
type = internal/xkeyboard
blacklist-0 = num lock

format-prefix = "    "
format-prefix-foreground = ${colors.primary}
format-prefix-font = 2

label-layout = %layout%
label-layout-foreground = ${colors.foreground}

label-indicator-padding = 2
label-indicator-margin = 1
label-indicator-background = ${colors.secondary}

[module/battery]
type = internal/battery
battery = BAT0
adapter = AC

format-charging = <animation-charging> <label-charging>
format-discharging = <ramp-capacity> <label-discharging>
format-full = <ramp-capacity> <label-full>

label-charging = %percentage%%
label-discharging = %percentage%%
label-full = %percentage%%

ramp-capacity-0 = 
ramp-capacity-1 = 
ramp-capacity-2 = 
ramp-capacity-3 = 
ramp-capacity-4 = 

animation-charging-0 = 
animation-charging-1 = 
animation-charging-2 = 
animation-charging-framerate = 750

[settings]
screenchange-reload = true
throttle-output = 5
throttle-output-for = 10

[global/wm]
margin-top = 5
margin-bottom = 5
```

6. **Add Picom config (~/.config/picom/picom.conf):**
```ini
# Shadows
shadow = true;
shadow-radius = 16;
shadow-opacity = 0.75;
shadow-offset-x = -15;
shadow-offset-y = -15;
shadow-exclude = [
    "name = 'Notification'",
    "class_g = 'Conky'",
    "class_g ?= 'Notify-osd'",
    "class_g = 'Cairo-clock'",
    "_GTK_FRAME_EXTENTS@:c"
];

# Fading
fading = true;
fade-in-step = 0.03;
fade-out-step = 0.03;
fade-delta = 5;

# Transparency
inactive-opacity = 0.95;
active-opacity = 1.0;
frame-opacity = 1.0;
inactive-opacity-override = false;

# Blur
blur: {
    method = "dual_kawase";
    strength = 6;
    background = true;
    background-frame = false;
    background-fixed = false;
}

# Rounded corners
corner-radius = 0
rounded-corners-exclude = [
    "window_type = 'dock'",
    "window_type = 'desktop'",
    "class_g = 'Polybar'",
    "class_g = 'i3-frame'"
];

# Exceptions
opacity-rule = [
    "90:class_g = 'Alacritty' && focused",
    "80:class_g = 'Alacritty' && !focused",
    "95:class_g = 'Code'",
    "90:class_g = 'Thunar'",
    "100:class_g = 'Firefox'",
    "100:class_g = 'Chromium'"
];

# Backend
backend = "glx";
vsync = true;

# Performance
use-damage = true;
log-level = "warn";

# Shadow exceptions
shadow-exclude = [
    "name = 'Notification'",
    "class_g = 'Conky'",
    "class_g ?= 'Notify-osd'",
    "class_g = 'Cairo-clock'",
    "class_g = 'Slop'",
    "class_g = 'Polybar'",
    "_GTK_FRAME_EXTENTS@:c",
    "_NET_WM_STATE@:32a *= '_NET_WM_STATE_HIDDEN'"
];

# Fade exceptions
fade-exclude = [
    "class_g = 'Slop'"
];

# Blur exceptions
blur-background-exclude = [
    "window_type = 'dock'",
    "window_type = 'desktop'",
    "class_g = 'Polybar'",
    "class_g = 'i3-frame'",
    "_GTK_FRAME_EXTENTS@:c"
];

# Windows with transparency
wintypes:
{
    tooltip = { fade = true; shadow = true; opacity = 0.75; focus = true; full-shadow = false; };
    dock = { shadow = false; clip-shadow-above = true; }
    dnd = { shadow = false; }
    popup_menu = { opacity = 0.95; }
    dropdown_menu = { opacity = 0.95; }
};
```

7. **Create Polybar launch script (~/.config/polybar/launch.sh):**
```bash
#!/bin/bash
killall -q polybar
while pgrep -u $UID -x polybar >/dev/null; do sleep 1; done
polybar mybar &
```

Make it executable:
```bash
chmod +x ~/.config/polybar/launch.sh
```

## ⚙️ Main Hotkeys

| Combination | Action |
|------------|----------|
| `Mod+Shift+x` | Screen lock |
| `Print` | Screenshot (Flameshot) |
| `Mod+Enter` | Open terminal |
| `Mod+D` | Rofi (application launcher) |
| `Mod+1-9` | Switch workspaces |
| `Alt+Space` | Switch keyboard layout |

## 🎨 Color Scheme

Main colors (Nord theme):
- Background: `#2E3440`
- Foreground: `#D8DEE9`
- Primary: `#88C0D0`
- Secondary: `#f29c00`
- Accent: `#BF616A`

## 📄 License

MIT License - free use and modification

⭐ **If you liked this config, give it a star on GitHub!**

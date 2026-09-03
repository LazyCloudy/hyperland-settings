# hyperland-settings

My [Hyprland](https://hypr.land) configuration, written in the new **Lua config format** (`hl.*` API) instead of `hyprland.conf`.

## Layout

```
hyprland.lua          entry point — requires every module
.luarc.json           points lua-language-server at /usr/share/hypr/stubs
moduals/
  autostart.lua       processes launched on hyprland.start
  binds.lua           programs + all keybindings
  env.lua             environment variables (toolkit backends, XDG, Qt, NVIDIA)
  input.lua           keyboard/touchpad/gestures, per-device config
  lf.lua              layout + look & feel (gaps, borders, blur, animations)
  mics.lua            misc settings
  monitor.lua         monitor modes and persistent workspace rules
  windowruls.lua      window + layer rules
```

`hyprland.lua` also pulls in `hyprland-gui`, which holds settings managed by HyprMod.

## Install

Back up your existing config, then clone into place:

```sh
mv ~/.config/hypr ~/.config/hypr.bak
git clone https://github.com/LazyCloudy/hyperland-settings.git ~/.config/hypr
```

Hyprland loads `~/.config/hypr/hyprland.lua`.

## Setup

- **Monitors** — `DP-3` at 2560x1440@180 (workspaces 1–5), `HDMI-A-1` at 1920x1080@60 (workspaces 6–10), both persistent.
- **Layout** — dwindle, 5px inner / 15px outer gaps, 10px rounding, blur and shadows on, inactive windows at 0.8 opacity.
- **Input** — `us,ara` keyboard layouts toggled with `Alt+Shift`, 3-finger horizontal swipe to change workspace.
- **Shell** — [Noctalia](https://github.com/noctalia-dev/noctalia-shell) (v5), driven through `noctalia msg` IPC.
- **GPU** — env vars assume NVIDIA (`LIBVA_DRIVER_NAME=nvidia`).

## Programs

| Role | Command |
| --- | --- |
| Terminal | `alacritty` |
| File manager | `dolphin` |
| App launcher | `rofi -show drun` |
| Run dialog | `rofi -show run` |
| Browser | Zen |
| Shell / bar | `noctalia` |

## Keybindings

`SUPER` is the main modifier.

### Windows

| Bind | Action |
| --- | --- |
| `SUPER + Q` | Close window |
| `SUPER + V` | Toggle floating |
| `SUPER + F` | Toggle fullscreen |
| `SUPER + P` | Pseudo-tile |
| `SUPER + J` | Toggle split |
| `SUPER + ←/→/↑/↓` | Move focus |
| `SUPER + LMB / RMB` | Drag / resize window |
| `SUPER + M` | Shut down (`hyprshutdown`, falls back to exiting Hyprland) |

### Workspaces

| Bind | Action |
| --- | --- |
| `SUPER + 1–0` | Switch to workspace 1–10 |
| `SUPER + SHIFT + 1–0` | Move window to workspace 1–10 |
| `SUPER + scroll` | Cycle workspaces |
| `SUPER + S` | Toggle special workspace `magic` |

### Launching

| Bind | Action |
| --- | --- |
| `SUPER + Return` | Terminal |
| `SUPER + E` | File manager |
| `SUPER + R` | App launcher (rofi drun) |
| `SUPER + SHIFT + R` | Run dialog |
| `SUPER + B` | Browser |

### Noctalia shell

| Bind | Action |
| --- | --- |
| `SUPER + Space` | Launcher panel |
| `SUPER + S` | Control center |
| `SUPER + A` | Audio panel |
| `SUPER + W` | Wallpaper panel |
| `SUPER + comma` | Settings |
| `SUPER + SHIFT + V` | Clipboard |
| `SUPER + SHIFT + S` | Start the shell |
| `ALT + Tab` | Window switcher |

### Screenshots & media

| Bind | Action |
| --- | --- |
| `SUPER + SHIFT + S` | Region screenshot → swappy |
| `SUPER + SHIFT + C` | Pick color region → clipboard |
| `XF86Audio*` | Volume / mute / play / next / prev |
| `XF86MonBrightness*` | Brightness up / down |

> Note: `SUPER + S` and `SUPER + SHIFT + S` are each bound more than once (special workspace, control center, shell start, screenshot). Later binds win — clean these up if a shortcut misbehaves.

## Dependencies

`alacritty`, `dolphin`, `rofi`, `noctalia`, `swaync`, `nm-applet`, `hyprpolkitagent`, Easy Effects, `grim`, `slurp`, `swappy`, `wl-clipboard`, `wpctl` (WirePlumber), `brightnessctl`, `playerctl`.

<<<<<<< HEAD
# 🌌 Warp Theme for Oh My Posh 🌌

![Cosmic Terminal Preview](https://images.unsplash.com/photo-1516339901639-2a4b0ba7b5f7?ixid=M3wzNjM5Nzd8MHwxfHNlYXJjaHwxfHxjb3Ntb3MlMjBzdGFyfGVufDB8fHx8MTcxNzI2NjM0NHwwMA&ixlib=rb-4.0.3&w=800)  
*A terminal theme that brings the cosmos to your command line*

---

## 🚀 About  
**Warp** is a visually stunning Oh My Posh theme inspired by interstellar exploration, celestial phenomena, and the mysteries of the universe. Designed by **The Space Lama Glama**, it combines vibrant cosmic colors with intuitive icons to transform your terminal into a spaceship cockpit.

```ini
name = 'Warp'
version = '1.0.2'
author = 'The Space Lama Glama'
license = 'MIT'
```

---

## 🌠 Features  
✅ **Cosmic Color Palette**:  
- Solar yellows, pulsar magentas, and nebula pinks create a vibrant space aesthetic  
- Dark cosmic black background for optimal contrast  

✅ **Dynamic Segments**:  
- Real-time Git status with constellation-style indicators (⇡⇣)  
- Execution time display for long-running commands  
- Seamless WSL/SSH session detection  

✅ **Space-themed Icons**:  
- Custom Nerd Fonts icons for OS, folders, and Git operations  
- Animated prompt transitions with diamond/powerline styles  

---

## 🛸 Installation  

### 1. Install Oh My Posh  
```powershell
# Windows (winget)
winget install JanDeDobbeleer.oh-my-posh

# macOS/Linux (brew)
brew install oh-my-posh
```

### 2. Download Warp Theme  
```bash
curl -o warp.omp.json https://raw.githubusercontent.com/your-username/your-repo/main/warp.omp.json
```

### 3. Activate the Theme  
**PowerShell**  
```powershell
oh-my-posh init pwsh --config warp.omp.json | Invoke-Expression
```

**Bash/Zsh**  
```bash
eval "$(oh-my-posh init bash --config warp.omp.json)"
```

---

## 🎨 Customization  
1. **Modify Colors**:  
   Edit the `[palette]` section in `warp.omp.json` to adjust:  
   ```ini
   solar_yellow = '#FFF078' → '#YOUR_COLOR'
   pulsar_magenta = '#E90074' → '#YOUR_COLOR'
   ```

2. **Tweak Segments**:  
   - Adjust icons in `template` fields (requires [Nerd Fonts](https://www.nerdfonts.com/))  
   - Modify `powerline_symbol` for different separators  

3. **Reload Configuration**:  
   Restart your terminal or run:  
   ```bash
   exec zsh  # or bash/pwsh
   ```

---

## 📜 License  
[MIT License](LICENSE) © 2024 The Space Lama Glama  
*Free for personal/commercial use - Star this repo if you enjoy the theme!*

---

## 📡 Contact  
🚀 Created by **The Space Lama Glama**  
[GitHub Profile](https://github.com/your-username) | [Report Issues](https://github.com/your-username/your-repo/issues)

<details>
<summary>Theme Code (warp.omp.json)</summary>

```json
{
  "name": "Warp",
  "author": "The Space Lama Glama",
  "description": "A cosmic theme inspired by the mysteries of space, astronomy, and interstellar exploration",
  "license": "MIT",
  "theme_version": "1.0.2",
  "console_title_template": "{{ .Shell }} in {{ .Folder }}",
  "version": 3,
  "final_space": true,
  "secondary_prompt": {
    "template": "󰯉 ",
    "foreground": "magenta",
    "background": "transparent"
  },
  "transient_prompt": {
    "template": "󱎃 ",
    "background": "transparent",
    "foreground_templates": [
      "{{if gt .Code 0}}p:alert_red{{end}}",
      "{{if eq .Code 0}}p:solar_yellow{{end}}"
    ]
  },
  "blocks": [
    {
      "type": "prompt",
      "alignment": "left",
      "newline": true,
      "segments": [
        {
          "type": "os",
          "style": "diamond",
          "leading_diamond": "",
          "trailing_diamond": "",
          "foreground": "p:cosmic_black",
          "background": "p:solar_yellow",
          "template": "{{ if .WSL }}WSL at {{ end }}{{ .Icon }} ",
          "properties": {
            "linux": " ",
            "macos": " ",
            "windows": " "
          }
        },
        {
          "type": "session",
          "style": "powerline",
          "powerline_symbol": "",
          "foreground": "p:stellar_white",
          "background": "p:nebula_pink",
          "template": "{{ if .SSHSession }} {{ end }} <p:stardust_pink></> {{ .UserName }}<p:stardust_pink>in</>{{ .HostName }}"
        },
        {
          "type": "path",
          "style": "powerline",
          "powerline_symbol": "",
          "template": " 󱓞 <p:stardust_pink></> {{ .Path }} ",
          "foreground": "p:stellar_white",
          "background": "p:pulsar_magenta",
          "properties": {
            "cache_duration": "none",
            "style": "folder",
            "mapped_locations": {
              "~": " "
            }
          }
        },
        {
          "type": "git",
          "style": "powerline",
          "powerline_symbol": "",
          "template": " {{ .HEAD }}{{ if or (.Working.Changed) (.Staging.Changed) }}*{{ end }} <p:aurora_cyan>{{ if gt .Behind 0 }}⇣{{ end }}{{ if gt .Ahead 0 }}⇡{{ end }}</>",
          "foreground": "p:nova_pink",
          "background": "p:cosmic_black",
          "properties": {
            "branch_icon": " ",
            "cache_duration": "none",
            "commit_icon": "@",
            "fetch_status": true
          }
        }
      ]
    },
    {
      "type": "rprompt",
      "overflow": "hidden",
      "segments": [
        {
          "type": "executiontime",
          "style": "plain",
          "template": "{{ .FormattedMs }}",
          "foreground": "p:solar_yellow",
          "background": "transparent",
          "properties": {
            "cache_duration": "none",
            "threshold": 5000
          }
        }
      ]
    },
    {
      "type": "prompt",
      "alignment": "left",
      "newline": true,
      "segments": [
        {
          "type": "text",
          "style": "plain",
          "template": "  ",
          "foreground_templates": [
            "{{if gt .Code 0}}p:alert_red{{end}}",
            "{{if eq .Code 0}}p:sky_blue{{end}}"
          ],
          "background": "transparent",
          "properties": {
            "cache_duration": "none"
          }
        }
      ]
    }
  ],
  "palette": {
    "stellar_white": "#FFFFFF",
    "solar_yellow": "#FFF078",
    "pulsar_magenta": "#E90074",
    "nebula_pink": "#FF4191",
    "stardust_pink": "#FF80B0",
    "nova_pink": "#F9F5F6",
    "cosmic_black": "#1A2330",
    "supernova_orange": "#FF8C00",
    "aurora_cyan": "#00FFFF",
    "alert_red": "#B83232",
    "sky_blue": "#CAF0F8"
  }
}
```
</details>
=======
# warp-omp
A space exploration them for Oh My Posh
>>>>>>> origin/main

# Frostbyte

A macOS Sonoma-inspired dark theme for VS Code with frosty glass panels, rounded corners, and smooth transitions.

![Frostbyte Theme](assets/screenshot.png)

## Features

- **Floating glass panels** — Sidebar, editor, panel, and auxiliary bar float with subtle margins and rounded corners
- **Glass-effect borders** — Directional light simulation with brighter top/left edges and subtle bottom/right
- **Pill-shaped activity bar** — Activity bar icons sit inside a glass pill with circular selection indicators
- **Rounded everything** — Command palette, notifications, context menus, autocomplete, find widget, tooltips
- **Breadcrumb bar dims** when not hovered, fading in smoothly on hover
- **Status bar dims** when not hovered, revealing full content on hover
- **Tab close buttons fade in** on hover (always visible on active tab)
- **Pill-shaped scrollbar thumbs** with smooth opacity transitions
- **Smooth transitions** on sidebar selections, list items, and scrollbars
- **macOS Sonoma color palette** — Warm charcoal backgrounds with Apple system colors for accents

## Color Palette

| Element | Color | Description |
|---------|-------|-------------|
| Canvas | `#141416` | Deep warm charcoal behind floating panels |
| Panels | `#1c1c1e` | Apple system gray 6 (dark) |
| Surfaces | `#2c2c2e` | Apple system gray 5 (dark) |
| Text | `#f5f5f7` | Apple standard light text |
| Secondary | `#86868b` | Apple secondary label |
| Accent | `#0A84FF` | Apple system blue (dark) |
| Keywords | `#FF6482` | Warm pink |
| Strings | `#30D158` | Apple system green (dark) |
| Functions | `#64D2FF` | Apple system cyan (dark) |
| Types | `#BF5AF2` | Apple system purple (dark) |
| Constants | `#FF9F0A` | Apple system orange (dark) |
| Errors | `#FF453A` | Apple system red (dark) |

## Prerequisites

1. **[Custom UI Style](https://marketplace.visualstudio.com/items?itemName=subframe7536.custom-ui-style)** extension by subframe7536

   This extension injects CSS into VS Code to enable the glass/rounded/floating effects. The theme color tokens alone cannot achieve these visual effects.

## Installation

### Step 1: Install the Frostbyte Theme

**Option A — Local install (recommended for development):**

1. Copy or symlink this folder to your VS Code extensions directory:
   - **Windows:** `%USERPROFILE%\.vscode\extensions\frostbyte`
   - **macOS:** `~/.vscode/extensions/frostbyte`
   - **Linux:** `~/.vscode/extensions/frostbyte`

2. Reload VS Code

**Option B — Install from VSIX:**

```bash
# First, package the extension
npm install -g @vscode/vsce
vsce package
code --install-extension frostbyte-0.1.0.vsix
```

### Step 2: Activate the Color Theme

1. Open Command Palette (`Ctrl+Shift+P` / `Cmd+Shift+P`)
2. Type **"Preferences: Color Theme"**
3. Select **"Frostbyte"**

### Step 3: Enable CSS Customizations

1. Install [Custom UI Style](https://marketplace.visualstudio.com/items?itemName=subframe7536.custom-ui-style) extension
2. Open your VS Code `settings.json` (`Ctrl+Shift+P` → "Preferences: Open User Settings (JSON)")
3. Copy the contents of this project's `settings.json` and merge them into your user settings
4. Open Command Palette → type **"Custom UI Style: Enable"**
5. VS Code will reload

> **Note:** You'll see a "Your VS Code installation appears to be corrupt" notification. This is expected and harmless — click the gear icon → "Don't Show Again".

### Step 4 (Optional): Recommended Settings

For the best experience, add these to your `settings.json`:

```json
{
  "editor.fontFamily": "'SF Mono', 'Fira Code', 'Cascadia Code', Menlo, monospace",
  "editor.fontLigatures": true,
  "editor.fontSize": 13,
  "editor.lineHeight": 1.6,
  "editor.cursorBlinking": "smooth",
  "editor.cursorSmoothCaretAnimation": "on",
  "editor.smoothScrolling": true,
  "workbench.list.smoothScrolling": true,
  "terminal.integrated.smoothScrolling": true,
  "editor.bracketPairColorization.enabled": true,
  "editor.guides.bracketPairs": "active",
  "editor.minimap.enabled": false,
  "window.titleBarStyle": "custom"
}
```

## After VS Code Updates

VS Code updates may reset the CSS injection. If the glass effects disappear after an update:

1. Open Command Palette → **"Custom UI Style: Enable"**
2. VS Code will reload with effects restored

## Troubleshooting

| Issue | Solution |
|-------|----------|
| Glass effects not showing | Ensure Custom UI Style is installed and enabled |
| "Corrupt installation" warning | Click gear → "Don't Show Again" (cosmetic warning) |
| Effects disappeared after update | Re-enable Custom UI Style from Command Palette |
| Rounded corners look clipped | Ensure `window.titleBarStyle` is set to `"custom"` |
| Activity bar not pill-shaped | The CSS targets specific VS Code DOM selectors that may change across versions |

## Architecture

```
frostbyte/
├── package.json        ← Extension manifest (registers the color theme)
├── themes/
│   └── frostbyte.json  ← Color theme (workbench colors + syntax tokens)
├── settings.json       ← CSS customizations (merge into user settings)
├── README.md           ← This file
└── LICENSE             ← MIT License
```

The extension has two layers:

1. **Color Theme** (`themes/frostbyte.json`) — Standard VS Code theme API. Controls all colors: backgrounds, foregrounds, accent colors, and syntax highlighting. All border tokens are set to transparent so the CSS glass borders take visual priority.

2. **CSS Customizations** (`settings.json`) — Delivered via the Custom UI Style extension. Controls visual effects impossible with the theme API: rounded corners, floating panels with margins, glass-effect directional borders, pill-shaped scrollbar thumbs, hover transitions, dim/reveal effects on status bar and breadcrumbs, and more.

## License

MIT

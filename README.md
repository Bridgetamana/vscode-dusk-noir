# Dusk Noir

A VS Code theme inspired by Apple's design. Floating panels, rounded corners, smooth hover effects. It also comes in dark and light.

<!-- TODO: Add screenshot here -->

## Setup

You need two things: the theme itself and the [Custom UI Style](https://marketplace.visualstudio.com/items?itemName=subframe7536.custom-ui-style) extension (this is what makes the rounded corners and floating panels possible).

### Install the theme

Copy this folder to your VS Code extensions directory:

- **Windows:** `%USERPROFILE%\.vscode\extensions\dusk-noir`
- **macOS / Linux:** `~/.vscode/extensions/dusk-noir`

Then reload VS Code.

Or build a VSIX:

```bash
npm install -g @vscode/vsce
vsce package
code --install-extension dusk-noir-0.2.0.vsix
```

### Pick your theme

1. `Ctrl+Shift+P` (or `Cmd+Shift+P` on Mac)
2. Type **Color Theme**
3. Choose **Dusk Noir Dark** or **Dusk Noir Light**

### Turn on the UI effects

1. Install [Custom UI Style](https://marketplace.visualstudio.com/items?itemName=subframe7536.custom-ui-style)
2. Open your user `settings.json` (`Ctrl+Shift+P` → **Open User Settings (JSON)**)
3. Copy the `"custom-ui-style.stylesheet"` block from this project's `settings.json` into yours
4. `Ctrl+Shift+P` → **Custom UI Style: Reload**

You'll get a "corrupt installation" warning. It's harmless — click the gear icon and dismiss it.

### Optional: nice extras

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
  "editor.minimap.enabled": false,
  "window.titleBarStyle": "custom"
}
```

## Colors

### Dark

| Role | Color | What it is |
|------|-------|------------|
| Canvas | `#141416` | Background behind panels |
| Panels | `#1c1c1e` | Sidebar, editor |
| Text | `#f5f5f7` | Primary text |
| Accent | `#0A84FF` | Apple system blue |
| Keywords | `#FF6482` | Pink |
| Strings | `#30D158` | Apple green |
| Functions | `#64D2FF` | Apple cyan |
| Types | `#BF5AF2` | Apple purple |
| Constants | `#FF9F0A` | Apple orange |

### Light

| Role | Color | What it is |
|------|-------|------------|
| Canvas | `#ececee` | Background behind panels |
| Panels | `#f5f5f7` | Sidebar, editor |
| Text | `#1d1d1f` | Primary text |
| Accent | `#007AFF` | Apple system blue |
| Keywords | `#FF2D55` | Apple pink |
| Strings | `#34C759` | Apple green |
| Functions | `#0071e3` | Apple link blue |
| Types | `#AF52DE` | Apple purple |
| Constants | `#FF9500` | Apple orange |

## After a VS Code update

VS Code updates can reset the CSS injection. If the effects disappear, run **Custom UI Style: Reload** from the command palette.

## Troubleshooting

| Problem | Fix |
|---------|-----|
| No rounded corners or floating panels | Make sure Custom UI Style is installed and enabled |
| "Corrupt installation" warning | Dismiss it — it's cosmetic |
| Corners look cut off | Set `window.titleBarStyle` to `"custom"` |

## How it works

The theme has two parts:

1. **Color themes** (`themes/dusk-noir-dark.json` and `themes/dusk-noir-light.json`) — standard VS Code theme files that set all the colors and syntax highlighting.

2. **CSS overrides** (`settings.json`) — custom CSS injected by the Custom UI Style extension. This handles the floating panels, rounded corners, hover effects, and transitions that VS Code's theme API can't do on its own.

## License

MIT

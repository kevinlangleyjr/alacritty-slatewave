<div align="center">

<img src="docs/logo.png" alt="Slatewave" width="840" />

# Slatewave (Alacritty)

A Slatewave theme for [Alacritty](https://alacritty.org) — slate foundation, teal signature. Part of the [Slatewave family](#slatewave-family) — one palette across editors, terminals, prompts, notes, and more.

> _Slate below, teal above._

</div>

---

## What it styles

Slatewave for Alacritty ships as two files. Pick one:

- **`slatewave.toml`** — palette only. Colors, cursor tint, selection, search, hints, footer. Composes with whatever font, window, and cursor-shape settings you already have.
- **`slatewave-full.toml`** — palette + opinionated typography. Imports `slatewave.toml`, then adds Hack Nerd Font Mono at 14pt, a non-blinking block cursor, and a fully opaque, unblurred window. Use this if you want the whole Slatewave house style in one import.

The palette itself is tuned against Alacritty's full color schema — not just the 16 ANSI colors. It sets:

- **ANSI 0–15** — mirrored from the VSCode Slatewave terminal block so `ls --color`, `git diff`, and 256-color TUIs all read identically across your editor and terminal
- **Background** — slate `#282c34`, matching the VSCode editor background
- **Foreground** — slate-200 `#e2e8f0`, matching the VSCode editor foreground
- **Cursor** — teal `#5eead4` with slate-background text, so the block cursor stays legible
- **Vi-mode cursor** — teal-200 `#99f6e4`, distinguishable from the regular cursor at a glance
- **Selection** — slate-700 `#334155` with slate-200 text, for a calm, non-competing highlight
- **Search** — sky `#38bdf8` for unfocused matches, teal `#5eead4` for the focused match (mirrors VSCode's `findMatchHighlight` / `findMatch` split)
- **Hints** — amber `#fbbf24` leader on amber-700 `#b45309` tail, for `⌘`-click-replacement keyboard hints
- **Footer bar** — chrome `#21252b` background matching the VSCode activity bar

---

## Installation

### Palette only (`slatewave.toml`)

Alacritty 0.13+ reads TOML config and supports importing theme files. The recommended layout is `~/.config/alacritty/themes/` for user-managed themes.

```sh
mkdir -p ~/.config/alacritty/themes
curl -fsSL https://raw.githubusercontent.com/kevinlangleyjr/alacritty-slatewave/main/slatewave.toml \
  -o ~/.config/alacritty/themes/slatewave.toml
```

Then reference it from your `~/.config/alacritty/alacritty.toml`:

```toml
[general]
import = ["~/.config/alacritty/themes/slatewave.toml"]
```

Alacritty watches its config file and applies theme changes live — no restart needed.

### Palette + typography (`slatewave-full.toml`)

The full bundle assumes `slatewave.toml` is installed at the standard path above, then imports it and adds font / cursor / window defaults. Requires [Hack Nerd Font](https://www.nerdfonts.com/font-downloads) — specifically the Mono variant, so Nerd icons stay single-cell in `lazygit`, `btop`, and `ls`.

```sh
curl -fsSL https://raw.githubusercontent.com/kevinlangleyjr/alacritty-slatewave/main/slatewave-full.toml \
  -o ~/.config/alacritty/themes/slatewave-full.toml
```

Then in `~/.config/alacritty/alacritty.toml`:

```toml
[general]
import = ["~/.config/alacritty/themes/slatewave-full.toml"]
```

### From a local clone

```sh
git clone https://github.com/kevinlangleyjr/alacritty-slatewave
cp alacritty-slatewave/slatewave.toml      ~/.config/alacritty/themes/
cp alacritty-slatewave/slatewave-full.toml ~/.config/alacritty/themes/  # optional
```

### Inline

If you'd rather not manage a separate theme file, paste the contents of [`slatewave.toml`](./slatewave.toml) directly into your `~/.config/alacritty/alacritty.toml` — the `[colors.*]` tables work at the top level of the main config too.

---

## Palette

Slatewave shares its palette with the companion themes. The anchor colors:

| | Hex | Tailwind | Role |
|---|---|---|---|
| ![#282c34](https://placehold.co/20x20/282c34/282c34.png) | `#282c34` | — | **background** |
| ![#21252b](https://placehold.co/20x20/21252b/21252b.png) | `#21252b` | — | footer bar |
| ![#334155](https://placehold.co/20x20/334155/334155.png) | `#334155` | slate-700 | selection background |
| ![#1e293b](https://placehold.co/20x20/1e293b/1e293b.png) | `#1e293b` | slate-800 | ANSI 0 (black) |
| ![#e2e8f0](https://placehold.co/20x20/e2e8f0/e2e8f0.png) | `#e2e8f0` | slate-200 | **foreground**, ANSI 7 (white) |
| ![#5eead4](https://placehold.co/20x20/5eead4/5eead4.png) | `#5eead4` | teal-300 | **cursor, focused search**, ANSI 2 (green) |
| ![#99f6e4](https://placehold.co/20x20/99f6e4/99f6e4.png) | `#99f6e4` | teal-200 | **vi-mode cursor**, ANSI 10 (bright green) |
| ![#7dd3fc](https://placehold.co/20x20/7dd3fc/7dd3fc.png) | `#7dd3fc` | sky-300 | ANSI 12 (bright blue) |
| ![#38bdf8](https://placehold.co/20x20/38bdf8/38bdf8.png) | `#38bdf8` | sky-400 | **search matches**, ANSI 4 (blue) |
| ![#b388ff](https://placehold.co/20x20/b388ff/b388ff.png) | `#b388ff` | — | ANSI 5 (magenta) |
| ![#fb7185](https://placehold.co/20x20/fb7185/fb7185.png) | `#fb7185` | rose-400 | ANSI 1 (red) |
| ![#fbbf24](https://placehold.co/20x20/fbbf24/fbbf24.png) | `#fbbf24` | amber-400 | **hint leader**, ANSI 11 (bright yellow) |

### ANSI mapping

Mirrors the `terminal.ansi*` block from [vscode-slatewave](https://github.com/kevinlangleyjr/vscode-slatewave/blob/main/themes/slatewave-color-theme.json) so shell output is consistent across editor and terminal.

| Slot | Normal | Bright |
|---|---|---|
| Black | `#1e293b` slate-800 | `#475569` slate-600 |
| Red | `#fb7185` rose-400 | `#ef5350` |
| Green | `#5eead4` teal-300 | `#99f6e4` teal-200 |
| Yellow | `#b45309` amber-700 | `#fbbf24` amber-400 |
| Blue | `#38bdf8` sky-400 | `#7dd3fc` sky-300 |
| Magenta | `#b388ff` | `#c4b5fd` violet-300 |
| Cyan | `#0e7490` cyan-700 | `#67e8f9` cyan-300 |
| White | `#e2e8f0` slate-200 | `#f1f5f9` slate-100 |

---

## Customize

The theme file is a plain Alacritty config fragment — every entry is a TOML table. To override a single color without forking, put the override _after_ the `import` line in `~/.config/alacritty/alacritty.toml`:

```toml
[general]
import = ["~/.config/alacritty/themes/slatewave.toml"]

# Override just the cursor
[colors.cursor]
cursor = "#99f6e4"
text   = "#282c34"
```

Later values win in Alacritty's merge order, so the override takes effect without editing the theme file itself.

---

## Slatewave family

One palette. Every tool.

- **Editors** — [VSCode](https://github.com/kevinlangleyjr/vscode-slatewave) · [Neovim](https://github.com/kevinlangleyjr/neovim-slatewave) · [Helix](https://github.com/kevinlangleyjr/helix-slatewave) · [Zed](https://github.com/kevinlangleyjr/zed-slatewave) · [Sublime Text](https://github.com/kevinlangleyjr/sublime-text-slatewave) · [JetBrains](https://github.com/kevinlangleyjr/jetbrains-slatewave)
- **Terminals** — [Ghostty](https://github.com/kevinlangleyjr/ghostty-slatewave) · [iTerm2](https://github.com/kevinlangleyjr/iterm2-slatewave) · [WezTerm](https://github.com/kevinlangleyjr/wezterm-slatewave) · [Windows Terminal](https://github.com/kevinlangleyjr/windows-terminal-slatewave)
- **Prompts** — [Oh My Posh](https://github.com/kevinlangleyjr/slatewave-omp) · [Starship](https://github.com/kevinlangleyjr/starship-slatewave)
- **Multiplexer** — [tmux](https://github.com/kevinlangleyjr/tmux-slatewave)
- **Notes** — [Obsidian](https://github.com/kevinlangleyjr/obsidian-slatewave) · [Logseq](https://github.com/kevinlangleyjr/logseq-slatewave)
- **Launchers** — [Alfred](https://github.com/kevinlangleyjr/alfred-slatewave) · [Raycast](https://github.com/kevinlangleyjr/raycast-slatewave)
- **Chat** — [Slack](https://github.com/kevinlangleyjr/slack-slatewave)

See [getslatewave.com](https://getslatewave.com) for the full family.

---

## Contributing

Issues and PRs welcome. For palette changes, include a before/after screenshot of the same terminal session (`ls --color`, `git diff`, a TUI like `lazygit` or `btop`) so the visual tradeoff is obvious.

---

## License

WTFPL — Do What The Fuck You Want To Public License. See [LICENSE](LICENSE).

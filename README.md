# Zed configuration: documented changes

This repository contains a Zed configuration bundle (settings, keybindings, tasks, and a helper script). Below is a complete, human-readable description of what each file changes from Zed defaults.

## settings.json

### UI, layout, and visuals
- Enables bracket colorization and code lens.
- Shows toolbar code actions.
- Shows signature help automatically and after edits.
- Enables inline blame.
- Enables experimental status bar display.
- Always shows line numbers and **relative** line numbers.
- Uses a **bar** cursor with blinking enabled.
- Uses system window tabs.
- Always shows whitespace and enables **hard tabs**.
- Git panel uses tree view and is docked on the **right**.
- Icon theme: **Material Icon Theme** (dark), **Catppuccin Mocha** (light).
- Theme: **Nord Dark** (dark), **Tokyo Night Light** (light).
- UI font size **17**, buffer font size **18.5**.
- Buffer font family **Maple Mono NF** with fallback list:
  - Maple Mono NF
  - JetBrainsMono Nerd Font Mono
  - Menlo
  - Monaco
  - Courier New
- File finder modal width set to **medium**.
- Tab bar is always shown.
- Scrollbar is hidden.
- Tabs show diagnostics **errors only**.
- Indent guides enabled with **indent_aware** coloring.
- Centered layout (zen-like): left/right padding **0.15**.
- Project, outline, and collaboration panels docked on the **right**.
- Project panel: button visible, git status shown, auto-fold **disabled**.

### Editing and behavior
- Vim mode enabled.
- Which-key enabled with **500ms** delay.
- Inlay hints enabled globally.
- Autosave after **1000ms** delay.
- CLI `zed` open behavior: **reuse existing window**.
- Redacts private values in logs/telemetry.

### AI / agent configuration
- Edit predictions provider: **GitHub Copilot**.
- Shows edit predictions.
- Agent sidebar docked **right**, default profile **write**.
- Default model: **copilot_chat / gpt-5.2-codex**.
- Favorite models:
  - copilot_chat / claude-sonnet-4.6
  - copilot_chat / gpt-5.2-codex
  - copilot_chat / claude-opus-4.6
- Inline assistant model set to **copilot_chat / auto**.
- Tool permissions default **allow** for `fetch` and `terminal`.
- Registers several agent servers (registry): `pi-acp`, `kilo`, `github-copilot-cli` (default model **gpt-5.2-codex**), `gemini`, `cursor`, `codex-acp`, `claude-acp`, `amp-acp`, `factory-droid`, `github-copilot`, `opencode` (favorite model **opencode-go/glm-5.1**).

### Language models (custom providers)
- `ollama` API URL: `http://localhost:11434`.
- `openai_compatible` provider **CrofAI** with several large-model entries, including:
  - Kimi K2.6 / K2.6 Precision
  - Qwen 3.5 / Qwen 3.6
  - Deepseek V4 Pro / Precision
  - GLM 5.1 / Precision

### LSP and language-specific settings
- Tailwind CSS language server: class attributes include `class`, `className`, `ngClass`, `styles`.
- **TypeScript**: show whitespace, edit predictions, hard tabs, inlay hints (no parameter hints).
- **Python**:
  - Show whitespace, edit predictions, hard tabs.
  - Format on save via **ruff**.
  - Language servers: `ty`, `ruff`, and explicitly disables `basedpyright`, `pyrefly`, `pyright`, `pylsp`.

### Terminal
- Terminal font size **17.0**, font family **Maple Mono NF**.
- Shows count badge.
- Sets `EDITOR=zed --wait` for terminal sessions.

### File handling
- File types:
  - Dockerfile patterns: `Dockerfile`, `Dockerfile.*`
  - JSON includes `jsonc` and `*.code-snippets`
- File scan exclusions expand defaults with:
  `out`, `dist`, `.husky`, `.turbo`, `.vscode-test`, `.vscode`, `.next`,
  `.storybook`, `.tap`, `.nyc_output`, `report`, `node_modules`.

### Telemetry
- Diagnostics **enabled**, metrics **disabled**.

### Collaboration/session
- Trusts all worktrees for session.

## keymap.json

### Vim normal/visual mode (leader: `space`)
- Git: `space g h d` toggle selected diff hunks, `space g s` toggle git panel focus.
- Toggles: `space t i` inlay hints, `space u w` soft wrap, `space c z` centered layout.
- Markdown preview: `space m p` open, `space m P` open to side.
- Projects: `space f p` open recent.
- Search: `space s w` search word under cursor, `space s b` buffer search.
- AI: `space a c` toggle agent focus.
- `g f` open excerpts (go-to-file).

### Vim normal mode
- Pane movement: `ctrl-h/j/k/l`.
- LSP: `space c a` or `space .` code actions, `space c r` rename.
- Navigation: `g d/D` def, `g i/I` impl, `g t/T` type def, `g r` references.
- Diagnostics: `] d`/`[ d` next/prev.
- Symbol search: `s s` outline, `s S` project symbols.
- Diagnostics panel: `space x x`.
- Git hunks: `] h`/`[ h` next/prev.
- Buffers: `shift-h/l` previous/next, `shift-q` or `ctrl-q` close, `space b d` close, `space b o` close others.
- Save: `ctrl-s`.
- File finder: `space space`.
- Project search: `space /`.
- Reveal in project panel: `space e`.

### Empty pane / shared screen
- `space space` file finder.
- `space f p` open recent.

### Visual mode
- `g c` toggle comments.

### Insert mode escape
- `j j` or `j k` to exit insert mode.

### Operator-pending tweaks
- While `c` operator is pending: `r` triggers rename, `a` opens code actions.

### Terminal and panels
- Toggle terminal panel: `ctrl-\`.
- Terminal pane movement: `ctrl-h/j/k/l`.
- Project panel (netrw-like):
  - `a` new file, `A` new dir, `r` rename, `d` delete, `x` cut, `c` copy, `p` paste.
  - `q` or `space e` toggle right dock.
  - `ctrl-h/j/k/l` move between panes.
- Dock movement: `ctrl-w h/j/k/l`.

### Tasks
- `space r t` runs nearest task.
- `ctrl-shift-p` runs **Save clipboard image (Hugo)** task.

### Sneak motion and which-key
- `s` / `S` mapped to Sneak forward/backward.
- `space` default in VimControl unbound to enable which-key.
- File finding: `space f f` file finder, `space f g` project search.

### Unbinds / rebinds
- `ctrl-b` remapped to **toggle right dock** (left dock toggle unbound).
- `ctrl-alt-b` right dock toggle unbound.
- `ctrl-g` unbound from Vim location/literal in VimControl.
- `ctrl-t` unbound from project symbols, older tag, and indent in insert mode.
- Threads sidebar: `ctrl-shift-t` toggles thread history, `ctrl-g` unbound.
- Git panel: `ctrl-shift-g` bound to toggle (focus binding unbound).

## tasks.json

Two tasks are defined:
1. **Save clipboard image (Hugo)**  
   Runs `/home/titus/.local/bin/save-img-hugo` in a new terminal, reveals in dock, hides on success, and saves the current file. Triggered by `ctrl-shift-p`.
2. **Launch Neovide**  
   Runs `neovide` in the current terminal, reveals in dock without focus, hides on success.

## save-img-hugo

Helper script used by the **Save clipboard image (Hugo)** task:
- Requires `cwebp` in `PATH`.
- Expects `ZED_FILE` to be set to a **.md** file (Zed provides this when run from a markdown buffer).
- Prompts for a filename (TTY, `zenity`, or `kdialog`), default `img-YYYYMMDD-HHMMSS`.
- Saves WebP to:  
  `/home/titus/github/website/static/images/<year>/<name>.webp`
- Inserts a Markdown image link into the current file, at `ZED_ROW` when available.
- Copies the Markdown link to the clipboard.


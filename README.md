# My config files

Config files for language-specific development and for the environment in general.

- :snake: **[Python](./python)** — linting (pylintrc, ruff.toml), Makefile
- :apple: **[macOS / Terminal](./dot)** — iTerm2 profile, `.zshrc`, shell config
- :robot: **[LLM / Pi Agent](./llm)** — Pi Coding Agent extensions, settings, shell integration
- :floppy_disk: **[DBeaver](./dbeaver)** — SQL client settings

---

## System

### macOS

#### System information

- [Show RAM utilization info: vm_stat, top](https://gist.github.com/aalexren/4dba2b850928077e41d3ee2840a15e5b)
- [Interactive LSCOLORS / LS_COLORS](https://geoff.greer.fm/lscolors/)
- [GitHub gist — color help](https://gist.github.com/aalexren/f840430608e80f1cdbf466a0c585f45e)

#### Terminal shortcuts

<details>
<summary>macOS Terminal keyboard shortcuts (click to expand)</summary>

Source: [StackOverflow answer](https://stackoverflow.com/a/16687377/7502538)

**Cursor movement**

| Shortcut | Action |
|---|---|
| `Ctrl + A` | Move to beginning of line |
| `Ctrl + E` | Move to end of line |
| `Ctrl + B` | Move back one character |
| `Ctrl + F` | Move forward one character |
| `Alt + B` | Move back one word |
| `Alt + F` | Move forward one word |
| `Ctrl + Left` | Move to beginning of line |
| `Ctrl + Right` | Move to end of line |

**Editing**

| Shortcut | Action |
|---|---|
| `Ctrl + D` | Delete character under cursor |
| `Ctrl + H` | Delete character before cursor |
| `Ctrl + W` | Delete word before cursor |
| `Alt + D` | Delete word after cursor |
| `Ctrl + K` | Delete to end of line |
| `Ctrl + U` | Delete to beginning of line |
| `Ctrl + T` | Transpose characters |

**History & process control**

| Shortcut | Action |
|---|---|
| `Ctrl + R` | Reverse search history |
| `Ctrl + P` | Previous command |
| `Ctrl + N` | Next command |
| `Ctrl + L` | Clear screen |
| `Ctrl + C` | Interrupt current process |
| `Ctrl + Z` | Suspend current process |
| `Ctrl + D` | Exit / send EOF |
| `Tab` | Autocomplete |

</details>

*Image also available: [`support/terminal_shortcuts.png`](./support/terminal_shortcuts.png)*

### iTerm2

Profile exported in [`dot/iterm2.json`](./dot/iterm2.json) (import via iTerm2 → Settings → Profiles → Other Actions → Import JSON Profiles).

| Setting | Value |
|---|---|
| Terminal type | `xterm-256color` |
| Normal font | MesloLGS NF Regular 13 |
| Non-ASCII font | Monaco 12 (system font — not redistributable) |
| Window | 100 × 30 |
| Bold font | enabled |
| Visual bell | enabled |
| Transparency | none (opaque) |
| Active color preset | OneHalfLight |
| Auto theme switching | enabled — profile carries light + dark variants (27 keys each), follows macOS appearance |

The profile embeds **both light and dark color variants** (keys like `Ansi 0 Color (Light)` / `Ansi 0 Color (Dark)`). iTerm2 swaps them automatically when macOS switches between Light and Dark mode — no manual switching needed.

#### Fonts

MesloLGS Nerd Font (the profile's normal font) is in [`dot/fonts/`](./dot/fonts):

```
MesloLGSNerdFont-Regular.ttf
MesloLGSNerdFont-Bold.ttf
MesloLGSNerdFont-Italic.ttf
MesloLGSNerdFont-BoldItalic.ttf
```

Install by copying to `~/Library/Fonts/` or double-clicking each file.

#### Color presets

Exported as `.itermcolors` in [`dot/themes/`](./dot/themes) (import via iTerm2 → Settings → Profiles → Colors → Color Presets → Import):

- [`OneHalfLight.itermcolors`](./dot/themes/OneHalfLight.itermcolors) — active preset (light)
- [`Dracula.itermcolors`](./dot/themes/Dracula.itermcolors) — dark
- [`GruvboxLight.itermcolors`](./dot/themes/GruvboxLight.itermcolors) — light, warm

These are the saved presets. The **auto light/dark switching** lives inside the profile itself (`dot/iterm2.json`) via the `(Light)`/`(Dark)` variant keys — importing the profile preserves the automatic switching.

### Homebrew

[Best CLI tools](https://habr.com/ru/articles/711968/) (overview, in Russian)

| Formula | What it does |
|---|---|
| [tldr](https://tldr.sh/) | Simplified, community-driven man pages |
| [tree](https://oldmanprogrammer.net/source.php?dir=projects/tree) | Display directories as trees |
| [zsh-syntax-highlighting](https://github.com/zsh-users/zsh-syntax-highlighting) | Fish-like syntax highlighting for zsh |
| [watch](https://linux.die.net/man/1/watch) | Execute a program periodically, fullscreen output |
| [nmap](https://nmap.org/) | Port scanning utility for large networks |
| [neofetch](https://github.com/dylanaraps/neofetch) | Fast, highly customisable system info script |
| [neovim](https://neovim.io/) | Ambitious Vim-fork focused on extensibility |
| [jq](https://stedolan.github.io/jq/) | Lightweight command-line JSON processor |
| [imagemagick](https://imagemagick.org/) | Tools and libraries to manipulate images |
| [jpegoptim](https://github.com/tjko/jpegoptim) | Utility to optimize JPEG files |
| [ffmpeg](https://ffmpeg.org/) | Play, record, convert, and stream audio and video |
| [fd](https://github.com/sharkdp/fd) | Simple, fast, user-friendly alternative to `find` |
| [eza](https://github.com/eza-community/eza) | Modern replacement for `ls` (maintained fork of `exa`) |
| [bat](https://github.com/sharkdp/bat) | `cat` clone with syntax highlighting and Git integration |
| [ripgrep](https://github.com/BurntSushi/ripgrep) | Faster `grep` alternative, respects gitignore |
| [fzf](https://github.com/junegunn/fzf) | Command-line fuzzy finder |
| [gh](https://cli.github.com/) | GitHub CLI — repos, PRs, issues from the terminal |
| [delta](https://github.com/dandavison/delta) | Syntax-highlighted `git diff` viewer |
| [lazygit](https://github.com/jesseduffield/lazygit) | Terminal UI for Git |
| [cloc](https://github.com/AlDanial/cloc) | Count lines of code by language |

---

## Shell

### ZSH

Config in [`dot/.zshrc`](./dot/.zshrc) — Powerlevel10k theme, oh-my-zsh, syntax highlighting, autosuggestions.

- [oh-my-zsh](https://github.com/ohmyzsh/ohmyzsh/wiki/Plugins) — plugin manager
- [aliases (acs)](https://github.com/ohmyzsh/ohmyzsh/tree/master/plugins/aliases) — handy alias listing
- [powerlevel10k](https://github.com/romkatv/powerlevel10k) — theme

#### oh-my-zsh plugins (active)

- [git](https://github.com/ohmyzsh/ohmyzsh/tree/master/plugins/git) — git shorthand aliases
- [zsh-syntax-highlighting](https://github.com/zsh-users/zsh-syntax-highlighting) — fish-like highlighting
- [zsh-autosuggestions](https://github.com/zsh-users/zsh-autosuggestions) — fish-like suggestions
- [z](https://github.com/ohmyzsh/ohmyzsh/tree/master/plugins/z) — jump to frequent folders

<details>
<summary>Other useful plugins (not active)</summary>

- [zsh-aliases-eza](https://github.com/DarrinTisdale/zsh-aliases-eza) — aliases for `eza` (forked from `exa`)
- [fd](https://github.com/ohmyzsh/ohmyzsh/tree/master/plugins/fd) — oh-my-zsh wrapper
</details>

### Fish shell

<details>
<summary>Fish shell setup</summary>

- [Make default shell](https://stackoverflow.com/questions/453236/how-can-i-set-my-default-shell-on-a-mac-e-g-to-fish)
- [Fisher plugin manager](https://github.com/jorgebucaran/fisher)
- [Git plugin](https://github.com/jhillyerd/plugin-git) (install using fisher, not omf)
- [Tide theme like powerlevel10k](https://github.com/IlanCosman/tide)
- [Z (to easy navigate)](https://github.com/rupa/z)
- [Sponge to clear unrelated history](https://github.com/meaningful-ooo/sponge)
- [Dracula colors](https://github.com/dracula/fish)
- [fish-exa (beauty ls and exa)](https://github.com/gazorby/fish-exa)
- [Bat (better cat command)](https://github.com/sharkdp/bat)
- [fd (easy find command)](https://github.com/sharkdp/fd)
</details>

---

## LLM / Pi Coding Agent

Full setup documented in [`llm/`](./llm) — installed extensions, `settings.json`, custom `pi-compaction-control` extension, and the `pi()` shell tool-excluder function.

- [Pi Coding Agent](https://github.com/earendil-works/pi) — the agent harness
- [pi-compaction-control](https://github.com/aalexren/pi-compaction-control) — my custom extension (context cap + compaction model)
- [pi-lens](https://github.com/apmantza/pi-lens) — LSP diagnostics + code navigation
- [context-mode](https://github.com/mksglu/context-mode) — run code over large outputs without flooding context
- [pi-web-access](https://github.com/nicobailon/pi-web-access) — web search + fetch
- [pi-mcp-adapter](https://github.com/nicobailon/pi-mcp-adapter) — MCP gateway
- [pi-auto-resume](https://github.com/kasaiarashi/pi-auto-resume) — auto-retry on rate limits
- [@latentminds/pi-quotas](https://github.com/latentminds-ai/pi-quotas) — usage/quota tracking
- [@tmustier/pi-extensions](https://github.com/tmustier/pi-extensions) — usage + tab status

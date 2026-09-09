# LLM — Pi Coding Agent setup

This folder documents my [Pi Coding Agent](https://github.com/earendil-works/pi) configuration: the agent itself, installed extensions, settings, and shell integration. Private keys and credentials are excluded.

---

## Pi Coding Agent

| | |
|---|---|
| Version | `0.85.1` |
| Binary | `/opt/homebrew/bin/pi` (Homebrew) |
| Node | `v25.9.0` |
| Config dir | `~/.pi/agent/` |
| Settings | `~/.pi/agent/settings.json` |
| Sessions | `~/.pi/agent/sessions/` |
| Global extensions | `~/.pi/agent/extensions/*/index.ts` (auto-discovered) |
| npm packages | `~/.pi/agent/npm/node_modules/` |
| Docs | https://github.com/earendil-works/pi |

Install:
```bash
brew install pi-coding-agent   # or: npm i -g @earendil-works/pi-coding-agent
```

---

## Settings (`~/.pi/agent/settings.json`)

Credentials and provider-specific model identifiers are redacted (`<provider-model>`).

```json
{
  "lastChangelogVersion": "0.85.1",
  "packages": [
    "npm:@tmustier/pi-usage-extension",
    {
      "source": "npm:@tmustier/pi-tab-status",
      "extensions": ["-tab-status.ts"]
    },
    {
      "source": "npm:pi-lens",
      "skills": [
        "-skills/pi-lens-ast-grep/SKILL.md",
        "-skills/pi-lens-lsp-navigation/SKILL.md",
        "-skills/pi-lens-write-ast-grep-rule/SKILL.md",
        "-skills/pi-lens-write-tree-sitter-rule/SKILL.md"
      ],
      "extensions": ["-dist/index.js"]
    },
    "npm:context-mode",
    "npm:pi-web-access",
    "npm:pi-powerline-footer",
    {
      "source": "npm:pi-themes",
      "themes": [
        "-themes/dracula.json",
        "-themes/gruvbox-dark.json",
        "-themes/gruvbox-light.json",
        "-themes/nord.json",
        "-themes/one-dark.json",
        "-themes/solarized-dark.json",
        "-themes/solarized-light.json",
        "-themes/tokyo-night.json"
      ]
    },
    "npm:pi-mcp-adapter",
    {
      "source": "npm:pi-auto-resume",
      "extensions": ["-auto-resume-on-token-limit.ts"]
    },
    {
      "source": "npm:@latentminds/pi-quotas",
      "extensions": [
        "-src/extensions/command-quotas/index.ts",
        "-src/extensions/command-tokens/index.ts"
      ]
    },
    "npm:pi-compaction-control",
    "npm:pi-context-view"
  ],
  "defaultModel": "<provider-model>",
  "defaultThinkingLevel": "high",
  "persistModelSelection": false,
  "theme": "catppuccin-latte/catppuccin-mocha",
  "modelThinkingLevels": {
    "<provider-model>-prod/<provider-model>": "xhigh"
  },
  "hideThinkingBlock": false,
  "compaction": {
    "enabled": true,
    "reserveTokens": 32768,
    "keepRecentTokens": 30000
  },
  "contextCap": {
    "cap": 256000,
    "matchPatterns": ["*"],
    "models": {
      "<provider-model>": 144000
    },
    "notify": true
  },
  "compactionModel": {
    "model": "current",
    "thinkingLevel": "low"
  },
  "autoResume": {
    "enabled": true,
    "rateLimit": {
      "enabled": true,
      "maxRetries": 5,
      "baseDelayMs": 7000,
      "maxDelayMs": 3600000
    }
  },
  "powerline": "default",
  "terminal": { "showTerminalProgress": true },
  "quietStartup": true,
  "defaultProvider": "<provider-model>-prod",
  "shellPath": "/bin/zsh"
}
```

### Key settings explained

| Setting | Value | Purpose |
|---|---|---|
| `modelThinkingLevels["<provider-model>-prod/<provider-model>"]` | `"xhigh"` | Max thinking budget for the default model — bumped from `high` |
| `hideThinkingBlock` | `false` | Render thinking blocks in the TUI (was hidden) |
| `compaction.reserveTokens` | 32768 | Tokens to reserve below the cap for the summary + reply (pi built-in) |
| `compaction.keepRecentTokens` | 30000 | Recent tokens kept verbatim, not summarized (pi built-in) |
| `contextCap.cap` | 256000 | Default hard cap on every model's effective context window (extension) |
| `contextCap.models.<provider-model>` | 144000 | Per-model granular override — compaction fires at 144000 − 32768 = 111232 (extension) |
| `compactionModel.model` | `"current"` | Use the active conversation model for compaction summaries (extension) |
| `compactionModel.thinkingLevel` | `"low"` | Low thinking during summarization — fits small output budgets (extension) |
| `autoResume.enabled` | true | Auto-retry on rate-limit errors with exponential backoff (pi-auto-resume) |

---

## Installed extensions

| Package | Source | What it does |
|---|---|---|
| [pi-compaction-control](https://github.com/aalexren/pi-compaction-control) | npm | **My extension.** Per-model context-window hard cap + configurable compaction summariser model. `/compaction-model` runtime override, thinking-level bypass, startup validation, `/compaction-control-doctor` serviceability probes |
| [pi-context-view](https://github.com/dimk90/pi-context-view) | npm | Context-usage visualization + inspect hidden parts (system prompt, tool defs, extension injections); `/context` command |
| [pi-lens](https://github.com/apmantza/pi-lens) | npm | LSP diagnostics, code navigation, turn-end error advisory, read-guard |
| [context-mode](https://github.com/mksglu/context-mode) | npm | Run code/commands over large outputs without flooding context; persistent KB |
| [pi-web-access](https://github.com/nicobailon/pi-web-access) | npm | Web search, fetch, claim verification, content retrieval |
| [pi-mcp-adapter](https://github.com/nicobailon/pi-mcp-adapter) | npm | MCP gateway — connect MCP servers (Trino, ClickHouse, etc.) |
| [pi-auto-resume](https://github.com/kasaiarashi/pi-auto-resume) | npm | Auto-retry on rate-limit/network errors with backoff |
| [pi-powerline-footer](https://github.com/nicobailon/pi-powerline-footer) | npm | Powerline status footer |
| [pi-themes](https://www.npmjs.com/package/pi-themes) | npm | Catppuccin + other themes |
| [@latentminds/pi-quotas](https://github.com/latentminds-ai/pi-quotas) | npm | Usage/quota tracking, `/quotas` + `/tokens` commands, status display |
| [@tmustier/pi-usage-extension](https://github.com/tmustier/pi-extensions/tree/main/usage-extension) | npm | Usage tracking |
| [@tmustier/pi-tab-status](https://github.com/tmustier/pi-extensions/tree/main/tab-status) | npm | Tab status display |

### Tool-tax note

These 12 extensions register ~31 tools total (~16K tokens of tool schemas per request). The shell function below excludes rarely-used ones to save ~3.5K tokens.

### pi-compaction-control config & commands

```json
{
  "contextCap": {
    "cap": 256000,
    "matchPatterns": ["*"],
    "models": { "<provider-model>": 144000 },
    "notify": true
  },
  "compactionModel": {
    "model": "current",
    "thinkingLevel": "low"
  }
}
```

| Command | Effect |
|---|---|
| `/compaction-model` | Interactive picker — choose model + thinking level |
| `/compaction-model <provider/model>` | Set model directly (keeps current level) |
| `/compaction-model current` | Use the active conversation model |
| `/compaction-model reset` | Clear override → back to `settings.json` default |
| `/compaction-model status` | Show effective config + source |
| `/compaction-control-doctor` | Run capability probes + show pi-compatibility status |

---

## Shell integration: tool-excluder (`~/.zshrc`)

Injects `--exclude-tools` for agent sessions to cut ~3.5K tool tokens. Bypassed for subcommands (`pi install/list/auth/...`) and info flags (`pi --version/--list-models`).

```zsh
# >>> pi tool-excluder >>>
PI_EXCLUDE_TOOLS_DEFAULT="ctx_purge,ctx_insight,ctx_upgrade,ctx_doctor,ctx_stats,pi_lens_activate_tools,project_report,read_enclosing,lens_diagnostics"
function pi() {
	local exclude="${PI_EXCLUDE_TOOLS-$PI_EXCLUDE_TOOLS_DEFAULT}"
	case "$1" in
		install|remove|uninstall|update|list|auth|config|help)
			command pi "$@"; return $? ;;
	esac
	case "$1" in
		--version|-v|--help|-h|--list-models)
			command pi "$@"; return $? ;;
	esac
	local a
	for a in "$@"; do
		case "$a" in
			--exclude-tools|--no-tools|--tools|-xt|--no-builtin-tools|-nt|-nbt)
				command pi "$@"; return $? ;;
		esac
	done
	[[ -z "$exclude" ]] && { command pi "$@"; return $? }
	command pi --exclude-tools "$exclude" "$@"
}
function pi-full() { PI_EXCLUDE_TOOLS="" command pi "$@"; }
# <<< pi tool-excluder <<<
```

| Invocation | Tools | Notes |
|---|---|---|
| `pi ...` | 22 (was 31) | Default — excludes rarely-used tools |
| `pi-full ...` | 31 | One-off full-tools session |
| `PI_EXCLUDE_TOOLS="" pi ...` | 31 | Bypass for one invocation |
| `pi --no-tools ...` | 0 | Explicit flag always respected |
| `pi list` / `pi --list-models` | — | Subcommands bypass (never see `--exclude-tools`) |

### Excluded tools (still accessible via `ctx` CLI or `pi-full`)

| Tool | Tokens | Why excluded |
|---|---|---|
| `lens_diagnostics` | 1307 | Footer is LSP; turn-end advisory + `lsp_diagnostics` cover errors |
| `ctx_purge` | 606 | Destructive, near-never (`ctx purge` CLI) |
| `project_report` | 478 | One-time project orientation |
| `pi_lens_activate_tools` | 339 | Only for authoring pi-lens rules |
| `read_enclosing` | 335 | `read_symbol` covers most needs |
| `ctx_insight` | 144 | Dashboard opener (`ctx insight` CLI) |
| `ctx_upgrade` | 114 | Run after updates only |
| `ctx_doctor` | 95 | Diagnostics when something breaks |
| `ctx_stats` | 92 | Usage stats, occasional |

---

## Auxiliary configs

### pi-lens (`~/.pi-lens/config.json`)
No config file — using defaults (lens + lsp + tests enabled, turn-end advisory on).

### pi-web-access (`~/.pi/web-search.json`)
No config file — using defaults (all 4 tools enabled: `web_search`, `source_check`, `fetch_content`, `get_search_content`).

---

## Layout

```
~/.pi/agent/
├── settings.json              # main config (packages, compaction, caps, model)
├── extensions/
│   ├── powerline-footer/      # empty (footer served by npm:pi-powerline-footer)
│   └── quotas.json            # @latentminds/pi-quotas runtime config (v0.5.0)
├── npm/node_modules/          # npm-installed packages (incl. pi-compaction-control, pi-context-view)
└── sessions/                  # session history

~/.pi-lens/                    # pi-lens config (defaults)
~/.pi/web-search.json          # pi-web-access config (defaults)
~/.zshrc                       # pi() shell function (tool-excluder)
```

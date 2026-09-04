# VS Code

User settings and extension list for VS Code, exported from
`~/Library/Application Support/Code/User/` on macOS.

## Files

| File | Source | Notes |
|---|---|---|
| [`settings.json`](./settings.json) | `…/Code/User/settings.json` | `yaml.schemas` block removed (machine-pinned `file:///` absolute paths). |
| [`extensions.txt`](./extensions.txt) | `code --list-extensions` | 31 extensions — only themes referenced in `settings.json` are kept; unused themes (`catppuccin.catppuccin-vsc`, `panxiaoan.themes-falcon-vscode`) dropped. |

## Install

### Settings & keybindings

Symlink (so edits flow back) or copy into the VS Code User dir:

```sh
ln -sf "$PWD/vscode/settings.json" ~/Library/Application\ Support/Code/User/settings.json
ln -sf "$PWD/vscode/keybindings.json" ~/Library/Application\ Support/Code/User/keybindings.json
```

### Extensions

```sh
xargs -L1 code --install-extension < vscode/extensions.txt
```

## Themes in use

These are the only theme extensions kept, because `settings.json` references them:

| Setting | Value | Extension |
|---|---|---|
| `workbench.preferredLightColorTheme` | GitHub Light Default | `github.github-vscode-theme` |
| `workbench.preferredDarkColorTheme` | Nord | `arcticicestudio.nord-visual-studio-code` |
| `workbench.iconTheme` | bearded-icons | `beardedbear.beardedicons` |
| `workbench.productIconTheme` | fluent-icons | `miguelsolorio.fluent-icons` |

## Known issue: `colorCustomizations` theme overrides

`workbench.colorCustomizations` has per-theme override blocks (`[GitHub Light Default]`,
`[Nord]`). VS Code 1.130–1.134 flagged every key inside them as
"Property is not allowed" — a JSON-schema bug ([microsoft/vscode#328165](https://github.com/microsoft/vscode/issues/328165)),
fixed in **1.135.0**. The keys are valid and applied at runtime; the warnings were
cosmetic. Do **not** flatten the blocks to top-level — that defeats the per-theme split.

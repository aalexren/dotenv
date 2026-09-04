# VS Code

User settings and extension list, exported from
`~/Library/Application Support/Code/User/` on macOS.

## Install

### Settings

Symlink (edits flow back to the repo) or copy into the VS Code User dir:

```sh
ln -sf "$PWD/vscode/settings.json" ~/Library/Application\ Support/Code/User/settings.json
```

### Extensions

```sh
xargs -L1 code --install-extension < vscode/extensions.txt
```

## Remove

### Settings

```sh
rm ~/Library/Application\ Support/Code/User/settings.json
```

VS Code recreates an empty settings file on next launch.

### Extensions

```sh
xargs -L1 code --uninstall-extension < vscode/extensions.txt
```

## Extensions

| Extension | Marketplace |
|---|---|
| `adamviola.parquet-explorer` | [marketplace](https://marketplace.visualstudio.com/items?itemName=adamviola.parquet-explorer) |
| `arcticicestudio.nord-visual-studio-code` | [marketplace](https://marketplace.visualstudio.com/items?itemName=arcticicestudio.nord-visual-studio-code) |
| `beardedbear.beardedicons` | [marketplace](https://marketplace.visualstudio.com/items?itemName=beardedbear.beardedicons) |
| `charliermarsh.ruff` | [marketplace](https://marketplace.visualstudio.com/items?itemName=charliermarsh.ruff) |
| `eamodio.gitlens` | [marketplace](https://marketplace.visualstudio.com/items?itemName=eamodio.gitlens) |
| `editorconfig.editorconfig` | [marketplace](https://marketplace.visualstudio.com/items?itemName=editorconfig.editorconfig) |
| `franneck94.vscode-python-dev-extension-pack` | [marketplace](https://marketplace.visualstudio.com/items?itemName=franneck94.vscode-python-dev-extension-pack) |
| `github.github-vscode-theme` | [marketplace](https://marketplace.visualstudio.com/items?itemName=github.github-vscode-theme) |
| `hogashi.crontab-syntax-highlight` | [marketplace](https://marketplace.visualstudio.com/items?itemName=hogashi.crontab-syntax-highlight) |
| `llvm-vs-code-extensions.vscode-clangd` | [marketplace](https://marketplace.visualstudio.com/items?itemName=llvm-vs-code-extensions.vscode-clangd) |
| `mechatroner.rainbow-csv` | [marketplace](https://marketplace.visualstudio.com/items?itemName=mechatroner.rainbow-csv) |
| `meta.pyrefly` | [marketplace](https://marketplace.visualstudio.com/items?itemName=meta.pyrefly) |
| `miguelsolorio.fluent-icons` | [marketplace](https://marketplace.visualstudio.com/items?itemName=miguelsolorio.fluent-icons) |
| `mikestead.dotenv` | [marketplace](https://marketplace.visualstudio.com/items?itemName=mikestead.dotenv) |
| `mrinmoybanik.zst-stream-viewer` | [marketplace](https://marketplace.visualstudio.com/items?itemName=mrinmoybanik.zst-stream-viewer) |
| `ms-python.debugpy` | [marketplace](https://marketplace.visualstudio.com/items?itemName=ms-python.debugpy) |
| `ms-python.pylint` | [marketplace](https://marketplace.visualstudio.com/items?itemName=ms-python.pylint) |
| `ms-python.python` | [marketplace](https://marketplace.visualstudio.com/items?itemName=ms-python.python) |
| `ms-python.vscode-pylance` | [marketplace](https://marketplace.visualstudio.com/items?itemName=ms-python.vscode-pylance) |
| `ms-python.vscode-python-envs` | [marketplace](https://marketplace.visualstudio.com/items?itemName=ms-python.vscode-python-envs) |
| `ms-toolsai.jupyter` | [marketplace](https://marketplace.visualstudio.com/items?itemName=ms-toolsai.jupyter) |
| `ms-toolsai.jupyter-keymap` | [marketplace](https://marketplace.visualstudio.com/items?itemName=ms-toolsai.jupyter-keymap) |
| `ms-toolsai.jupyter-renderers` | [marketplace](https://marketplace.visualstudio.com/items?itemName=ms-toolsai.jupyter-renderers) |
| `ms-toolsai.vscode-jupyter-cell-tags` | [marketplace](https://marketplace.visualstudio.com/items?itemName=ms-toolsai.vscode-jupyter-cell-tags) |
| `ms-toolsai.vscode-jupyter-slideshow` | [marketplace](https://marketplace.visualstudio.com/items?itemName=ms-toolsai.vscode-jupyter-slideshow) |
| `ms-vscode-remote.remote-ssh` | [marketplace](https://marketplace.visualstudio.com/items?itemName=ms-vscode-remote.remote-ssh) |
| `ms-vscode-remote.remote-ssh-edit` | [marketplace](https://marketplace.visualstudio.com/items?itemName=ms-vscode-remote.remote-ssh-edit) |
| `ms-vscode.remote-explorer` | [marketplace](https://marketplace.visualstudio.com/items?itemName=ms-vscode.remote-explorer) |
| `redhat.vscode-yaml` | [marketplace](https://marketplace.visualstudio.com/items?itemName=redhat.vscode-yaml) |
| `tamasfe.even-better-toml` | [marketplace](https://marketplace.visualstudio.com/items?itemName=tamasfe.even-better-toml) |
| `thedangander.jsonl-lab` | [marketplace](https://marketplace.visualstudio.com/items?itemName=thedangander.jsonl-lab) |

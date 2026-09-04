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

### Themes & icons

| Extension | What |
|---|---|
| [arcticicestudio.nord-visual-studio-code](https://marketplace.visualstudio.com/items?itemName=arcticicestudio.nord-visual-studio-code) | Nord color theme |
| [github.github-vscode-theme](https://marketplace.visualstudio.com/items?itemName=github.github-vscode-theme) | GitHub color theme |
| [beardedbear.beardedicons](https://marketplace.visualstudio.com/items?itemName=beardedbear.beardedicons) | File icon theme |
| [miguelsolorio.fluent-icons](https://marketplace.visualstudio.com/items?itemName=miguelsolorio.fluent-icons) | Product icon theme |

### Python

| Extension | What |
|---|---|
| [ms-python.python](https://marketplace.visualstudio.com/items?itemName=ms-python.python) | Core Python support |
| [ms-python.vscode-pylance](https://marketplace.visualstudio.com/items?itemName=ms-python.vscode-pylance) | Python language server |
| [ms-python.debugpy](https://marketplace.visualstudio.com/items?itemName=ms-python.debugpy) | Python debugger |
| [charliermarsh.ruff](https://marketplace.visualstudio.com/items?itemName=charliermarsh.ruff) | Python linter & formatter |
| [meta.pyrefly](https://marketplace.visualstudio.com/items?itemName=meta.pyrefly) | Python type checker |
| [franneck94.vscode-python-dev-extension-pack](https://marketplace.visualstudio.com/items?itemName=franneck94.vscode-python-dev-extension-pack) | Python dev extension pack |

### Jupyter & notebooks

| Extension | What |
|---|---|
| [ms-toolsai.jupyter](https://marketplace.visualstudio.com/items?itemName=ms-toolsai.jupyter) | Jupyter notebook support |
| [ms-toolsai.jupyter-keymap](https://marketplace.visualstudio.com/items?itemName=ms-toolsai.jupyter-keymap) | Jupyter keybindings |
| [ms-toolsai.jupyter-renderers](https://marketplace.visualstudio.com/items?itemName=ms-toolsai.jupyter-renderers) | Jupyter output renderers |
| [ms-toolsai.vscode-jupyter-cell-tags](https://marketplace.visualstudio.com/items?itemName=ms-toolsai.vscode-jupyter-cell-tags) | Jupyter cell tags |
| [ms-toolsai.vscode-jupyter-slideshow](https://marketplace.visualstudio.com/items?itemName=ms-toolsai.vscode-jupyter-slideshow) | Jupyter slideshow cells |

### Languages & formats

| Extension | What |
|---|---|
| [redhat.vscode-yaml](https://marketplace.visualstudio.com/items?itemName=redhat.vscode-yaml) | YAML language support |
| [tamasfe.even-better-toml](https://marketplace.visualstudio.com/items?itemName=tamasfe.even-better-toml) | TOML language support |
| [mikestead.dotenv](https://marketplace.visualstudio.com/items?itemName=mikestead.dotenv) | `.env` syntax highlighting |
| [editorconfig.editorconfig](https://marketplace.visualstudio.com/items?itemName=editorconfig.editorconfig) | EditorConfig support |
| [llvm-vs-code-extensions.vscode-clangd](https://marketplace.visualstudio.com/items?itemName=llvm-vs-code-extensions.vscode-clangd) | C/C++ language server |

### Data viewers

| Extension | What |
|---|---|
| [mechatroner.rainbow-csv](https://marketplace.visualstudio.com/items?itemName=mechatroner.rainbow-csv) | CSV highlighter |
| [adamviola.parquet-explorer](https://marketplace.visualstudio.com/items?itemName=adamviola.parquet-explorer) | Parquet file viewer |
| [thedangander.jsonl-lab](https://marketplace.visualstudio.com/items?itemName=thedangander.jsonl-lab) | JSONL viewer |
| [mrinmoybanik.zst-stream-viewer](https://marketplace.visualstudio.com/items?itemName=mrinmoybanik.zst-stream-viewer) | ZST stream viewer |

### Git & remote

| Extension | What |
|---|---|
| [eamodio.gitlens](https://marketplace.visualstudio.com/items?itemName=eamodio.gitlens) | Git superpowers |
| [ms-vscode-remote.remote-ssh](https://marketplace.visualstudio.com/items?itemName=ms-vscode-remote.remote-ssh) | Remote-SSH |
| [ms-vscode-remote.remote-ssh-edit](https://marketplace.visualstudio.com/items?itemName=ms-vscode-remote.remote-ssh-edit) | Remote-SSH edit |
| [ms-vscode.remote-explorer](https://marketplace.visualstudio.com/items?itemName=ms-vscode.remote-explorer) | Remote explorer |

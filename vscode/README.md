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

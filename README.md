# Dev Container Template

A simple template for a devcontainer with my neovim and dotfiles installed. Add custom packages at the end of the Dockerfile to avoid breaking the cached build steps.

## Usage

Designed for me to use with the [devcontainer cli tool](https://www.npmjs.com/package/@devcontainers/cli). To use, run 
```bash
devcontainer up --workspace-folder .
devcontainer exec --workspace-folder . "/bin/bash" 2>/dev/null
```
in a repository with this `.devcontainer` folder.

It also works with vscode. When prompted, press `Reopen in container`.

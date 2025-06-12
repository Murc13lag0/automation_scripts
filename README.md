# Automation Toolkit

A collection of shell scripts for productivity and automation on Arch Linux or other distros (but I use arch btw).

## Environment
!!!Different terminals or editors will cause problems. Adjust manually!!!

* **OS:** Arch Linux
* **Shell:** Bash
* **Terminal:** Alacritty
* **Editor:** Neovim

## Dependencies

Install required packages:

```bash
sudo pacman -S git gh alacritty wmctrl xrandr
```

## Initialization

Ensure your `~/bin` directory is in your `PATH`:

```bash
grep -qxF 'export PATH="$HOME/bin:$PATH"' ~/.bashrc || \
  echo 'export PATH="$HOME/bin:$PATH"' >> ~/.bashrc
source ~/.bashrc
```

If you prefer login shells, have `~/.bash_profile` source `~/.bashrc` or configure Alacritty to launch a login shell.

## Installation

1. Create `~/bin` and copy scripts:

   ```bash
   mkdir -p ~/bin
   cp code git-new ~/bin/
   chmod +x ~/bin/code ~/bin/git-new
   ```
2. Verify `~/bin` is first in your `PATH`:

   ```bash
   type code    # should show ~/bin/code
   type git-new # should show ~/bin/git-new
   ```

## Usage

### `code` script

```bash
code "project_name"
```

* Opens `$HOME/code/project_name/src/*` (or parent directory) in separate Alacritty windows running Neovim.
* Tiles the first two windows side by side automatically.

### `git-new` script

```bash
git-new [repo-name] [public|private]
```

* Prompts to initialize a Git repository if none exists.
* Commits existing files if the repository is empty.
* Creates and pushes to a GitHub repository using the `gh` CLI.

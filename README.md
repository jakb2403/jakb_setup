---

## 1️⃣ Install Prerequisites

On a fresh Ubuntu server image, install the basics:

```bash
sudo apt update
sudo apt install -y git curl neovim npm python3 python3-pip ripgrep
```

Optional (for C/C++ LSPs):

```bash
sudo apt install -y build-essential clang
```

Optional (for Markdown Preview):

```bash
sudo npm install -g markdown-preview.nvim
```

---

## 2️⃣ Clone your config repo

Assuming your repo is at `~/jakb_setup`:

```bash
mkdir -p ~/.config
git clone <your-git-repo-url> ~/.config/nvim
```

* Replace `<your-git-repo-url>` with your repo URL
* The folder structure you have (`init.lua`, `lua/plugins`, etc.) will be preserved

---

## 3️⃣ Install Lazy.nvim Plugins

Open Neovim and run:

```vim
:Lazy sync
```

This will:

* Download all your plugins from GitHub
* Compile any Lua configs
* Run `build` commands where needed (e.g., `markdown-preview.nvim`)

---

## 4️⃣ Optional: Build Markdown Preview

If you use `markdown-preview.nvim`, go into the plugin folder and build it:

```bash
cd ~/.local/share/nvim/lazy/markdown-preview.nvim/app
npm install
```

---

## 5️⃣ Verify

* Open Neovim:

```bash
nvim
```

* Check plugins are installed:

```vim
:Lazy
```

* Test key bindings:

  * `<C-p>` → Telescope file finder
  * `<C-g>` → Telescope live grep
  * `<C-n>` → Neo-tree

---

## 6️⃣ Optional: Tmux Setup

If you also want Tmux (your config in `.tmux.conf`):

```bash
sudo apt install -y tmux curl
mkdir -p ~/.tmux
# copy .tmux.conf from your repo
cp ~/jakb_setup/.tmux.conf ~/.tmux.conf
# Install TPM plugins
git clone https://github.com/tmux-plugins/tpm ~/.tmux/plugins/tpm
tmux source ~/.tmux.conf
```

Then in Tmux: `prefix + I` to install plugins.


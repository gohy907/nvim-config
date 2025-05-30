This is my config for [Neovim v0.11.1](https://github.com/neovim/neovim) powered by [NvChad v2.5](https://github.com/NvChad/NvChad)

# Features
- All features of latest NvChad
- C++ and C# files autocompletion, autoformatting and syntax highlighting
- C++ and C# debuggers:
    - `<leader>db` toggles breakpoint on line
    - `<F5>` starts debugger
    - `<F5>t` stops debugger
    - `<F5>r` restarts debugger
    - `<F6>` steps into the code 
    - `<F7>` steps over the code 
    - `<F8>` steps out of the code
    - **All of these mappings can be easily changed to your taste in "dap" section of [mappings.lua](./lua/mappings.lua)** 
- Automatic installation of neccesary LSP servers, formatters, parsers and linters via `mason.nvim`

# Defaults
- NvDash opens at start 
    - You can disable that by editing [chadrc.lua](./lua/chadrc.lua)
- Comments are in italic 
    - You can change that by editing [chadrc.lua](./lua/chadrc.lua)
- "oxocarbon" theme
    - You can change that via NvChad, press `<leader>th` to change the theme to your liking 


# Pre-requisites
## Ubuntu 

> Apparently, `curl` command installed via `snap` may have some issues with `nvim-treesitter` and it may not get things installed, so I would recommend to reinstall it via `apt`
>
> ```bash
> sudo snap remove curl
> sudo apt install curl
> ```

If you are completely new to Neovim and don't have it installed, don't worry, I got you covered

First of all, install some [Nerd Font](https://www.nerdfonts.com/font-downloads) that suits you as your terminal font 
- Make sure that the font you set doesn't end with Mono to prevent small icons. For exmaple, JetbrainsMono Nerd Font Mono **is not suitable, use JetbrainsMono Nerd Font**

Then install Neovim itself:

```bash
curl -LO https://github.com/neovim/neovim/releases/latest/download/nvim-linux-x86_64.tar.gz
sudo rm -rf /opt/nvim
sudo tar -C /opt -xzf nvim-linux-x86_64.tar.gz
```

Don't forget to include absolute path to Neovim executable in `~/.bashrc` so you don't have to call it's absolute path everytime you run it.
Put this line in the end of `.bashrc` file

```bash
export PATH="$PATH:/opt/nvim-linux-x86_64/bin"
```

You would need to have `python3-venv` installed to install `clangd`

```bash
sudo apt install -y python3-venv
```

You need to have `dotnet` packages installed to have `netcoredbg` and `omnisharp` work

```bash
sudo apt-get update
sudo apt install -y dotnet-sdk-8.0
sudo apt-get install -y aspnetcore-runtime-8.0
sudo apt-get install -y dotnet-runtime-8.0
```

# Installation
## Ubuntu

Delete your previous Neovim configs:

```bash
rm -rf ~/.config/nvim
rm -rf ~/.local/state/nvim
rm -rf ~/.local/share/nvim
```

And install this config: 

```bash
git clone https://github.com/gohy907/nvim ~/.config/nvim && nvim 
```

Wait for `lazy.nvim` to install all the plugins. After that open `mason.nvim` by `:Mason` command and wait it to end installing LSPs and formatters

To install C++ debugger run `:MasonInstall codelldb` and wait for `mason.nvim` to install it

To install C# debugger run `:MasonInstall netcoredbg` and wait for `mason.nvim` to install it

After `mason.nvim` finishes with that, reopen Neovim and you are ready to go!

# Uninstallation
## Ubuntu 

Delete this config with these commands:

```bash
rm -rf ~/.config/nvim
rm -rf ~/.local/state/nvim
rm -rf ~/.local/share/nvim
```

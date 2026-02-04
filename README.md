# ansible-for-development-machine

Ansible playbook that provisions an Ubuntu development workstation.

## What Gets Installed

- **User setup** - Creates user with bash shell
- **Ubuntu packages** - tree, vim, ripgrep, fzf, fd-find, gcc, git, luarocks, make, unzip, curl, cargo, wget, xclip, and more
- **uv** - Python package manager (via snap)
- **Neovim** - Latest release with kickstart.nvim config, pyrefly LSP, set as default editor
- **PowerShell** - Via snap
- **Obsidian** - Via snap, with preconfigured vault at ~/Notes/Default
- **JetBrainsMono Nerd Font** - Installed to user fonts directory
- **Kitty terminal** - With themes, set as default terminal, Ctrl+Alt+T keybinding
- **Docker CE** - With compose plugin, user added to docker group
- **GNOME settings** - 15 minute screen timeout

## Install and Run

```bash
sudo apt update
sudo apt install software-properties-common git --yes
sudo add-apt-repository --yes --update ppa:ansible/ansible
sudo apt install ansible --yes
git clone https://github.com/ManzellaTech/ansible-for-development-machine.git
cd ansible-for-development-machine
ansible-playbook playbook.yml
```

## Project Structure

```
├── playbook.yml      # Main playbook
├── inventory.ini     # Localhost inventory with username variable
├── ansible.cfg       # Ansible configuration
└── tasks/
    ├── user.yml      # User creation
    ├── packages.yml  # Ubuntu apt packages
    ├── uv.yml        # uv Python package manager
    ├── neovim.yml    # Neovim + kickstart.nvim
    ├── powershell.yml
    ├── obsidian.yml  # Obsidian + vault config
    ├── fonts.yml     # JetBrainsMono Nerd Font
    ├── kitty.yml     # Kitty terminal + keybinding
    ├── docker.yml    # Docker CE
    └── gnome.yml     # GNOME settings
```

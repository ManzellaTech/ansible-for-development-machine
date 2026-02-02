# Ansible Dev Environment Playbook

Ansible playbook that provisions an Ubuntu development workstation for user `nmanzella`.

## Project Structure

- `playbook.yml` - Main playbook (single play, runs against localhost)
- `inventory.ini` - Inventory file (localhost with local connection)
- `ansible.cfg` - Ansible config (points to inventory)

## What the Playbook Installs

- User setup (`nmanzella`) with nvim as default editor
- Ubuntu packages (tree, vim, ripgrep, fzf, fd-find, gcc, git, make, etc.)
- tree-sitter-cli (via cargo)
- uv (Python package manager, via official installer)
- Neovim (via PPA) with LazyVim starter config
- Pyrefly LSP (via uv)
- PowerShell + Az module (via Microsoft .deb repo)
- Kitty terminal with Gruvbox Dark theme
- Docker CE with compose plugin

## Running the Playbook

```bash
ansible-playbook playbook.yml
```

Requires `sudo` privileges (`become: true` is set at the play level).

## Conventions

- Target OS is Ubuntu (uses `apt`, Ubuntu PPAs, and `ansible_distribution_version`/`ansible_distribution_release` facts).
- Use fully qualified collection names for modules (e.g., `ansible.builtin.apt`, not `apt`).
- Use `creates` parameter on shell/command tasks for idempotency.
- Use `become_user: "{{ username }}"` for tasks that should run as the user rather than root.
- User-specific paths use the `username` variable (e.g., `/home/{{ username }}/`).

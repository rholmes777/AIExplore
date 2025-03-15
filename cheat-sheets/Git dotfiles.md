# Managing Configuration Files with Git

Here are the best ways to manage your config files with Git without making your entire home directory a repository:

## 1. Bare Git Repository Approach

This is a popular approach that doesn't require symlinks:

```bash
# Create a bare git repository
git init --bare $HOME/.dotfiles

# Create an alias for management
alias dotfiles='git --git-dir=$HOME/.dotfiles/ --work-tree=$HOME'

# Hide untracked files (very important)
dotfiles config --local status.showUntrackedFiles no

# Add the alias to your .bashrc
echo "alias dotfiles='git --git-dir=$HOME/.dotfiles/ --work-tree=$HOME'" >> $HOME/.bashrc
```

Use it like git, but with the 'dotfiles' command:
```bash
dotfiles add .bashrc .vimrc
dotfiles commit -m "Add config files"
dotfiles push origin main
```

## 2. Symlink-Based Approach with GNU Stow

GNU Stow is a symlink farm manager that works well for dotfiles:

```bash
# Install stow
brew install stow  # macOS with Homebrew

# Create a dotfiles directory with subdirectories for each application
mkdir -p ~/dotfiles/bash ~/dotfiles/vim

# Move your config files
mv ~/.bashrc ~/dotfiles/bash/
mv ~/.vimrc ~/dotfiles/vim/

# Use stow to create symlinks
cd ~/dotfiles
stow bash vim  # Creates symlinks to your home directory
```

## 3. Simple DIY Approach

If you prefer a manual approach:

```bash
# Create a dotfiles repository
mkdir ~/dotfiles
cd ~/dotfiles
git init

# Create a setup script
cat > setup.sh << 'EOF'
#!/bin/bash
DOTFILES="$(cd "$(dirname "${BASH_SOURCE[0]}")" && pwd)"

# Create symlinks
ln -sf "$DOTFILES/.bashrc" "$HOME/.bashrc"
ln -sf "$DOTFILES/.vimrc" "$HOME/.vimrc"
# Add more config files as needed
EOF

chmod +x setup.sh
```

The bare repo approach is the most seamless if you're comfortable with Git, while Stow provides better organization for more complex setups.
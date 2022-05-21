# Installation files for my Linux customizations
## These files are made to work on my machine(**Asus UX430UAR**) so there is **NO** guarantee that they will work on all machines

# Clone the repository
```bash
git clone https://github.com/AtifUsmani/dotfiles-i3-archcraft.git
cd dotfiles-i3-archcraft
```

## Building paru from source
```bash
sudo pacman -Sy archlinux-keyring
sudo pacman -S --needed base-devel
git clone https://aur.archlinux.org/paru.git
cd paru
makepkg -si
```

```bash
cd ..
rm -rf paru
paru -Syyu
```

```
paru -S python-pywal i3-gaps archcraft-i3wm ncdu visual-studio-code-bin parsec-bin freedownloadmanager nerd-fonts-jetbrains-mono python-pywalfox nautilus docker auto-cpufreq-git neofetch polybar rofi dunst picom-ibhagwan-git
```

### Enable services
```bash
sudo auto-cpufreq --install
sudo systemctl enable --now auto-cpufreq 
sudo systemctl enable --now docker
```
### Edit grub configuration
Edit /etc/default/grub
```bash
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash intel_pstate=disable"
```
### Regenerate grub configuration
```bash
sudo grub-mkconfig -o /boot/grub/grub.cfg
```
### Make Docker work without administrative privileges
```bash
sudo groupadd docker
sudo usermod -aG docker $USER
```
# Install oh-my-zsh
```bash
sh -c "$(curl -fsSL https://raw.github.com/ohmyzsh/ohmyzsh/master/tools/install.sh)"
```
---

### Move Configuration file for power saving
```bash
sudo mv -f auto-cpufreq.conf /etc/
```

# Install Plugins

```bash
git clone https://github.com/zsh-users/zsh-autosuggestions ${ZSH_CUSTOM:-~/.oh-my-zsh/custom}/plugins/zsh-autosuggestions
git clone https://github.com/zsh-users/zsh-completions ${ZSH_CUSTOM:-${ZSH:-~/.oh-my-zsh}/custom}/plugins/zsh-completions
git clone https://github.com/zsh-users/zsh-syntax-highlighting.git
echo "source ${(q-)PWD}/zsh-syntax-highlighting/zsh-syntax-highlighting.zsh" >> ${ZDOTDIR:-$HOME}/.zshrc
```

## Edit .zshrc file

### Add the following line to your .zshrc file

```
plugins=( 
    zsh-autosuggestions
)

fpath+=${ZSH_CUSTOM:-${ZSH:-~/.oh-my-zsh}/custom}/plugins/zsh-completions/src
```

```bash
source ./zsh-syntax-highlighting/zsh-syntax-highlighting.zsh
```
## Then copy the files from the repository
# Then Reboot

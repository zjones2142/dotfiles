# To use these configs:
check www.atlassian.com/git/tutorials/dotfiles for details on how to import configs to your system after cloning this repo.
(skip to the "Installing your dotfiles onto a new system (or migrating to this setup)" section)

*Note: I will write up a quick recap of the tutorial to include here at some point this week.*

<details><summary><h2>Screenshots:<h2></summary>
![2025-03-30-185935_hyprshot](https://github.com/user-attachments/assets/a986da03-b2e1-4ba8-ac79-45812a744efa)
![2025-03-30-185946_hyprshot](https://github.com/user-attachments/assets/0d909d5d-85a8-4446-a593-f7bfabecd54c)
![2025-03-30-194053_hyprshot](https://github.com/user-attachments/assets/95335d8f-481f-40ac-b0c5-a1fce7a4d155)
![2025-03-30-194146_hyprshot](https://github.com/user-attachments/assets/795830b2-a650-4d3b-92a5-caff8a4e3392)
</details>

## Basic setup from the beginning:
- use archinstall script when installing OS
- use GRUB for bootloader
    - to set up fast auto-boot to arch install:
    - once installed go into /etc/default/grub and add the following lines:
    GRUB_TIMEOUT_STYLE=hidden
    GRUB_TIMEOUT=0
    - and run: sudo grub-mkconfig -o /boot/grub/grub.cfg - to apply changes

- install during arch setup:
  - git
  - yay
  - networkmanager

- install after setup and first boot into OS (using yay -S {package name}):
  - hyprland-meta-git (includes all components within hyprland ecosystem)
  - kitty (default hyprland terminal)

- now config base hyprland (import configs from repo)
  - mainly just need terminal binds setup so you can open kitty within hyprland
  - add following lines to $HOME/.config/hypr/hyprland.conf if needed (this should already be there if you are using my configs):
`$terminal = kitty`
`$mainMod = SUPER`
`bind = $mainMod, Q, exec, $terminal`

- install everything else after base hyprland setup:

### utils/usefull apps:
- wofi
- waybar
- dolphin
- curl
- spotify
- discord
- zen-browser-bin 
- zenity

### customization:
- neofetch
- starship
- pywal

### drivers and tooling:
- pulseaudio
- pulseaudio-alsa
- pipewire
- pavucontrol
- playerctl
- libva
- libva-utils
- libva-intel-driver(per system driver)
- intel-media-driver(insert graphics drivers here)
- openssh
- ffmpeg
- htop
- s-tui

## Additional Notes:
- to start hyprland upon login without a display manager add the following to your .bash_profile (or import from git)
```
if [[ -z $DISPLAY ]] && [[ $(tty) = /dev/tty1 ]]; then
  exec Hyprland
fi
```

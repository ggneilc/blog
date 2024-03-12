---
layout: ../../layouts/BlogLayout.astro
title: 'Arch Linux'
pubDate: '2023-04-14 01:31'
blurb: 'becoming a fully fledged nerd'
tags: ["project","linux"]
---

## Installing Arch linux

You install arch linux like any other operating system. The only catch is that after the intial boot, every other operating system out there takes you through an automated installation process where you pick and choose the things like keyboard layout, time zone, disk partitions, connecting to wifi, then creating your own user, and afterwords you and fresh into you new windows/whatever desktop.

Arch does absolutely ***none*** of this for you :)

### Installing with the live environment

Installing arch works in this order:
1. Flash usb & plug in
	1. boot in UEFI and select the usb to boot from, wait for installation environment to load
2. Now make sure basics are working:
	1. Set the keyboard layout
	2. Connect to internet
	3. update the system clock
3. Now we prep the disks:
	1. partition the disks
	2. format the disks
	3. Mount the partitions

And now we can install arch linux!

1. Select the mirror server to download from
2. install essential packages with pacstrap

	`pacstrap -K /mnt base base-devel linux linux-firmware NetworkManager sudo nvim git `

### Configure the System

1. Generate the fstab file (**f**ile **s**ystem **tab**le)
2. Change the root to the new system
3. Set the time zone
4. Localization
5. Network configuration
6. set root password
7. boot loader

---
## Post install

### Window Manager (Desktop Environment)

Hyprland seems to be the best newest option: it's dynamic, easiest to configure (text-based), smooth, and has nice animations :D

switching to a tiling window manager creates a whole new desktop with *absolutely fucking nothing* on it. Like literally no taskbar no system alerts no notifications or anything because **you** have to install all the things ***you*** want. 

Must-haves:
- notification daemon
- Authentication agent 
- qt5 & qt6 libraries (just normal dependencies)

These are the minimum things a desktop needs to be able to be usable and not require switching over to a different desktop to then configure or download smth required in hyprland.

**notification daemon** -> something running in the background keeping track of and displaying notifications. Best choice: **Dunst**

**authentication agent** -> enables apps to request higher privilege (so your GUI for add/remove software can request root password to download packages). Best Choice: KDE-auth (recommended by hyprland)

First things to add after:
- Status bar
- XDG desktop portal
- app launchers
- wallpaper
- clipboard
- screensharing

**Status bar** -> lots of different options for customizing what and how you want activities/workspaces/system info/weather/time displayed. best choice: **waybar**

you can alternatively use the nwg-shell project's suite of desktop goodies.

**app launcher** -> way to quickly open apps/run files: **tofi**

**wallpaper** -> yes, you need to download a program so you can have a wallpaper: **hyprpaper**

**screensharing**: just a standard app called: **pipeware**

clipboard: cliphist -> lets you also copy images 

desktop portal: xdg-desktop-portal-hyprland-git


###  more downloads

#### CLI tools

- kitty -> terminal
- ranger -> file explorer in terminal
- bat -> better cat command (prints code highlighting)
- btop -> better htop (system information)
- exa (prettier ls command)
- zoxide (better cd command)
- git
	- lazygit
- fzf -> command line fuzzy finder


![[Pasted image 20230414103652.png]]

[ranger command cheat sheet](https://gist.github.com/heroheman/aba73e47443340c35526755ef79647eb)


#### Must have applications

**firefox** -> internet access
**obsidian** -> take notes & 2nd brain
**nvim** -> open any text document/full IDE
**discord** -> communicate with others

with these 4 applications you can seriously do absolutely anything, and it's pretty wild to think about. 

**firefox** -> cascade one line theme -> very minimalist and keyboard friendly (install vimium (maybe make firefox account?))

**neovim** -> better vim, NvChad with minor adjustments -> i will put config files on my github

dickcock & obsidian are self explanatory and lit


---
## Further Enhancements & Productivity

Ideally, this machine should be good at performing any computing related task, be it interface with the network, manage files/users/groups/processes within the system, working with json/spreadsheets/pdf/docx, or creating software / digital art.


desktops should reflect the kind of work that happens:
1. Obsidian -> reading, notetaking (more than enough room to open firefox for readings)
2. Web Dev  nvim
3. System -> anything relating to downloads/users/process/monitoring or *Cyber Security*
4. jetbrains java/data

TV:
 - Large spreadsheets / files
 - Background music
 - communication


**Add desktop files/entries to home/neilc/.local/applications**

### Checklist:

- [x] download fonts
- [x] waybar
- [x] hyprpaper
- [x] authentication agent
- [x] pipeware
- [x] pulseaudio
- [x] clipboard
- [x] screensharing
- [x] configure firefox
- [x] download over projects
- [x] configure bash
- [x] look more into hyprland configs
- [x] configure waybar

- [x] dunst -> better styled notifications
- [x] fix nvim -> make it more tailored for you!
- [x] fix ranger to be able to open all documents types
- [ ] add hyprctrl/kitty scripts to open workspaces 
- [x] figure out difference between kitty & tmux $\to$ kitty and tmux together are fine!

- [x] autologin script that starts Hyprland
- [x] Swaylock
	
- [x] What does wayland let me do/hinder me from doing -> just a display protocol
- [x] see if there are any conflicts with bash & zsh
	
- [ ] make sure all binaries & services are correct, uninstall any applications

- [x] find out why git is requiring this token :
Github Token: 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


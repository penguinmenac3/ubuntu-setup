# ubuntu-setup

## Installation

Follow the default instructions, except for "minimal installation", "updates" and "additional packages" which you should enable.

## Installing Software

```bash
# Install basic tools
sudo apt install vim neofetch tmux screen htop keepass2 gnome-tweaks apt-transport-https curl evolution evolution-ews

# Add flatpack support (e.g. TeamSpeak is a flatpak)
sudo apt install gnome-software-plugin-flatpak
flatpak remote-add --if-not-exists flathub https://flathub.org/repo/flathub.flatpakrepo

# Replace Firefox by Brave
sudo curl -fsSLo /usr/share/keyrings/brave-browser-archive-keyring.gpg https://brave-browser-apt-release.s3.brave.com/brave-browser-archive-keyring.gpg
echo "deb [signed-by=/usr/share/keyrings/brave-browser-archive-keyring.gpg arch=amd64] https://brave-browser-apt-release.s3.brave.com/ stable main"|sudo tee /etc/apt/sources.list.d/brave-browser-release.list
sudo apt update && sudo apt install brave-browser
sudo apt purge firefox
```

## Fast Boot (skipping GRUB)

We need to edit the grub config file.
```bash
sudo vim /etc/default/grub
```

Change/Add the following 3 lines.
```bash
GRUB_DEFAULT=saved
GRUB_HIDDEN_TIMEOUT=0
GRUB_TIMEOUT=0.1
```

After exiting vim update grub and set the default boot option to ubuntu.
```bash
sudo update-grub
sudo grub-set-default 0
```

If you want to boot to windows, simply do the following:
```bash
grub-reboot Windows
```

## Installing Teamspeak

Open "gnome software" and search for "Teamspeak" click install.

## Installing Signal

Install signal with these commands.
```bash
wget -O- https://updates.signal.org/desktop/apt/keys.asc | gpg --dearmor > signal-desktop-keyring.gpg
sudo mv signal-desktop-keyring.gpg /usr/share/keyrings/

echo 'deb [arch=amd64 signed-by=/usr/share/keyrings/signal-desktop-keyring.gpg] https://updates.signal.org/desktop/apt xenial main' |\
  sudo tee -a /etc/apt/sources.list.d/signal-xenial.list

sudo apt update && sudo apt install signal-desktop
```

## Setting up Gnome Extensions

Visit [extensions.gnome.org](https://extensions.gnome.org) and follow the instructions at the top banner/popup to install the plugin for your browser.

Reload the page and install:
* [User Themes](https://extensions.gnome.org/extension/19/user-themes/)
* [GSConnect](https://extensions.gnome.org/extension/1319/gsconnect/) -> KDEConnect
* [Dash to Panel](https://extensions.gnome.org/extension/1160/dash-to-panel/)

You can configure the extensions via extensions.gnome.org or via gnome-tweaks once they are installed.

## Setting up Brave

Enable your sync and add your apps as shortcuts with separate windows (`Hamburger -> More Tools -> Create Shortcut...`).
This allows you to have all your webapps easy to access.

### Installing Teams, Spotify, etc.

Do not install them, use the webapps instead.
* [Teams](https://teams.microsoft.com)
* [Spotify](https://open.spotify.com)

## Setting up Mail/Calendar/Contacts

Open up "Online Accounts" (in Settings) and add your accounts. Imap and google are straight forward.

Now in evolution you will have your mail, calendar, contacts, todos available to you.

If you have an office365 account, you need to set it up as exchange with the server (under advanced) as `outlook.office365.com`.

## Setting up GSConnect

Open "Gnome Tweaks" and navigate to extensions. Click on the little cogwheel (settings) next to gsconnect.

There it will show up available phones in the same network (you need to install and open "kde connect" on your phone first). You can pair by clicking on it and then accepting on the phone. Once paired clicking on the phone changes the settings.


## Have Fun

Have fun! Btw steam and lutris allow for gaming on linux. ;)



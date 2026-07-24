## Pós-instalação básica (Arch Linux após instalar com Plasma + Konsole)

### 1. Configurar pacman (Downloads Paralelos)
```bash
sudo sed -i 's/#ParallelDownloads = 5/ParallelDownloads = 15/' /etc/pacman.conf

```

### 2. Atualizar sistema

```bash
sudo pacman -Syu --noconfirm

```

### 3. Instalar headers do kernel ativo

```bash
sudo pacman -S --needed $(pacman -Qq | grep -E '^linux(-lts|-zen|-hardened)?$' \vert{} sed 's/$/-headers/')

```

### 4. Instalar pacotes oficiais

```bash
sudo pacman -S --needed base-devel git wget curl btop fastfetch cava zip unzip unrar p7zip \
ttf-dejavu ttf-liberation noto-fonts noto-fonts-emoji noto-fonts-cjk timeshift flatpak \
gst-plugins-good gst-plugins-bad gst-plugins-ugly gst-libav ffmpeg libdvdcss \
firefox mpv

```

### 5. Instalar AUR Helper (yay)

```bash
git clone [https://aur.archlinux.org/yay.git](https://aur.archlinux.org/yay.git) /tmp/yay
cd /tmp/yay && makepkg -si --noconfirm

```

### 6. Instalar fontes Microsoft (AUR)

```bash
yay -S --noconfirm ttf-ms-fonts

```

### 7. Configurar Flathub

```bash
flatpak remote-add --if-not-exists flathub [https://dl.flathub.org/repo/flathub.flatpakrepo](https://dl.flathub.org/repo/flathub.flatpakrepo)

```

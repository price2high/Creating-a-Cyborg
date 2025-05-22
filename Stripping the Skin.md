# Creating a Cyborg: Security Lab Diaries

## Entry 18: “Stripping the Skin – Installing Arch on a Corporate Shell”

> *"The machine was born in the system. Raised by policies, locked behind a logo. But today… today it became mine."*

### 📓 Log Start:
The mission was simple: remove the corporate chains of a repurposed HP work laptop and install Arch Linux—a clean slate, fully under my control. But it was more than just swapping OSs. This was a ritual. A rebirth.

The irony? I was doing this from macOS. But that too had to go.

---

### 🔧 The Corpse: HP EliteBook (8GB RAM, 256GB SSD)

Originally a corporate Windows device, someone had installed macOS on it via OpenCore (Hackintosh style). But it ran like a ghost—slow, incompatible, and paranoid. The system didn’t trust itself.

---

### 💥 Step 1: Erase macOS Like a Memory Wipe

I booted from a USB using **Ventoy**, which I loaded with the **Arch ISO**.

```bash
diskpart (on Windows if prepping the USB)
# or use balenaEtcher if you're still on a Mac
```

On boot:
- Hit `F9` for the HP boot menu.
- Selected the Ventoy USB.
- Launched the Arch installer.

**`/dev/sda` was wiped clean.**  
Mac partitions? Gone. I used `cfdisk` to create new ones:
- `/boot` (512MB, EFI)
- `/` (40GB, ext4)
- `/home` (rest of disk, ext4)
- `swap` (2GB)

---

### 🧠 Step 2: Install Arch — Minimalist and Manual

Connected to Wi-Fi using:
```bash
iwctl
station wlan0 connect "Network_Name"
```

Updated mirrors, installed the base system:
```bash
pacstrap /mnt base linux linux-firmware nano networkmanager grub efibootmgr
```

Generated fstab, chrooted in, and did the real magic:
```bash
grub-install --target=x86_64-efi --efi-directory=/boot --bootloader-id=GRUB
grub-mkconfig -o /boot/grub/grub.cfg
```

Created user accounts, passwords, and enabled services:
```bash
systemctl enable NetworkManager
```

---

### 🧰 Step 3: Cybernetic Enhancements

Once rebooted into a pure Arch CLI, I layered in tools:

- `xfce4` + `lightdm` for a lightweight GUI
- `terminator` as my terminal shell
- `neofetch`, `htop`, `btop` to keep tabs on my cyborg’s internals
- `firefox`, `burpsuite`, `wireshark`, `nmap`, `hydra` — the hacker’s toolkit

---

### 🧠 Reflections:

It wasn’t just installing an OS. It was reclaiming control.  
That HP laptop wasn’t mine before. Now, every command it runs, every packet it sees — it does for **me**.

> *"A cyborg isn’t born with chrome limbs or AI cores. Sometimes, it’s built with willpower, a USB stick, and a blank drive."*

---

### 🧪 Outcome:
This machine is now a permanent piece of my cyber lab arsenal — used for live packet inspection, threat emulation, and rogue access testing. It's quiet. It's clean. It's mine.

---

**End Log**

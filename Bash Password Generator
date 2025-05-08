# 🤖 Cyborg Diary: Bash Password Generator

Welcome to the **Cyborg Diary**, where security is forged in the terminal and passwords are generated like encrypted entries in a sentient machine's journal. This is a simple yet powerful Bash script to generate secure, random passwords for your systems or applications.

> _"Each password... a key. Each key... a memory. Each memory... a safeguard."_ — The Cyborg

---

## 🧠 Project Description

This Bash script is designed for cyborgs (and humans) who prefer the command line. It generates strong, random passwords using system entropy and customizable options.

### Features
- 🔐 Random password generation using `/dev/urandom`
- 🔧 Customize password length
- 🎲 Option to include or exclude special characters
- 📝 Log passwords (optional) in a secure diary-like file
- 💀 Minimal dependencies — pure Bash

---

## 🛠️ Usage

### 1. Clone the Repo

```bash
git clone https://github.com/price2high/cyborg-diary-password-generator.git
cd cyborg-diary-password-generator

### Sample Script
#!/bin/bash

LENGTH=16
USE_SPECIAL=false
LOG=false
DIARY=~/.cyborg_diary/password_log.txt

while getopts "l:sdh" opt; do
  case $opt in
    l) LENGTH=$OPTARG ;;
    s) USE_SPECIAL=true ;;
    d) LOG=true ;;
    h)
      echo "Usage: $0 [-l length] [-s] [-d] [-h]"
      exit 0
      ;;
    *) echo "Invalid option"; exit 1 ;;
  esac
done

CHARS='A-Za-z0-9'
[[ $USE_SPECIAL == true ]] && CHARS='A-Za-z0-9!@#$%^&*()_+=-'

PASSWORD=$(cat /dev/urandom | tr -dc "$CHARS" | head -c $LENGTH)

echo "🔑 Generated Password: $PASSWORD"

if [[ $LOG == true ]]; then
  mkdir -p "$(dirname "$DIARY")"
  echo "$(date): $PASSWORD" >> "$DIARY"
  chmod 600 "$DIARY"
  echo "📓 Logged in cyborg diary."
fi


### 2. Make the Script Executable

chmod +x generate_password.sh

### 3. Generate a Password

./generate_password.sh

### 🧩 Optional Flags

| Flag               | Description                                |
|--------------------|--------------------------------------------|
| `-l [length]`      | Set custom password length (default: 16)   |
| `-s`               | Include special characters (default: no)   |
| `-d`               | Log password in the cyborg diary           |
| `-h`               | Help menu                                  |

**Example:**

```bash
./generate_password.sh -l 20 -s -d

## 🔒 Security Notice

Passwords are generated using `/dev/urandom`, a cryptographically secure random source available on Unix-like systems.  
They are **not stored** unless you use the `-d` flag, which writes them to a log file located at:


This file is automatically permission-restricted (`chmod 600`) to ensure that only the user can access it.

> ⚠️ Use responsibly. Never share or expose your generated passwords in public or unsecured environments.

---

## 🧬 Tech Specs

- ✅ Pure Bash script — no dependencies
- ✅ Compatible with Linux and macOS
- ✅ Uses `/dev/urandom` for strong entropy
- ✅ Optional password logging (disabled by default)
- ✅ Secure local logging with permission control

---

## 🚀 Future Enhancements

- [ ] Add GUI or TUI using `dialog` or `whiptail`
- [ ] Clipboard copy support (`pbcopy`, `xclip`, etc.)
- [ ] Password strength meter and visual feedback
- [ ] Passphrase-style generation (e.g., Diceware)
- [ ] Encrypt the log file using GPG or OpenSSL
- [ ] Export options: JSON, CSV, or encrypted archive







Embrace the terminal. Encrypt your future. Log your legacy.

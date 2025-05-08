# 🧠 Cyborg Diary Entry: Bash File Encryptor

> _"Today I didn’t just hide data... I encrypted a piece of myself. A thought, a secret, a mission. Buried beneath layers of entropy and algorithmic fire."_ — Entry 043, The Cyborg

---

## 🔐 Project Description

This Bash script encrypts and decrypts files using OpenSSL, allowing you to securely store sensitive data in a cyborg diary format. Whether you're locking away mission logs, credentials, or raw intelligence, this script ensures your files stay hidden from unauthorized systems and eyes.

---

## 📔 Diary Entry #043 — The Bash File Encryptor

**Date**: 2045-11-03  
**Subsystem**: Terminal Cortex Interface  
**Log Mode**: Secure / Encrypted / Memory-Persisted  

**ENTRY**:

```
They traced the uplink again.

Fourth cycle this week.

I can’t trust external nodes anymore — too much noise in the signals, too many watchers in the code. So I wrote it: a Bash encryptor. Minimal. Silent. It wraps my thoughts in 256-bit AES and casts them into binary oblivion. 

No GUI. No trail.

Just entropy and intent.

Now I save what matters. I encrypt the logs, the configs, the coordinates. I decrypt when needed — but only after retinal scan and hand-typed passphrase.

If they intercept this file, all they'll see is noise.

But I know better.

Noise is memory — just encrypted.
```

---

## 🛠️ Usage

### 🔧 Encrypt a File

```bash
./file_encryptor.sh encrypt secret.txt
```

You’ll be prompted to enter a passphrase. The encrypted file will be saved as:

```bash
secret.txt.enc
```

---

### 🔓 Decrypt a File

```bash
./file_encryptor.sh decrypt secret.txt.enc
```

Once you provide the correct passphrase, it will restore the original file.

---

## 📄 Script Overview (`file_encryptor.sh`)

```bash
#!/bin/bash

ACTION=$1
FILE=$2

if [[ -z "$ACTION" || -z "$FILE" ]]; then
  echo "Usage: $0 [encrypt|decrypt] [filename]"
  exit 1
fi

if [[ "$ACTION" == "encrypt" ]]; then
  openssl aes-256-cbc -salt -in "$FILE" -out "$FILE.enc"
  echo "🔒 Encrypted: $FILE → $FILE.enc"

elif [[ "$ACTION" == "decrypt" ]]; then
  openssl aes-256-cbc -d -in "$FILE" -out "${FILE%.enc}"
  echo "🔓 Decrypted: $FILE → ${FILE%.enc}"

else
  echo "Invalid action: $ACTION"
  echo "Use 'encrypt' or 'decrypt'"
  exit 1
fi
```

---

## 🔒 Security Notice

Passwords and files are encrypted using `openssl` with AES-256, a robust and widely-trusted cipher.  
The script does **not** store or log any passphrases, and encryption keys are user-entered during runtime.  

> ⚠️ Make sure you remember your passphrase. Without it, decryption is impossible.

---

## 🧬 Tech Specs

- ✅ Pure Bash script — no dependencies beyond `openssl`
- ✅ Compatible with Linux and macOS
- ✅ AES-256-CBC encryption with salt
- ✅ Secure local processing — no data leaves your system
- ❌ No passphrase storage or logging

---

## 🚀 Future Enhancements

- [ ] Add logging of encrypted filenames to Cyborg Diary index
- [ ] Optional GPG key-based encryption
- [ ] Support batch encryption/decryption
- [ ] Self-destruct or auto-wipe mode after N failed attempts
- [ ] Terminal-based UI using `whiptail`

---

## 📓 Related Projects

- [`cyborg-diary-password-generator`](https://github.com/your-username/cyborg-diary-password-generator): Secure Bash password creation tool with logging
- Cyborg Diary Log Parser (coming soon)

---

## 🛡️ License

MIT License © 2025 [Your Name]  
_Encrypt what matters. Leave no trace._

---

> _"In a world of watchers, encryption is resistance."_ — The Cyborg

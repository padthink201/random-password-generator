# Word Password Generator + Vault

Memorable, strong passwords and a safe place to keep them, in one small app.

Most password generators give you something like `x7#Kq9!mZ2pL`. It's strong, but no human can remember it. This app builds passwords from real words instead:

```
Bullish.Dill!Skewer84
Acorn@Neuter#Riverside76
Detector_Reroute!Vividness77
```

They're easy to read, easy to type and easy to remember, and they still pass the password rules on almost every website: upper and lower case letters, a number and a symbol.

## Features

**Generator**
- Picks 2–5 random words from a list of 7,772 English words
- 2–4 digits at the end
- Random symbols between words, or the same symbol every time (`_ - . ! @ #`) for sites that only accept certain ones
- Capitalised words or mixed case
- Shows the password's length and how strong it is (in bits)

**Vault**
- Type an account name such as `google` and press Enter. The password is saved, copied and ready to paste.
- Save passwords you already have, too
- Search, copy, show or hide, and delete accounts
- Warns you before replacing an existing account's password
- Account names in any language, including Georgian

## Security

- **Encrypted.** Everything is protected by one master password, using Argon2id + XChaCha20-Poly1305 (Monocypher library). Without the master password the file is unreadable, and if anyone changes it, the app refuses to open it.
- **Secure randomness.** Passwords come from the operating system's secure random generator.
- **Clipboard protection.** Copied passwords are erased after 30 seconds and kept out of Windows clipboard history (Win+V) and cloud clipboard sync.
- **Auto-lock** after 5 minutes of inactivity.
- **Safe saving.** Every save keeps the previous version as a `.bak` backup, so a crash or power cut can't corrupt the vault.
- **Offline.** No internet connection, no account, no cloud. Your passwords never leave your computer.

## Important

- **The master password cannot be recovered.** If you forget it, the vault cannot be opened, by you or anyone else. Write it down and keep it somewhere safe.
- **Back up your vault.** It's stored at `%APPDATA%\WordPassVault\vault.wpv` on Windows and `~/.local/share/wordpass/vault.wpv` on Linux. Copy it to a USB stick from time to time. It's encrypted, so a lost stick doesn't expose your passwords.
- **Portable mode.** Put `vault.wpv` in the same folder as the `.exe` and the app uses that copy instead.
- This is a personal project. No independent security expert has audited it. For the most critical accounts (email, banking), an audited password manager such as Bitwarden is the safer choice.

## Platforms

| | |
|---|---|
| **Windows 10 / 11** | `WordPassword.exe`: a single file, no install needed |
| **Linux** | `wordpass`: terminal version, reads the same vault file |

Linux commands:
```
wordpass add google        generate and save a password
wordpass add bank --own    save a password you type yourself
wordpass get google        copy to clipboard
wordpass list              list accounts
wordpass rm google         delete an account
wordpass passwd            change the master password
wordpass gen               just generate, don't save
```

## First start on Windows

Windows may show **"Windows protected your PC"** because the app isn't code-signed. Click **More info → Run anyway**.

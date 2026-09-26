<img width="972" height="760" alt="Screenshot 2026-09-26 230704" src="https://github.com/user-attachments/assets/caaca8a9-7df7-4896-93ed-b2aaae7d0c7e" />
# WalletCracker

A standalone Windows GUI for recovering a forgotten **Bitcoin Core `wallet.dat`** password.

Single `.exe`. No Python. No dependencies. Just download, run, and point it at your wallet.

---

## What it does

Loads a Bitcoin Core `wallet.dat`, reads the encrypted master key, and tests candidate passwords against it using Bitcoin Core's real key-derivation function and AES-256 decryption. Supports wordlist attacks, custom brute-force, or single-password checks.

**For your own wallets only.** WalletCracker is a recovery tool for passwords you have lost access to on wallets you own.

---

## Features

- Single `.exe` — no Python, no pip, no dependencies for the user
- Runs on any Windows 10 / 11 machine (64-bit)
- Works fully offline — no network calls, no telemetry
- Reads Bitcoin Core `wallet.dat` (Berkeley DB Btree v9)
- Reads modern SQLite-format Core wallets (Bitcoin Core 25+)
- Auto-detects and tries both old (100,000-round) and new (250,000-round) KDF iteration counts
- Pure-Python Berkeley DB reader — no `bsddb3` or `berkeleydb` needed
- Wordlist attack — load any `.txt` password list, auto-counts entries
- Brute-force attack — custom charset, min/max length, optional prefix
- Single-password test — verify a remembered password instantly
- Live progress bar with percentage complete
- Live attempts-per-second rate, elapsed time, ETA, and tried count
- Stop button that cancels within a second
- Green "PASSWORD FOUND" banner with one-click copy to clipboard
- Scrollable log with timestamps and status messages
- Implements the actual Bitcoin Core KDF (SHA-512, salt ‖ password ‖ salt)
- AES-256-CBC verification — no false positives
- Read-only access to the wallet — never writes to it
- Native Tkinter GUI — small, fast, no Electron
- Pure Python source, GPLv2+, single auditable file
- BDB reader ported from BTCRecover (© 2014–2015 Christopher Gurnee)

---

## Limitations

- **CPU only.** Roughly 300–1,500 passwords per second on a modern CPU core. No GPU acceleration.
- **Bitcoin Core `wallet.dat` only.** Does not support Electrum, MetaMask, Exodus, Ledger, Trezor, or any other wallet format.
- **Unsigned binary.** Windows SmartScreen will warn on first launch. Click *More info* → *Run anyway*.

---

## Requirements

**To run the released exe:** nothing. Download and double-click.

## Download

Grab `WalletRecoverer.rar` from the Releases page.

On first launch Windows will show a SmartScreen warning ("Windows protected your PC"). Click **More info** → **Run anyway**. This appears because the exe is unsigned — it is not a virus warning, just Windows flagging an unknown publisher.

---

## Quick start

1. **Double-click `WalletCracker.exe`.**
2. Click **Open wallet .dat…** and pick your `wallet.dat` file.
3. Look at the info panel. It will show the salt, iteration count, and the KDF rounds that will be tried.
4. Choose a **password source** (wordlist, brute-force, or single password).
5. Click **Start cracking**.
6. Watch the progress bar. When the password is found, a green banner appears with a **Copy** button.

That's it. The rest of this document explains each step in more detail.



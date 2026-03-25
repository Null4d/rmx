# rmx

Crypto-shredding trash for Linux. Encrypts files on delete, destroys the key on empty.

SSD-aware: shreds a 32-byte key instead of gigabytes of data.

## Install

```
cp rmx ~/.local/bin/
```

## Usage

```
rmx <file ...>              # encrypt and trash
```

## How it works

- `rmx file.txt` encrypts with AES-256-CBC, stores key in `/dev/shm` (RAM)
- Reboot = keys gone = encrypted files are noise
- No `/dev/shm`? Falls back to plain `mv` (no encryption)

## Dependencies

- `openssl` - encryption
- `flock` - concurrent access locking
- `base64` - filename encoding in key storage
- `shred` - key destruction (optional, falls back to `rm`)

## License

MIT
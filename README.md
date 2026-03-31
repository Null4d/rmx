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
rmx recover <filename>      # decrypt and restore to CWD
rmx list                    # show recoverable files
rmx empty                   # destroy all keys + trash
```

## How it works

- `rmx file.txt` encrypts with AES-256-CBC, stores key in `/dev/shm` (RAM)
- Reboot = keys gone = encrypted files are noise
- `rmx empty` shreds the key file (32 bytes) then deletes trash
- No `/dev/shm`? Falls back to plain `mv` (no encryption)

## Dependencies

- `openssl` - encryption
- `flock` - concurrent access locking
- `base64` - filename encoding in key storage
- `shred` - key destruction (optional, falls back to `rm`)

## License

MIT
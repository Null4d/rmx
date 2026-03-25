# rmx

Simple trash utility for Linux. Moves files to trash instead of permanent deletion.

## Install

```
cp rmx ~/.local/bin/
```

## Usage

```
rmx <file ...>              # move to trash
```

## How it works

- Moves files to `~/.local/share/Trash`
- Handles filename collisions (file.txt → file.txt.1)

## Dependencies

- `flock` - concurrent access locking

## License

MIT
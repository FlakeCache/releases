# FlakeCache

High-performance Nix binary cache with FastCDC chunking.

## GitHub Action

```yaml
- uses: FlakeCache/releases@v1
```

### With Options

```yaml
- uses: FlakeCache/releases@v1
  with:
    flakecache: 'true'      # Enable FlakeCache binary cache (default: true)
    install-cli: 'true'     # Install FlakeCache CLI
```

### Full Example

```yaml
jobs:
  build:
    runs-on: ubuntu-latest
    container: nixos/nix:latest
    steps:
      - uses: actions/checkout@v4
      - uses: FlakeCache/releases@v1
      - run: nix build

      # Optional: push to cache
      - uses: FlakeCache/releases@v1
        with:
          install-cli: 'true'
      - run: flakecache push ./result
        env:
          FLAKECACHE_TOKEN: ${{ secrets.FLAKECACHE_TOKEN }}
```

## CLI Installation

### Quick Install

```bash
curl -fsSL https://flakecache.com/install.sh | sh
```

### Manual Download

See [Releases](https://github.com/FlakeCache/releases/releases) for binaries.

## Links

- [Website](https://flakecache.com)
- [Documentation](https://docs.flakecache.com)

## License

Apache-2.0

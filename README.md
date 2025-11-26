# FlakeCache

High-performance Nix binary cache with integrated flake registry.

## GitHub Action

Install Nix with FlakeCache binary cache enabled.

### Basic Usage

```yaml
- uses: FlakeCache/releases@v1
```

### With Options

```yaml
- uses: FlakeCache/releases@v1
  with:
    flakecache: 'true'           # Enable FlakeCache binary cache (default: true)
    install-cli: 'true'          # Install FlakeCache CLI (default: false)
    cli-version: 'latest'        # CLI version (default: latest)
    extra-substituters: ''       # Additional binary cache URLs
    extra-trusted-keys: ''       # Additional trusted public keys
    extra-conf: ''               # Extra nix.conf lines
```

### Examples

#### Basic Nix Build

```yaml
jobs:
  build:
    runs-on: ubuntu-latest
    steps:
      - uses: actions/checkout@v4
      - uses: FlakeCache/releases@v1
      - run: nix build
```

#### With Container

```yaml
jobs:
  build:
    runs-on: ubuntu-latest
    container: nixos/nix:latest
    steps:
      - uses: actions/checkout@v4
      - uses: FlakeCache/releases@v1  # Detects Nix already installed
      - run: nix build
```

#### Push to Cache

```yaml
jobs:
  build:
    runs-on: ubuntu-latest
    steps:
      - uses: actions/checkout@v4
      - uses: FlakeCache/releases@v1
        with:
          install-cli: 'true'
      - run: nix build
      - run: flakecache push ./result
        env:
          FLAKECACHE_TOKEN: ${{ secrets.FLAKECACHE_TOKEN }}
```

## CLI Installation

### Quick Install

```bash
curl -fsSL https://raw.githubusercontent.com/FlakeCache/cli/main/install.sh | sh
```

### Manual Download

Download binaries from [Releases](https://github.com/FlakeCache/releases/releases):

- `flakecache-linux-x86_64` - Linux x86_64
- `flakecache-linux-aarch64` - Linux ARM64
- `flakecache-macos-x86_64` - macOS Intel
- `flakecache-macos-aarch64` - macOS Apple Silicon

```bash
# Example: Install on Linux x86_64
VERSION=v1.0.0  # Check releases for latest version
curl -L -o flakecache https://github.com/FlakeCache/releases/releases/download/cli-${VERSION}/flakecache-linux-x86_64
chmod +x flakecache
sudo mv flakecache /usr/local/bin/
```

## CLI Usage

```bash
# Push build results to cache
flakecache push ./result

# Pull from cache
flakecache pull nixpkgs#hello

# List cache contents
flakecache list

# Show cache info
flakecache info
```

## Features

- **FastCDC Chunking** - Efficient content-defined chunking
- **GitHub Actions Integration** - Native action support
- **Container Detection** - Auto-detects Nix in containers
- **Multi-platform** - Linux (x86_64, ARM64), macOS (Intel, Apple Silicon)
- **Zero Config** - Works out of the box

## Links

- [Website](https://flakecache.com)
- [Documentation](https://docs.flakecache.com)
- [CLI Repository](https://github.com/FlakeCache/cli)
- [Action Repository](https://github.com/FlakeCache/nix-installer)

## License

Apache-2.0

# FlakeCache Releases

Binary releases for FlakeCache CLI and related artifacts.

## GitHub Action

Install Nix with FlakeCache binary cache enabled. Use the dedicated action repo:

```yaml
- uses: FlakeCache/nix-installer@v1
```

Documentation and options: [FlakeCache/nix-installer](https://github.com/FlakeCache/nix-installer).

> **Note:** `FlakeCache/releases@v1` previously pointed at the same installer action.
> New workflows should use `FlakeCache/nix-installer@v1`.

## CLI Installation

### Quick Install

```bash
curl -fsSL https://raw.githubusercontent.com/FlakeCache/cli/main/install.sh | sh
```

### Manual Download

Download binaries from [GitHub Releases](https://github.com/FlakeCache/releases/releases):

- `flakecache-linux-x86_64` — Linux x86_64
- `flakecache-linux-aarch64` — Linux ARM64
- `flakecache-macos-x86_64` — macOS Intel
- `flakecache-macos-aarch64` — macOS Apple Silicon

```bash
VERSION=v1.0.0  # check releases for latest
curl -L -o flakecache "https://github.com/FlakeCache/releases/releases/download/${VERSION}/flakecache-linux-x86_64"
chmod +x flakecache
sudo mv flakecache /usr/local/bin/
```

## CLI Usage

```bash
flakecache push ./result
flakecache pull nixpkgs#hello
flakecache list
flakecache info
```

## Links

- [Website](https://flakecache.com)
- [Documentation](https://docs.flakecache.com)
- [CLI Repository](https://github.com/FlakeCache/cli)
- [Nix Installer Action](https://github.com/FlakeCache/nix-installer)

## License

Apache-2.0

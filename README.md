# FlakeCache Releases

Binary releases for the **FlakeCache CLI** (not the Nix installer action).

## Nix installer action

Use the dedicated action repo only:

| Host | `uses:` |
|------|---------|
| Forgejo (fleet) | `flakecache/nix-installer@v1` |
| GitHub (mirror) | `FlakeCache/nix-installer@v1` |

Docs: [flakecache/nix-installer](https://git.infra.centralcloud.com/flakecache/nix-installer) · [GitHub mirror](https://github.com/FlakeCache/nix-installer)

> **`FlakeCache/releases@v1` is retired.** This repo no longer ships `action.yml`. Workflows that still reference `releases@v1` must switch to `nix-installer@v1`.

## CLI installation

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

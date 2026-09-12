# talos-releases

Public release archive for [Talos](https://talos.love).

This repository stores Talos release artifacts and release automation only. It does not contain application source code and is not used for product issue discussion.

- Product site and downloads: https://talos.love
- Source repository: https://github.com/apilots/talos
- Issues and discussion: use the main Talos repository.

The `Build release` workflow accepts automatic and manual dispatch through the same
mandatory gate: validate tagged source and Notes, run Talos-owned source checks,
build products, run native TUI installation checks against those products, then
publish artifacts and stable image tags. Gate failures block publication.

The canonical [release policy](https://github.com/apilots/talos/blob/main/docs/development/RELEASE.md)
owns branch/version timing, bug-fix-only stabilization, verification, and merge-back
rules. This repository reuses the tagged source scripts; it does not maintain a
second check implementation or a gate-bypass option.

The matching Release in `apilots/talos` owns the canonical Release Notes. This repository reads that body by tag and publishes it unchanged. A missing or empty source Release fails the workflow; release-note generation is not duplicated here.

Current release scope:

- `Talos-Desktop-<version>-macos-arm64.dmg`
- `Talos-Desktop-<version>-linux-amd64.AppImage`
- `Talos-Server-<version>-linux-amd64.tar.gz`
- `Talos-Server-<version>-linux-arm64.tar.gz`
- `Talos-TUI-<version>-linux-amd64.tar.gz`
- `Talos-TUI-<version>-linux-arm64.tar.gz`
- `Talos-TUI-<version>-macos-amd64.tar.gz`
- `Talos-TUI-<version>-macos-arm64.tar.gz`
- `install.sh`
- `checksums.txt`
- `manifest.json`
- `ghcr.io/apilots/talos-server:<version>` multi-architecture server image for `linux/amd64` and `linux/arm64`

Package entry points:

- TUI tarballs expose `bin/talos` and include the version-matched config template and database migrations under `conf/`.
- Server tarballs expose `bin/talos-server` and include the WebUI bundle.
- Server container images run `talos-server` with the production config and persist data in the default `/home/talos/.talos` home directory.
- `libexec/app-server` is a private runtime file and is not uploaded as a standalone release asset.

R2 upload support is included but optional. It runs only when the R2 secrets are configured in this repository.
Published release tags and their versioned R2 prefixes are immutable. Rebuilding changed artifacts
requires a new version tag; the workflow fails instead of replacing assets for an existing tag.

Install the latest TUI bundle with:

```bash
curl --proto '=https' --tlsv1.2 -fsSL \
  https://github.com/apilots/talos-releases/releases/latest/download/install.sh | sh
```

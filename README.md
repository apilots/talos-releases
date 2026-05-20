# talos-releases

Public release archive for [Talos](https://talos.love).

This repository stores Talos release artifacts and release automation only. It does not contain application source code and is not used for product issue discussion.

- Product site and downloads: https://talos.love
- Source repository: https://github.com/apilots/talos
- Issues and discussion: use the main Talos repository.

The `Build release` workflow is invoked by the main Talos repository through `repository_dispatch` whenever a `v*` tag is pushed. The workflow checks out the tagged Talos source, builds release artifacts through `build.sh`, uploads GitHub Actions artifacts, and creates a GitHub Release in this repository.

Current release scope:

- macOS Desktop DMG
- Linux Desktop portable package
- Linux server + WebUI package
- Linux TUI package

R2 upload support is included but optional. It runs only when the R2 secrets are configured in this repository.

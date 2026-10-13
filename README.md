# talos-releases

Public historical release archive for [Talos](https://talos.love). New releases,
including the Server and Worker images, are published from
[`apilots/talos`](https://github.com/apilots/talos). This repository no longer runs
release automation.

Existing tags, GitHub releases, assets, and R2 version prefixes remain unchanged.
The Talos installer checks current Talos releases first and falls back to this
archive for older versions that have not moved. Existing download URLs continue to
work. The source repository owns the current release policy, checks, build matrix,
canonical notes, checksums, manifest, optional R2 mirroring, and multi-architecture
container publishing.

Historical assets in this repository include Desktop, Server WebUI, and TUI bundles,
`install.sh`, `checksums.txt`, `manifest.json`, and the previously published Server
container image. New Server and Worker images are published by Talos.

- Product site and downloads: https://talos.love
- Source and issue tracking: https://github.com/apilots/talos

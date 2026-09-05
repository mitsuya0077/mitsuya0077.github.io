# Legacy URL redirects — not the official website source

This repository exists only to preserve URLs used by already-distributed
VR Vlog app binaries after the official website repository is renamed.

- Official website source: [vr-vlog-website](https://github.com/mitsuya0077/vr-vlog-website).
- Old entry point: `https://mitsuya0077.github.io/vr-vlog/`.
- Destination: `https://mitsuya0077.github.io/vr-vlog-website/`.
- The legacy page preserves query strings and fragments (including `#privacy`)
  through a fixed-destination JavaScript redirect. Without JavaScript it uses
  an HTML refresh and a visible privacy-policy link. With no fragment, privacy
  is the default destination for shipped clients.

## Hosting

Use GitHub Pages: **Deploy from a branch**, `main`, `/ (root)`.
The `.nojekyll` file selects static files without a Jekyll transformation.
Deploy this repository before renaming the existing `vr-vlog` project site.
While that project still exists, it owns the old project URL; after renaming,
the user-site `vr-vlog/index.html` supplies the compatibility endpoint.
Verify both the old URL (with `#privacy`) and the new site after the rename.

This contains no application or exporter source and no private credentials.
Do not delete the legacy endpoint while distributed clients still reference it.

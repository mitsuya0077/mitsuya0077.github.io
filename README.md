# Legacy URL compatibility — not the official source

This repository preserves URLs used by already-distributed VR Vlog app
binaries and existing Exporter VPM repository registrations.

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

## Exporter VPM compatibility

- Official introduction: `https://vrvlog.fun/exporter/`.
- New registrations: `https://vrvlog.fun/exporter/index.json`.
- Canonical publication: `https://vr-vlog.github.io/VR-Vlog-lilToon-Exporter/index.json`.
- Existing personal registrations: `https://mitsuya0077.github.io/VR-Vlog-lilToon-Exporter/index.json`.
- Legacy introduction: `https://mitsuya0077.github.io/VR-Vlog-lilToon-Exporter/`.

The legacy listing is real JSON served with HTTP 200, not an HTML redirect.
It retains repository ID `com.vrvlog.packages`, every published package version,
dependency and ZIP checksum. Only the listing's root `url` differs from the
other endpoints. Existing VCC/ALCOM registrations stay unchanged. Browser
visits to the introduction page move to the official domain.

The Exporter repository's approved `Build VPM Listing` publication validates
and publishes the canonical JSON, then synchronizes the official site and this
legacy JSON with `Tools/sync-vpm-mirrors.py`. It creates ordinary commits on
`main` with an expected-head guard and waits for the existing branch-based
Pages deployment. It changes only `VR-Vlog-lilToon-Exporter/index.json` here.
No workflow or schedule is added to this repository. A dedicated credential
is restricted to this repository and `mitsuya0077/vr-vlog-website`.

The publication completes only after all three public JSON endpoints return
HTTP 200 and the current publication data, except their own root `url`.
A failed or partially applied update is reported by the publication job;
retry the approved publication without force-pushing or changing published
ZIPs. Immutable history and checksums prevent an older snapshot from removing
already published versions. Keep both legacy paths while clients use them.

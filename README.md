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

- Canonical listing: `https://vr-vlog.github.io/VR-Vlog-lilToon-Exporter/index.json`.
- Legacy listing: `https://mitsuya0077.github.io/VR-Vlog-lilToon-Exporter/index.json`.
- Legacy introduction page: `https://mitsuya0077.github.io/VR-Vlog-lilToon-Exporter/`.

The legacy listing is real JSON served with HTTP 200, not an HTML redirect.
It retains repository ID `com.vrvlog.packages`, all package versions and ZIP
checksums. Only the listing's root `url` differs from the canonical JSON.
Existing VCC/ALCOM registrations can keep using their original URL.

After each approved canonical VPM publication, run this local command from
an existing [Exporter checkout](https://github.com/VR-Vlog/VR-Vlog-lilToon-Exporter):

```sh
python3 Tools/sync-legacy-listing.py --site-root /path/to/mitsuya0077.github.io
```

Review the changed JSON, merge its PR, and wait for this repository's existing
branch-based Pages deployment. Read back both public JSON endpoints and verify
that they match except for the root `url`. Do not report legacy updates complete
until the old endpoint is current. This adds no workflow, scheduled job, token,
or automatic synchronization; maintaining the mirror is a publication step.
Keep both legacy paths while clients still reference them.

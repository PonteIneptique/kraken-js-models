# CLLG Kraken models

The built-in models of [CLLG Desktop](https://github.com/cllg-project/cllg-scanner), in
the [kraken-js](https://github.com/cllg-project/kraken-js) `.js_mlmodel` format (ONNX graph
+ metadata). They are stored with Git LFS and published as release assets; CLLG Desktop
downloads them on first run instead of bundling them in the application.

| File | Role |
|---|---|
| `segmentation.js_mlmodel` | Kraken line segmentation |
| `ppocr_v6_tau090.js_mlmodel` | Kraken text recognition (Ancient Greek) |
| `dfine_cllg.js_mlmodel` | D-FINE layout zones for Greek scholarly editions (CLLG) |
| `dfine_ladas.js_mlmodel` | D-FINE layout zones for Latin and general documents (LADaS) |

`SHA256SUMS` holds the checksum of every model; CLLG Desktop's `resources/models.json`
lists the same checksums and only keeps a download that matches.

## Cloning

Git LFS is required (`git lfs install` once), otherwise `models/` only holds pointer files.

## Publishing a new version

1. Replace or add the files in `models/`, then regenerate the checksums:
   `(cd models && sha256sum *.js_mlmodel > ../SHA256SUMS)`
2. Commit, tag (`git tag v1.1.0`) and push the tag: the release workflow checks the files
   against `SHA256SUMS` and publishes them as a GitHub release.
3. In CLLG Desktop, update `resources/models.json` (the models tag, and each file's size
   and sha256).

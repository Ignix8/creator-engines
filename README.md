# creator-engines

Pinned builds of open-source local AI engines for **Ignix Creator**, made where
the upstream project publishes no binary Creator can use.

Each build is produced by the workflow in this repository from **one pinned
upstream commit**, with no source changes. Every release includes:

- the upstream licences;
- a `THIRD_PARTY_NOTICES.txt` file;
- SHA-256 sums;
- a GitHub build provenance attestation.

Ignix Creator downloads these files only from the release, and only when the
exact archive SHA-256 and the per-file SHA-256 values compiled into Creator
match.

## stable-diffusion.cpp (`sd-cli`, macOS)

| | |
| --- | --- |
| Upstream | https://github.com/leejet/stable-diffusion.cpp (MIT) |
| Why built here | Upstream has no macOS x86-64 build. Its Apple Silicon build is unsigned and requires macOS 26. |
| arm64 | Metal backend, shaders embedded, macOS 13.3+, ad-hoc signed |
| x86-64 | CPU (AVX2/FMA/F16C), macOS 13.3+, ad-hoc signed |
| Options | `GGML_NATIVE=OFF`, WebP/WebM I/O off, static (only system libraries) |

To build a release, run the **Build stable-diffusion.cpp (macOS)** workflow with
the upstream tag and commit. To verify an archive, run:

```bash
gh attestation verify <archive>.tar.gz --repo Ignix8/creator-engines
```

The workflow files in this repository are MIT-licensed (see `LICENSE`).

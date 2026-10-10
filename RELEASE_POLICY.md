# Release Publication Rules

Current channel status: **NOT ACTIVE**.

1. Publish only approved Horizon Portal developer builds. The Boundary core OS and Linux security updates use a different, future pipeline.
2. Confirm provenance, third-party licenses, privacy disclosures and permitted public redistribution. The preview ZIP includes Python files, and a public artifact is readable even when the source repository is private.
3. Sign reviewed manifest bytes using an Ed25519 **publisher private key stored outside GitHub** (prefer isolated trusted signing host). Publish only the **public** verification key after its fingerprint is independently established.
4. Do not turn on user updater feeds before testing signature validation, expired/replayed builds, wrong hash, tampering, safe backup, failed installation and recovery.
5. Keep release sequence strictly increasing. Do not repurpose an old version number for different bytes. Do not manually edit signed manifest JSON after signature generation.
6. Keep application updates user-approved, back up earlier files and retain a no-update fallback. No silent restarts or forced system changes.
7. Maintain an auditable change log that distinguishes build source testing from VM runtime verification and from mandatory security-audit acceptance.
8. No release may claim that sandboxing, malware detection, privacy enforcement or kernel integrity is provided unless the separate controls and G01–G12 release gates have been independently verified.
9. Treat the release signing private key as highly sensitive. Never send it through chat, commit it, or keep it inside a VM used for untrusted OS development.

## Pages release layout

After the owner enables GitHub Pages **Deploy from a branch → main / (root)**, project-site downloads will be served from the HTTPS `spiffyrunner.github.io/BoundaryOS-Releases/` prefix.

The Update Center is configured only after the public HTTPS feed exists **and** the trusted public key is pinned out of band. GitHub Releases attachments normally redirect to a different asset origin, while the Boundary Update Center intentionally refuses redirects; use the Pages host for this channel.

## First public release acceptance checklist

- [ ] Trusted signing key generated on an appropriate device and backed up offline.
- [ ] Public key fingerprint independently verified.
- [ ] GitHub Pages enabled and public `index.html` accessible.
- [ ] Publisher verifies all package contents and distribution rights.
- [ ] Manifest, detached signature and package pass independent cryptographic preflight.
- [ ] Hyper-V test guest accepts authentic release, rejects tampered/expired/replayed release, maintains user consent and recovers after failure.
- [ ] 2 GiB memory impact checked.
- [ ] Public beta/security release gates reviewed separately.

# Boundary OS — Official Release Distribution (Preview)

**Public downloads only. Source development remains private.**

This repository is the distribution channel for **cryptographically signed Boundary OS preview release artifacts**. It intentionally contains no publisher private keys, GitHub credentials, unpublished development files, or user telemetry.

## Current status

**NOT YET ACTIVE — NO SIGNED RELEASES PUBLISHED.**

Do not install anything from a pull request, branch archive, random fork, or file not referenced by a verified release manifest. The Update Center must remain **disabled** until the official publisher signing public-key fingerprint is independently verified.

The first supported channel will deliver **Boundary Horizon Portal user-level preview updates only**, not kernel, firmware, Debian packages, a full ISO, or core security controls.

## Planned channel

The desktop Update Center will eventually retrieve a signed manifest and a small `horizon-portal-<build>.zip` package through GitHub Pages on HTTPS. GitHub Pages must be separately enabled by the repository owner.

**No update URLs currently represent a usable trusted channel.**

## Privacy and ownership

- Main development source repository: private; its permissions are not changed here.
- This public repository: signed, reviewed, explicit-release files only.
- Python source files contained inside future Horizon preview packages may be viewable by anyone who downloads a release, so each package must be approved for public distribution before publishing.
- No automatic installation, no background telemetry, no user-account collection.
- End users approve each installation.
- Public artifacts are **not proof** of production readiness or independent security certification.

See [SECURITY.md](SECURITY.md) for verification, threat model and vulnerability reporting guidance.

## Release acceptance gate

A release can only be published after independent source review, approved publisher key provisioning, signature verification, restore testing, and confirmation that the security warnings remain accurate. No package should be published just to test whether a private repository can be read.

License and redistribution rights for distributed code must be settled before first public artifact. This repository's public visibility does not itself grant a software license.

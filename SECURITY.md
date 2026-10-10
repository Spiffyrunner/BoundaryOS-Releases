# Boundary OS Release Distribution Security Policy

## Release trust model

The Boundary Update Center trusts **only** releases whose manifests verify against a publisher Ed25519 public key that the user has independently pinned. HTTPS protects transport; a file's SHA-256 hash alone is not proof of publisher identity.

**Current status: no signing key or signed public feed has been provisioned.** Do not interpret this repository, GitHub's public badge, or the desktop icon as evidence of a secure active update channel.

### Never publish here
- Private Ed25519 signing keys, passwords, access tokens, private repository clones, unreviewed source or database exports.
- Unsigned update manifests, executable scripts presented as automatic updates, emergency security patches without independent verification.
- User/host identifiers, telemetry logs, crash dumps, proprietary third-party artifacts without distribution rights.

### Approved artifact shape (once release signing is ready)
- `horizon-standard.json` — short-lived canonical release manifest (Ed25519 signed).
- `horizon-standard.json.sig` — detached **64-byte raw Ed25519** signature over the exact bytes of the JSON file.
- `horizon-portal-N.zip` — allowlisted **user-level** preview package with filename tied to strictly increasing build N.

The updater validates a pinned public key, manifest signature and expiration, edition and component, package size/hash, exact archive member allowlist and user approval. The published download origin must be the configured HTTPS Pages endpoint; redirects and cross-origin artifacts are intentionally refused.

### Limitations and response
This preview updater cannot defend against malware already running as the user's account, a compromised publisher signing key, arbitrary kernel modifications, or a compromised physical host. It does **not** update the Linux kernel, Debian packages, firmware, or privileged privacy enforcement.

For suspected malicious update content: **disable the updater**, remove the signed feed configuration, preserve evidence, and use an existing Hyper-V checkpoint or independently trusted backup. Key revocation and a complete incident response workflow are mandatory before public beta. Do not publish a new private key in this repository.

## Vulnerability reporting

Before a dedicated private security contact is established, avoid posting exploit proofs, secrets, or personal data in public issues. Use the development project's owner-administered private contact channel for sensitive disclosures. Public issues may discuss non-sensitive, reproducible usability problems without harmful code.

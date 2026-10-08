# Ocean Protocol — Security Advisory Archive

This is the **project-wide archive** of security advisories for the Ocean Protocol
stack, covering every repository under
[github.com/oceanprotocol](https://github.com/oceanprotocol).

Our security and disclosure process is described in our
[Security Policy](./SECURITY.md). Report vulnerabilities to
**security@oceanprotocol.com** or via a repository's private
**Security → Advisories** tab.

## How we publish

- Each advisory is published as a **GitHub Security Advisory (GHSA)** — either on
  the affected repository's Security tab, or (for cross-cutting issues) on this
  `oceanprotocol/.github` repository at
  [`/security/advisories`](https://github.com/oceanprotocol/.github/security/advisories).
- We request a **CVE** where applicable.
- Every published advisory is indexed in the table below so there is **one place**
  to see all Ocean Protocol advisories, regardless of which repo they affect.

## Advisories

| ID | Date | Affected | Severity | Summary | Link |
|---|---|---|---|---|---|
| OCEAN-2026-001 | 2026-09 | `ocean-node` (C2D compute engine / `pushConfig`) | Critical | A compute environment pushed via the admin `pushConfig` command could specify arbitrary Docker bind mounts and Linux capabilities with no safety denylist. Combined with the free-compute image-build path, this allowed an authorized-but-malicious admin to mount the host filesystem into a job and read node secrets (including the signing key). Fixed by denylisting dangerous binds/capabilities in `pushConfig` and at container creation, and hardening free-compute. | _GHSA link — to be added on publication_ |

<!--
Template for new rows (copy, fill, and keep newest at the top):

| OCEAN-YYYY-NNN | YYYY-MM | `<repo>` (<component>) | Critical/High/Medium/Low | <one-line impact + what the fix does> | <GHSA/CVE URL> |

Fields to confirm before publishing an advisory:
- Final CVSS v3.1 severity + vector
- Affected and fixed version(s) / commit(s)
- GHSA identifier (and CVE, if requested)
- Reporter credit (or "anonymous")
-->

---

*For the full policy, scope, response targets, and safe-harbor terms, see
[SECURITY.md](./SECURITY.md).*

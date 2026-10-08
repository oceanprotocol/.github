# Security Policy

Ocean Protocol builds open-source software for publishing, exchanging, and running
compute on data — including smart contracts that custody on-chain value and nodes
that run untrusted compute workloads. We take the security of this stack seriously
and welcome coordinated disclosure of vulnerabilities from the community.

This policy explains **what is in scope**, **how to report**, **what you can
expect from us**, and **how we publish fixes**.

---

## Reporting a vulnerability

Please report security issues through **either** channel:

- **Email:** **security@oceanprotocol.com**. If you would like to encrypt
  sensitive exploit details, contact us at that address and we will arrange a
  secure channel.
- **GitHub private vulnerability reporting:** open a private report from the
  **Security → Advisories** tab of the affected repository
  (`https://github.com/oceanprotocol/<repo>/security/advisories/new`). This keeps
  the report private to maintainers until a fix is published.

**Please do _not_** open a public GitHub issue, pull request, or forum/Discord post
for a security vulnerability, and do not disclose it publicly before we have had a
chance to remediate (see *Coordinated disclosure* below).

### What to include

A good report lets us reproduce and triage quickly. Where possible, include:

- The affected repository, component, version/commit, and deployment (e.g. a node
  configuration, a specific chain/contract address, a testnet vs mainnet).
- A clear description of the vulnerability and its security impact.
- Step-by-step reproduction, proof-of-concept code, and any logs or transactions.
- An assessment of severity and the conditions required to exploit it.

If you are unsure whether something is in scope, report it anyway and let us
triage.

---

## Scope

### In scope

The software we maintain under **https://github.com/oceanprotocol**, including but
not limited to:

| Area | Repositories |
|---|---|
| Smart contracts | `contracts` (datatokens, data-NFTs, fixed-rate exchange, dispenser, `Escrow` / `EnterpriseEscrow`) |
| Node / backend | `ocean-node`, `ocean-node-bootstrap` |
| Client libraries & tooling | `ocean.js`, `ocean-cli`, `ddo.js`, `on-mcp` |
| Supporting services | incentive / monitoring backends and related repositories under the org |

Vulnerability classes we are particularly interested in:

- **Smart contracts:** loss or lock-up of funds, access-control and
  authorization flaws, reentrancy, economic/accounting errors, and escrow or
  payment-settlement bugs. On-chain value is at stake — these are our highest
  priority.
- **Nodes / Compute-to-Data:** container escapes and sandbox bypasses, unsafe
  Docker configuration (bind mounts, capabilities, privilege escalation),
  key/secret exposure, authentication and admin-command bypasses, SSRF, and
  remote code execution.
- **Client libraries / CLI:** key-handling and signing flaws, encryption
  weaknesses, request-forgery and replay issues.
- **Supply chain:** malicious or compromised dependencies affecting our build or
  release artifacts.

### Out of scope

- Deployments, configurations, and infrastructure operated by **third-party node
  operators** (we can help coordinate, but we do not control their systems).
- Findings that require physical access, social engineering of Ocean staff, or a
  compromised end-user device.
- Volumetric denial-of-service / stress testing against shared or production
  infrastructure.
- Automated-scanner output with no demonstrated, exploitable impact; missing
  "best-practice" HTTP headers; and theoretical issues without a realistic attack
  path.
- Vulnerabilities in third-party dependencies that are already public and not
  specifically exploitable through our code (report these upstream).

> **Note on rewards:** this is a coordinated-disclosure policy, not a paid bug
> bounty. Some repositories (currently including `ocean-node`) are explicitly
> **excluded from any bug-bounty rewards** — but vulnerability reports for them
> are still welcome and handled under this policy. Where a separate bounty program
> applies, its terms are published with that program.

---

## Our commitments and response targets

When you report in good faith under this policy, we aim — **to the extent
possible** — to:

- **Acknowledge** your report, usually within about **3 business days**.
- Provide an **initial assessment** (validity + preliminary severity), usually
  within about **10 business days**.
- Keep you **informed** of progress through remediation, and credit you in the
  published advisory if you wish (or keep you anonymous if you prefer).

We triage severity using **CVSS v3.1**. Our remediation timelines are
best-effort targets rather than guarantees — typically, from the point a report
is validated:

| Severity | Target time to fix (typical) |
|---|---|
| Critical | around **30 days** (with interim mitigations as soon as possible) |
| High | around **60 days** |
| Medium | around **90 days** |
| Low / informational | best effort, usually with the next regular release |

For issues affecting deployed smart contracts or live funds, we may act faster
than these targets and coordinate mitigations (e.g. pausing, migration) out of
band before any public detail is shared.

These are typical targets, not guarantees; complex fixes or those requiring
on-chain migration may take longer, and we will keep you updated if so.

---

## Coordinated disclosure

- We follow **coordinated disclosure**. We ask that you give us a reasonable
  opportunity to remediate before any public disclosure — **90 days** from your
  report by default, or until a fix is released, whichever comes first.
- We are happy to agree on a **mutually acceptable disclosure date**, and to
  coordinate timing with you so that you receive appropriate credit.
- Once a fix is available, we publish an advisory (see below). If an issue is
  being actively exploited, we may accelerate disclosure together with a fix or
  mitigation.

### Safe harbor

We will **not pursue or support legal action** against researchers who, in good
faith:

- make a reasonable effort to comply with this policy,
- only interact with systems and accounts they own or are explicitly authorized
  to test (never third-party operators' deployments or other users' data),
- avoid privacy violations, data destruction, and service degradation, and
- give us reasonable time to respond before any disclosure.

If in doubt about whether an action is authorized, ask us first at
security@oceanprotocol.com.

---

## Advisory archive

We maintain a single, **project-wide advisory archive** covering every Ocean
Protocol repository:

**https://github.com/oceanprotocol/.github/blob/main/SECURITY-ADVISORIES.md**

Individual advisories are published as **GitHub Security Advisories (GHSA)** — on
the affected repository's Security tab, or on the
[`oceanprotocol/.github`](https://github.com/oceanprotocol/.github/security/advisories)
repository for cross-cutting issues — and we request CVE identifiers where
applicable. Every published advisory is indexed in the archive above, so there is
one place to see all Ocean Protocol advisories regardless of which repository they
affect. Each entry records the affected versions, impact, severity, the fixed
version(s), and credit to the reporter.

---

*Thank you for helping keep Ocean Protocol and its users safe.*

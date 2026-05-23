*Security Digest — 2026-05-23* (Claude managed agents)
Verdict: 1 actively exploited, 5 to schedule this week, 3 to monitor. _Sources: KEV, GH Advisory, EPSS_

*PATCH TODAY*
- [CVE-2025-34291](https://github.com/advisories/GHSA-577h-p2hh-v4mv) — langflow (pip) · KEV added 2026-05-21 · EPSS 0.34 · CVSS 8.8
  CORS misconfiguration + SameSite=None refresh cookie → attackers make cross-origin requests with credentials, pivot to RCE via obtained tokens. Exploited per CISA (due 2026-06-04).
  → upgrade langflow above 1.6.9 or apply vendor mitigations immediately; do not expose Langflow admin to the internet.

*PATCH THIS WEEK*
- [GHSA-g6ww-w5j2-r7x3](https://github.com/advisories/GHSA-g6ww-w5j2-r7x3) — boxlite (npm/pip/go/rust) · CVSS 10.0 · EPSS n/a · no public PoC
  Permission bypass lets any caller overwrite files flagged read-only. → upgrade boxlite / @boxlite-ai/boxlite to ≥0.9.0 across all SDK languages.

- [GHSA-f396-4rp4-7v2j](https://github.com/advisories/GHSA-f396-4rp4-7v2j) — boxlite (npm/pip/go/rust) · CVSS 9.6 · EPSS n/a
  Path traversal in the same package allows arbitrary file write on the host. → same fix: upgrade to ≥0.9.0.

- [GHSA-cr22-wjx7-2w6m](https://github.com/advisories/GHSA-cr22-wjx7-2w6m) — mcp-server-kubernetes (npm) · CVSS 8.8 · EPSS n/a
  Tool access controls enforced only in the presentation layer; execution layer ignores them. Any caller can invoke restricted Kubernetes tools. → upgrade mcp-server-kubernetes to ≥3.6.0.

- [GHSA-vrxg-gm77-7q5g](https://github.com/advisories/GHSA-vrxg-gm77-7q5g) — windows-mcp (pip) · CVSS n/a · EPSS n/a
  HTTP transport accepts unauthenticated requests with wildcard CORS; gives callers full PowerShell control. → upgrade windows-mcp to ≥0.7.5 or firewall MCP port immediately.

- [GHSA-q2f7-m237-v562](https://github.com/advisories/GHSA-q2f7-m237-v562) — @hulumi/policies (npm) · CVSS n/a · EPSS n/a
  GitHub OIDC trust policy bypass via AWS set-qualified condition operators; a forked or sibling repo can assume your production role. → upgrade @hulumi/policies to ≥1.3.2 and audit OIDC trust conditions.

*MONITOR*
- [GHSA-j3vx-cx2r-pvg8](https://github.com/advisories/GHSA-j3vx-cx2r-pvg8) — network-ai (npm) · CVSS 7.6 · no patch yet
  Empty default MCP secret allows any cross-origin request to invoke tools without authentication. → track for patch; avoid exposing network-ai MCP server to untrusted origins.

- [GHSA-m549-qq94-fvhg](https://github.com/advisories/GHSA-m549-qq94-fvhg) — lmdeploy (pip) · CVSS 7.8 · patch: ≥0.13.0
  Hardcoded trust_remote_code=True loads arbitrary remote code during model init with no user opt-out. → schedule upgrade to lmdeploy ≥0.13.0.

- [GHSA-7hh5-prp2-mfh5](https://github.com/advisories/GHSA-7hh5-prp2-mfh5) — sagemaker (pip) · CVSS 7.2 · EPSS 0.00055 · no fix yet
  HMAC signing key stored in cleartext in ModelBuilder/Serve path; key recovery possible from disk. → watch for patched release; avoid logging or persisting ModelBuilder artifacts.

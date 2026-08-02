# Aryaka

Aryaka Networks, Inc. delivers **Unified SASE as a Service** — a converged, fully managed
networking and security platform combining a private global core network, fully managed
SD-WAN, WAN/application acceleration, multi-cloud on-ramps, and a single-pass security
stack (NGFW, SWG, CASB, DNS filtering, anti-malware, IPS, Universal ZTNA), operated
through the **MyAryaka** portal.

- Website — https://www.aryaka.com/
- Documentation — https://docs.aryaka.com/
- MyAryaka portal — https://my.aryaka.com/
- Secondary-market listing — https://forgeglobal.com/aryaka_stock/

## API surface

**Aryaka publishes no public developer portal and no machine-readable API contract.**
Contract discovery was run on 2026-08-02 against every Aryaka host (`www.aryaka.com`,
`aryaka.com`, `docs.aryaka.com`, `my.aryaka.com`, `api.aryaka.com`, `developer.aryaka.com`,
`portal.aryaka.com`) for OpenAPI/Swagger, GraphQL introspection, MCP `tools/list`, and A2A
agent cards at both `/.well-known/agent-card.json` and `/.well-known/agent.json`. Every
probe missed. `api.aryaka.com` resolves into a domain-parking range and serves nothing.
`www.aryaka.com` answers **HTTP 200 with a "Page Not Found" HTML shell for every unknown
path**, so its 200s on `/.well-known/*` are soft-404s, not published documents — see
[`well-known/aryaka-well-known.yml`](well-known/aryaka-well-known.yml) for the full probe
table. The docs sitemap (384 pages across the KNOW/PTNR/VW spaces) contains no API
reference. Programmatic access is gated behind the MyAryaka portal.

Per the pipeline's search-only rule, **no A2A agent card artifact was written** — an agent
card may only ever be harvested from the provider's own host.

## What Aryaka does publish

| Artifact | Method | Note |
|---|---|---|
| [`llms/aryaka-llms.txt`](llms/aryaka-llms.txt) | searched | Real `llms.txt` served at `https://www.aryaka.com/llms.txt` (200, `text/plain`), saved verbatim |
| [`well-known/aryaka-well-known.yml`](well-known/aryaka-well-known.yml) | probed | Full `/.well-known/` probe table across all hosts, with soft-404s flagged |
| [`authentication/aryaka-authentication.yml`](authentication/aryaka-authentication.yml) | searched | Aryaka Identity Management (AIM) — SAML 2.0/OIDC SSO (Entra, Okta, Duo, AD, LDAP), portal RBAC, network-user identity. **Portal auth, not API auth** |
| [`conformance/aryaka-conformance.yml`](conformance/aryaka-conformance.yml) | searched | SOC 2 Type II, ISO 27001, CSA CCM, GDPR, CCPA verified; FIPS readiness; HIPAA claim unsubstantiated |
| [`changelog/aryaka-changelog.yml`](changelog/aryaka-changelog.yml) | searched | Named seasonal platform releases via the press archive; no API changelog exists |
| [`lifecycle/aryaka-lifecycle.yml`](lifecycle/aryaka-lifecycle.yml) | searched | No public status page, no deprecation policy; SLAs are contractual |
| [`asyncapi/aryaka-siem-log-streaming.yml`](asyncapi/aryaka-siem-log-streaming.yml) | searched | SIEM log streaming (security / flow / Private Access logs) with published attribute references. Not AsyncAPI and not webhooks — no `AsyncAPI`/`Webhooks` pointer emitted |
| [`security/aryaka-domain-security.yml`](security/aryaka-domain-security.yml) | probed | TLS 1.3 everywhere; HSTS only on `docs.aryaka.com`; SPF + DMARC (quarantine); no DNSSEC, no CAA |
| [`packages/aryaka-packages.yml`](packages/aryaka-packages.yml) | searched | Ten registries + GitHub searched — zero first-party SDKs |
| [`mcp/aryaka-mcp.yml`](mcp/aryaka-mcp.yml) | searched | No MCP server; probe record kept so a later round can re-check |

### Notable finding

Aryaka's own `llms.txt` links a "Trust & Security Center" at
`https://www.aryaka.com/legal/security-compliance/` and attributes HIPAA compliance to it.
**That URL returns the site's 404 page.** The SOC 2 / ISO 27001 / GDPR / CCPA claims were
independently verified elsewhere on the site; the HIPAA claim could not be substantiated on
any live page and is recorded as `conforms: false` with that caveat.

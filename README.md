# Aryaka

<!-- API-EVANGELIST-PROVENANCE:BEGIN -->
> ### About this repository
>
> **This is not our API.** This repository is an independent, third-party profile of a company's
> **publicly available** API surface, maintained by [API Evangelist](https://apievangelist.com).
> API Evangelist does not operate, host, resell, or support this company's APIs, and is not
> affiliated with or endorsed by the company unless stated on the profile.
>
> **Where the information came from.** Everything here is assembled from material a member of the
> public can reach with a browser and no credentials — the company's own website, developer portal
> and documentation, the specifications it publishes for public use (OpenAPI, AsyncAPI, JSON Schema,
> `apis.json`, `llms.txt` and similar), its public repositories, and its public status, pricing and
> changelog pages. **Nothing here is obtained by breaching a system, defeating an access control, or
> using credentials of any kind.**
>
> **The rating is an independent assessment.** The Kin Score and Agent Readiness rating are
> independently calculated scores of a company's *public* API artifacts, produced by API Evangelist
> against a published rubric. They are not certifications, endorsements, security assessments, or
> audits, and they score published artifacts — not the quality, safety, or security of the software.
>
> **Corrections, re-scores, and removal are free.** No partnership, contract, or purchase is
> required, and you do not need to justify the request.
>
> - **Something wrong?** Open an issue on this repository, or email
>   [info@apievangelist.com](mailto:info@apievangelist.com).
> - **Published something new?** Ask for a re-score and we will re-run the rating.
> - **Want the listing taken down?** Say so and we will honor it. The profile is reduced to your
>   company name, a factual description, and a link to your own site, and the company is recorded as
>   **unrated** — never scored zero for having asked.
>
> **Response times.** Acknowledgement within **one business day**; removal or restriction within
> **two business days**; corrections and re-scores within **five business days**.
>
> **On a security or compliance team?** Email
> [info@apievangelist.com](mailto:info@apievangelist.com) with *security* in the subject line and
> you will get a person, not a form. We will tell you exactly which public URLs this profile was
> built from so your team can see the same surface we did, and we will take the listing down on
> request while you work through it.
>
> Full detail: **[Where this data comes from](https://apievangelist.com/about/where-our-data-comes-from)**
<!-- API-EVANGELIST-PROVENANCE:END -->

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

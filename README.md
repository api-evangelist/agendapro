# AgendaPro

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
> **Not from the company, and here with a question?** You are welcome here — we would rather be the
> front line and point you the right way than have a good report go nowhere. What this repository
> can answer is narrow, though, so it is worth knowing who you are actually looking for:
>
> - **A question about how the API works, an account, billing, or a bug in the service** — that is
>   the company's own support, not us. We profile this API; we do not operate it and cannot see
>   your account.
> - **A bug in an open-source project we only catalog** — file it on that project's own repository.
>   This has happened with a real and correct bug report that reached us instead of the people who
>   could fix it, which helped nobody.
> - **Anything about this listing itself** — the description, the tags, the rating, a missing or
>   wrong artifact — is ours. Open an issue here.
> - **Not sure, or something general about API Evangelist or APIs.io** — open an issue on the
>   [APIs.io Inbox](https://github.com/api-search/inbox) and we will route it.
>
> **This repository contains no software, and we will never ask you to download anything.** There is
> no build, release, installer, or binary here — only text and machine-readable API descriptions, so
> there is nothing here that can be "corrupt" or need "repairing". Any issue, comment, or email
> claiming otherwise and offering a download link is not from us and is hostile. Do not follow the
> link; it is a lure. Report it to GitHub and, if you like, tell us at
> [info@apievangelist.com](mailto:info@apievangelist.com) so we can take it down.
>
> **On a security or compliance team?** Email
> [info@apievangelist.com](mailto:info@apievangelist.com) with *security* in the subject line and
> you will get a person, not a form. We will tell you exactly which public URLs this profile was
> built from so your team can see the same surface we did, and we will take the listing down on
> request while you work through it.
>
> Full detail: **[Where this data comes from](https://apievangelist.com/about/where-our-data-comes-from)**
<!-- API-EVANGELIST-PROVENANCE:END -->

AgendaPro is a Latin American vertical SaaS platform for appointment-based service businesses — salons, barbershops, spas, aesthetic and medical clinics, gyms, veterinarians and wellness studios — combining online booking, calendar and staff scheduling, client CRM and treatment records, point of sale, inventory, commissions, marketing campaigns and WhatsApp/SMS/email reminders, plus online payments and gift cards. Founded in Chile and operating across Chile, Mexico, Colombia, Peru, Argentina, Brazil and Spain, it serves multi-location merchants from a single account. Its public developer surface is the Connect v3 API, an OpenAPI 3.0.3-described REST gateway at connect.agendapro.com that exposes bookings, availability slots, clients, custom attributes, locations, services, categories, service providers, sales, carts and online payment requests, with Bearer API-key auth, scoped keys, per-minute and per-day rate limiting, and HMAC-signed webhooks. API access requires an active Pro plan.

**Areas:** Appointment Scheduling · Booking · Salon Software · Spa and Wellness · Point-of-Sale · Clinic Management · CRM · Payments · Webhook · Vertical SaaS · Latin America · Small Business

## AgendaPro on APIs.io

Everything profiled for AgendaPro is published on APIs.io rather than in this repository. Start at the provider page — **[apis.io/providers/agendapro/](https://apis.io/providers/agendapro/)** — or go straight to one of the APIs or properties below.

### APIs (10)

- [AgendaPro Available Slots API](https://apis.io/apis/agendapro/agendapro-available-slots-api/) — Query available booking slots for a service at a location
- [AgendaPro Bookings API](https://apis.io/apis/agendapro/agendapro-bookings-api/) — Booking management (list, show, create, update, cancel)
- [AgendaPro Carts API](https://apis.io/apis/agendapro/agendapro-carts-api/) — Shopping carts for the online payment flow
- [AgendaPro Clients API](https://apis.io/apis/agendapro/agendapro-clients-api/) — Client management (list, show, create, update) and custom attributes
- [AgendaPro Custom Attributes API](https://apis.io/apis/agendapro/agendapro-custom-attributes-api/) — Custom attribute templates (company-level definitions)
- [AgendaPro Locations API](https://apis.io/apis/agendapro/agendapro-locations-api/) — Location listing and details
- [AgendaPro Payment Requests API](https://apis.io/apis/agendapro/agendapro-payment-requests-api/) — Online payment requests (checkout URL) on a cart
- [AgendaPro Providers API](https://apis.io/apis/agendapro/agendapro-providers-api/) — Service provider listing and details
- [AgendaPro Sales API](https://apis.io/apis/agendapro/agendapro-sales-api/) — Sales records (read-only)
- [AgendaPro Services API](https://apis.io/apis/agendapro/agendapro-services-api/) — Service catalog listing and details

### Published properties

Each property below is a page on APIs.io carrying the machine-readable artifact and what it says.

#### AsyncAPI (1)

Event-driven and webhook contracts.

- [Agendapro Webhooks](https://apis.io/asyncapis/agendapro/agendapro-webhooks/)

#### MCP servers (1)

Model Context Protocol servers that expose the API to agents.

- [agendapro-mcp.yml](https://apis.io/servers/agendapro/agendapro-mcp-yml/)

#### Overlays (1)

OpenAPI overlays, including conversational phrasing for each operation.

- [Agendapro Connect V3 Overlay](https://apis.io/overlays/agendapro/agendapro-connect-v3-overlay/)

#### Security (2)

Authentication, trust centre, and vulnerability disclosure.

- [Agendapro Authentication](https://apis.io/security/agendapro/agendapro-authentication/)
- [Agendapro Domain Security](https://apis.io/security/agendapro/agendapro-domain-security/)

#### OAuth scopes (1)

The permissions the API asks for.

- [Agendapro Scopes](https://apis.io/scopes/agendapro/agendapro-scopes/)

#### Plans and pricing (1)

Published plans, tiers and prices.

- [Agendapro Plans Pricing](https://apis.io/plans/agendapro/agendapro-plans-pricing/)

#### Rate limits (1)

Published request limits.

- [Agendapro Rate Limits](https://apis.io/rate-limits/agendapro/agendapro-rate-limits/)

## Where to find this API

Links to the company's own pages. This repository publishes no copy of their specifications — the canonical document is theirs and lives at the URLs below.

- [Website](https://agendapro.com/)
- [Documentation](https://developers.agendapro.com/docs/getting-started)
- [Getting started](https://developers.agendapro.com/docs/getting-started)
- [API reference](https://developers.agendapro.com/reference/getting-started-v3)
- [Pricing](https://agendapro.com/en/planes)
- [Sign up](https://agendapro.com/lead/registro)
- [Support](https://ayuda.agendapro.com/)
- [Blog](https://agendapro.com/blog)
- [Terms of service](https://agendapro.com/en/terminos-y-condiciones)
- [Privacy policy](https://agendapro.com/en/politica-de-privacidad)
- [GitHub](https://github.com/agendapro)
- [Status](https://status.agendapro.com/)

## API Evangelist rating

**Kin Score 55.6** — strong · rubric 0.25.0 · scored 2026-10-23

| Facet | Score |
|---|---|
| Discoverability | 73.2 |
| Contract quality | 58.2 |
| Contract governance | 4.5 |
| Operational transparency | 39.5 |
| Developer ergonomics | 58.9 |
| Access clarity | 76.3 |

**Agent readiness 39.9** — agent-ready (gated down from agent-native)

| Agent-readiness dimension | Result |
|---|---|
| Spec Presence | yes |
| Agentic Access | — |
| Reversibility Documented | documented (partial credit) |
| MCP Server | — |
| Auth Clarity | bearer (partial credit) |
| Idempotency | — |
| Error Semantics | verified |
| OpenAPI Examples | verified |
| Rate Limit Signal | verified |
| Event Surface Described | yes |
| Agent Skills | derived (partial credit) |
| Well Known Catalog | — |
| Consent Identity | — |
| Agent Card | — |
| Dry Run Mode | — |
| Delegated Identity | — |
| Protected Resource Metadata | — |
| Dynamic Client Registration | — |
| Agentic Commerce | — |
| Pagination Ratio | partial |
| Operation Distinctiveness | distinct |

**Regulatory alignment 31.3** — Payments

The rubric is published at [github.com/api-evangelist/kin-score](https://github.com/api-evangelist/kin-score). The per-check breakdown behind these numbers — which checks were earned, partial or missed — along with score history and how this provider compares to its peers, is available at [apis.io/providers/agendapro/](https://apis.io/providers/agendapro/).

## How this profile is made

API Evangelist profiles a company's public API surface the way a developer would find it: the website, developer portal and documentation, the specifications it publishes, its public repositories, and its pricing, status and changelog pages. From that it derives the properties above — contracts split per API, workflows, schemas, collections, governance rules, plans and rate limits — and scores them against the published [Kin Score rubric](https://github.com/api-evangelist/kin-score).

The artifacts are published on [APIs.io](https://apis.io), not in this repository. This repository is the public record for AgendaPro: the place to say something is wrong, missing or out of date, and to ask for a re-score or a removal.

## Open an issue

- **Something about this listing** — a wrong description, a missing API, a stale artifact or a question about the rating: [open an issue on this repository](https://github.com/api-evangelist/agendapro/issues/new).
- **A new API, or one that is not in the catalog yet** — [submit it on APIs.io](https://apis.io/add/).
- **Anything else** — [the APIs.io inbox](https://github.com/api-search/inbox/issues/new) or [info@apievangelist.com](mailto:info@apievangelist.com).

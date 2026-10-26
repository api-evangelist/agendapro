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

## API

**AgendaPro Connect v3 API** — `https://connect.agendapro.com`

- Documentation: https://developers.agendapro.com/reference/getting-started-v3
- OpenAPI 3.0.3 — 23 paths, 28 operations, 43 component schemas: `openapi/agendapro-connect-v3-openapi.yml`
- Authentication: per-company Bearer API key (`apk_live_`), Pro plan required
- Rate limits: 70 requests/minute burst, 10,000/day per company
- Webhooks: 6 events, HMAC-SHA256 signed

## Links

- Website: https://agendapro.com/
- DeveloperPortal: https://developers.agendapro.com/
- Documentation: https://developers.agendapro.com/docs/getting-started
- APIReference: https://developers.agendapro.com/reference/getting-started-v3
- GettingStarted: https://developers.agendapro.com/docs/getting-started
- Support: https://ayuda.agendapro.com/
- Blog: https://agendapro.com/blog
- Pricing: https://agendapro.com/en/planes
- SignUp: https://agendapro.com/lead/registro
- Login: https://app.agendapro.com/users/sign_in
- TermsOfService: https://agendapro.com/en/terminos-y-condiciones
- PrivacyPolicy: https://agendapro.com/en/politica-de-privacidad
- StatusPage: https://status.agendapro.com/
- GitHubOrganization: https://github.com/agendapro

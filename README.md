# Liblab (liblab)

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

liblab generates and publishes type-safe, idiomatic SDKs in TypeScript, Python, Java, .NET, Go, PHP, and Terraform from OpenAPI/Swagger/Postman specs, plus MCP servers that expose those APIs to AI agents. The platform ships a CLI, hosted portal, and CI/CD GitHub Action that publish SDKs to customer repos via pull requests. liblab joined Postman in November 2025 to complete the API lifecycle.

**APIs.yml:** [apis.yml](https://raw.githubusercontent.com/api-evangelist/liblab/refs/heads/main/apis.yml)

## Scope

- **Type:** Index
- **Position:** Consumer
- **Access:** 3rd-Party

## Tags

SDKs, SDK Generation, Code Generation, OpenAPI, Developer Tools, MCP, AI Agents, Postman, Terraform, Developer Experience

## Timestamps

- **Created:** 2026-03-03
- **Modified:** 2026-05-22

## APIs

### Liblab SDK Generator
Cloud-based generator that produces customizable, type-safe SDKs in seven target stacks (TypeScript, Python, Java, .NET, Go, PHP, Terraform) from OpenAPI 2.0/3.0/3.1 or Postman Collections. CLI and CI/CD workflows publish SDKs to customer GitHub repos as pull requests.

**Human URL:** https://liblab.com/

**Tags:** SDK Generation, Code Generation, OpenAPI, CLI, CI/CD

**Properties:**

- [Documentation](https://liblab.com/docs)
- [GettingStarted](https://liblab.com/docs/get-started/quickstart-generate-sdk)
- [Portal](https://app.liblab.com/)
- [Hub](https://hub.liblab.com/)
- [CLI](https://liblab.com/docs/cli/cli-overview)
- [GitHubAction](https://github.com/liblaber/liblab-sdk-updates)
- [SampleAPI](https://github.com/liblaber/simple-petstore-openapi)

### Liblab MCP Generator
Generates a complete Model Context Protocol (MCP) server from an OpenAPI, Swagger, or Postman spec so AI chat clients (Claude, Cursor, OpenAI) can call the underlying API in natural language. Launched June 2025; first-year free tier covers 100 MCP calls per month, then $5 per 100 calls.

**Human URL:** https://liblab.com/blog/mcp-generator

**Tags:** MCP, AI Agents, Model Context Protocol, OpenAPI

**Properties:**

- [Announcement](https://liblab.com/blog/2025-06-24-introducing-liblab-mcp-generator)
- [BlogPost](https://liblab.com/blog/mcp-generator)
- [Pricing](https://liblab.com/pricing)

### Liblab Hub
Public catalog of pre-generated SDKs (Python, TypeScript, C#, PHP) for popular third-party APIs (Postman, RingCentral, NYT, UPS, NHL, Pinnacle, OpenHue, Skyscanner, Voyado, Booking, etc.) used to demonstrate generator output quality. Free to use.

**Human URL:** https://hub.liblab.com/

**Tags:** SDKs, Hub, Catalog

### Liblab Terraform Provider Generator
Generates a Terraform provider from an OpenAPI specification, enabling Infrastructure-as-Code workflows against any documented API.

**Human URL:** https://liblab.com/docs

**Tags:** Terraform, Infrastructure, Code Generation

## Common Properties

- [Website](https://liblab.com/)
- [Documentation](https://liblab.com/docs)
- [GettingStarted](https://liblab.com/docs/get-started/quickstart-generate-sdk)
- [Blog](https://liblab.com/blog)
- [Pricing](https://liblab.com/pricing)
- [About](https://liblab.com/about)
- [Contact](https://liblab.com/contact)
- [Portal](https://app.liblab.com/)
- [SignUp](https://app.liblab.com/join)
- [Developer](https://liblab.com/developer)
- [CLI](https://liblab.com/docs/cli/cli-overview)
- [PrivacyPolicy](https://liblab.com/privacy-policy)
- [TermsOfService](https://liblab.com/terms)
- [Hub](https://hub.liblab.com/)
- [GitHubOrganization](https://github.com/liblaber)
- [Twitter](https://x.com/LibLaber)
- [LinkedIn](https://www.linkedin.com/company/liblaber)
- [MCPServer - MCP Generator](https://liblab.com/blog/mcp-generator)
- [GitHubAction - liblab-sdk-updates](https://github.com/liblaber/liblab-sdk-updates)
- [HomebrewTap](https://github.com/liblaber/homebrew-liblab)
- [SampleOpenAPI](https://github.com/liblaber/simple-petstore-openapi)
- [AgentExample - ai-github-agent-example](https://github.com/liblaber/ai-github-agent-example)
- [RAGTemplate - build-a-rag-ai-app-template](https://github.com/liblaber/build-a-rag-ai-app-template)
- [AgentRepo - ai](https://github.com/liblaber/ai)
- [Plans](https://raw.githubusercontent.com/api-evangelist/liblab/main/plans/liblab-plans-pricing.yml)
- [RateLimits](https://raw.githubusercontent.com/api-evangelist/liblab/main/rate-limits/liblab-rate-limits.yml)
- [FinOps](https://raw.githubusercontent.com/api-evangelist/liblab/main/finops/liblab-finops.yml)
- [Acquisition - liblab joins Postman](https://liblab.com/blog/liblab-joins-postman-to-complete-the-api-lifecycle)

## Artifacts

- **Plans** - [plans/liblab-plans-pricing.yml](plans/liblab-plans-pricing.yml)
- **Rate Limits** - [rate-limits/liblab-rate-limits.yml](rate-limits/liblab-rate-limits.yml)
- **FinOps** - [finops/liblab-finops.yml](finops/liblab-finops.yml)
- **Blog mirror** - [blogs/](blogs/)

> No `openapi/`, `capabilities/`, `json-schema/`, `json-structure/`, `json-ld/`, `vocabulary/`, `rules/`, or `examples/` directories are published in this repo. liblab is an SDK + MCP generation platform, not a transactional API provider, so there is no public OpenAPI surface of its own to anchor those artifacts. The platform's outputs (SDKs, MCP servers, Terraform providers) are generated downstream from each customer's own spec.

## Maintainers

**FN:** Kin Lane

**Email:** kin@apievangelist.com

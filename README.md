# Liblab (liblab)

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

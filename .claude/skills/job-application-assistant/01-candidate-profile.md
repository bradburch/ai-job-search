---
framework_version: 1.0.0
---

# Candidate Profile

## Identity
- **Name:** Brad Burch
- **Location:** San Francisco, CA
- **Phone:** (574) 835-6870
- **Email:** bradburch.jobs@gmail.com
- **LinkedIn:** linkedin.com/in/burchbrad
- **GitHub:** github.com/bradburch (portfolio: bradburch.github.io)
- **Languages:** English (Native or Bilingual)
- **Status:** Currently self-employed (Founder & Software Engineer, Pawservation). Actively looking to join an established engineering team — not seeking founding/0-to-1 solo roles.
- **Constraints:** San Francisco based; on-site or hybrid; open to occasional travel for customer-facing work.
- **EEO / application questions:** US citizen; not a veteran; no disability.

## Education

| Degree | Period | Institution | Key Topics |
|--------|--------|-------------|------------|
| Bachelor of Arts, Computer Science | 2013-2017 | DePauw University | Core CS coursework |

## Professional Experience

### Founder & Software Engineer - Pawservation (Sept 2022 - Present)
San Francisco, CA
- Owned the full product loop end-to-end for a real SF pet-care business (30+ active clients, 60+ bookings/month, 30+ invoices/month): discovery with clients, system design, implementation, deploy, support, and iteration as sole engineer.
- Built and operate a production Claude Haiku 4.5 chat agent (15 tools, Vercel AI SDK v6) with two-phase confirmation on mutations and layered cost controls: per-user rate limits, daily token budgets, a circuit breaker, and hard per-user/global USD caps via a reserve-then-reconcile scheme.
- Built a standards-compliant OAuth 2.1 + PKCE MCP server exposing the same tool surface to external AI agents; documented and published the spec.
- Designed and built a TypeScript monorepo on Cloudflare Workers (React 19, Hono, a 23-table D1 schema, KV, R2, Workflows) with no origin server, integrating Google Calendar, Notion, Gmail, and Venmo with per-source failure isolation.
- Modeled the core booking domain: conflict-aware scheduling with pet-count capacity rules, a server-enforced tiered cancellation policy, and combined-set multi-pet pricing that keeps quote, charge, and invoice in agreement.
- Re-architected a fragile calendar backfill into a Cloudflare Workflows fan-out/fan-in with exactly-once finalization and silent-failure alerting.
- Hardened production against real attack classes: revocable server-side sessions, SPF/DKIM-verified payment ingestion, and RFC 5987 filename encoding closing a header-injection vector.
- Published a public AI security self-audit (prompt injection, tool scoping, auth boundaries); shipped a WCAG 2.1 AA accessibility pass.
- Built a CI-gated Vitest + Playwright test suite audited for assertion quality, not line coverage; the audit surfaced and closed four silently-untested security controls. Zero customer-impacting incidents to date.
- Extracted and open-sourced two components: Pawservation (embeddable multi-tenant booking widget on Cloudflare Workers) and mcp-auth-kit (OAuth 2.1 + PKCE MCP server kit).

### Software Engineer - Front (May 2022 - Sept 2022)
San Francisco, CA (role eliminated in company-wide layoff)
- Shipped a Node.js REST API enabling account-level email rules for multi-domain enterprise customers (previously configurable only per-inbox), driving a 30% increase in adoption.
- Optimized the contact CSV importer for incremental file uploads while preserving historical customer data, cutting processing time 5%.
- Performed a security upgrade on the core JavaScript email library responsible for 200K+ outbound messages/month.

### Software Engineer - Total Brain (May 2019 - Sept 2021)
San Francisco, CA
- Engineering point of contact on enterprise Customer Success and Sales calls: scoped integrations live, demoed to technical and business stakeholders, debugged customer issues, and wrote onboarding integration guides.
- Built custom enterprise integrations (HubSpot CRM sync, Box secure file storage) and standardized SAML 2.0 + JWT SSO across the platform, cutting enterprise onboarding from 2+ weeks to ~3 days.
- Designed a Scala backend integration for Apple, Google, and Facebook authentication, contributing to a 60% lift in new sign-ups.
- Migrated user data from MSSQL to DynamoDB with a redesigned NoSQL schema, cutting average API response times 50%; added an in-memory caching layer that raised read throughput 50%.
- Built the backend CI/CD pipeline on Jenkins with bash release automation, raising deploy frequency 75%; mentored junior engineers on backend patterns.

### Software Engineer - Salesforce.com (Jul 2017 - Aug 2018)
San Francisco, CA
- Built and maintained Spring-based automated testing frameworks across the Salesforce ecosystem on a developer productivity team.
- Built a Spring-based OAuth2 security filter for microservice access control, plus a React management UI that cut internal test setup time 40%.
- Designed a persistent repository for integration-test state using Java, Spring, PostgreSQL, and EclipseLink.
- Led delivery of a config builder and validator used by internal teams, scoping milestones and coordinating partner teams to ship on schedule.

### Software Engineer Intern - Salesforce (May 2016 - Aug 2016)
Indianapolis, IN
- Built a REST API returning complex SMS Message objects.
- Worked on minor bug fixes within an Agile team environment.

## Independent Projects
- **Pawservation**: Embeddable multi-tenant booking widget on Cloudflare Workers, extracted and open-sourced from the Pawservation production system.
- **mcp-auth-kit**: OAuth 2.1 + PKCE MCP server kit, extracted and open-sourced from the Pawservation production system.
- **Roadrunner**: Django app that matches eBird and iNaturalist observations to overlapping Strava activities and writes the species list into each activity's description (Strava API, deployed on Vercel).

## Technical Skills

### Programming & ML
- **TypeScript / JavaScript** (primary): React 19, React Router 7, Node.js, Hono
- **Python**: Django (Roadrunner)
- **Go, Java, Scala, SQL**; Spring, Play (JVM frameworks)
- **AI/LLM**: Claude (Haiku 4.5, Sonnet), Claude Code, Cursor, AI coding agents, Vercel AI SDK v6, Model Context Protocol (MCP), agentic tool loops, streaming SSE, prompt design

### Domain Expertise
- Forward-deployed / customer-facing engineering: requirements gathering, live technical demos, integration scoping, POC-to-production delivery
- Auth & security: OAuth 2.0/2.1 + PKCE (RFC 7636), JWT, SAML 2.0, refresh token rotation, CSRF/XSS hardening
- Production operations: on-call ownership, runbooks, technical writing, structured logging, monitoring & alerting

### Software & Tools
- Cloudflare (Workers, D1, KV, R2, Workflows), AWS (DynamoDB, SQS), PostgreSQL, MSSQL, SQLite, Docker, Linux
- Git, Vitest, Playwright, GitHub Actions, Jenkins, CI/CD
- Google Calendar v3, Notion, Gmail, HubSpot, Box, REST, Webhooks

## Certifications
- Essentials for Solution Engineers
- Creative Problem Solving for Technologists
- What Is Generative AI?
- Hands-On AI: Building AI Agents with Model Context Protocol (MCP) and Agent2Agent (A2A)
- Generative AI: The Evolution of Thoughtful Online Search

## Publications
None currently.

## Awards
- Dean's List - DePauw University (multiple semesters)
- Computer Science Department Honor Society - DePauw University

## References
None on file yet. Add reference letters to `documents/references/` and re-run `/setup`, or provide contact details directly to add here.

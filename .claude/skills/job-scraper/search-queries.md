# Search Queries for Job Scraper

## Installed portal CLIs (primary for `/scrape`)

`/scrape` discovers every portal skill under `.agents/skills/*/SKILL.md` and runs its CLI first. Shipped country-agnostic CLIs include `linkedin-search` and `freehire-search`. You do **not** need a matching `site:` line below for those CLIs to run.

**Indeed, Wellfound, and Welcome to the Jungle have no CLI skill installed yet** — there's no shipped `.agents/skills/` scaffold for them, so `/scrape` falls back to the `site:` WebSearch queries below for these three. Run `/add-portal` for any of them if you want a proper CLI integration (faster, more reliable than WebSearch scraping).

The `site:` query templates in this file are the **WebSearch fallback** — for portals without a CLI, company career pages, or when a CLI fails. Plain (non-`site:`) Google searches are also fair game for company career pages and roles that don't show up on the major boards.

**Language scope:** write every query category in every language listed in your CLAUDE.md Languages table (typically 1-2, sometimes more). A posting requiring a language you have *not* declared, as a job condition, is excluded before scoring; a posting requiring a *higher level* than you declared in a language you *do* work in is flagged for your own judgment, not excluded — see `04-job-evaluation.md`'s Language Gate, the single source of truth for this rule. Translate each category's keywords rather than machine-translating word-for-word (e.g. "Frontend Developer" -> "Desarrollador Frontend", not a literal word-for-word translation) if you work in more than one language.

## Search Sites

Primary:
- **linkedin.com/jobs** — also covered by the `linkedin-search` CLI
- **indeed.com** — WebSearch fallback (no CLI yet)
- **wellfound.com** — WebSearch fallback (no CLI yet); strong fit given the Series B+ company-stage preference below
- **welcometothejungle.com** — WebSearch fallback (no CLI yet)

Secondary (company career pages via Google):
- Direct Google searches, with and without `site:` filters, for known target companies and general FDE/SWE openings in the SF Bay Area

## Company Stage Filter

Target companies **Series B through enterprise/public**. Deprioritize pre-seed/seed/Series A postings — those roles skew toward "founding engineer" scope, which is explicitly out of scope (see `01-candidate-profile.md` Identity/Status). When a posting's funding stage is unclear, check Crunchbase/the company's own press page before including it, and flag as "stage unknown" rather than guessing.

## Query Categories

Queries are grouped by priority. Write **each category in every language from your Languages table** (see Language scope above). Combine each query with your location terms (e.g. your city, region, or metro area) where the site supports it.

**Organize by function, not job title.** The same underlying work carries different titles across companies and markets (a "Data Scientist" role at one employer may be posted as "Insights Analyst" or "Data Consultant" at another). Name each priority category after the function it covers, and list several plausible job titles as query variants within that category rather than betting an entire priority tier on one exact title string.

### Priority 1: Product Engineer / Software Engineer (top) + Member of Technical Staff / Forward Deployed Engineer (still accepted, lower priority)

Primary targeted titles, and variations on those titles (Solutions Engineer dropped — "SE was a dead end"). Product Engineer and Software Engineer are the top titles; Member of Technical Staff and Forward Deployed Engineer are still accepted but ranked lower.

```
site:linkedin.com/jobs "Software Engineer" "Cloudflare Workers" San Francisco
site:linkedin.com/jobs "Product Engineer" San Francisco
site:linkedin.com/jobs "Member of Technical Staff" San Francisco
site:linkedin.com/jobs "Forward Deployed Engineer" San Francisco
site:indeed.com "Forward Deployed Engineer" "San Francisco Bay Area"
site:wellfound.com "Software Engineer" OR "Product Engineer" OR "Member of Technical Staff" OR "Forward Deployed Engineer"
site:welcometothejungle.com "Forward Deployed Engineer" San Francisco
"Product Engineer" OR "Member of Technical Staff" San Francisco Bay Area Series B OR Series C OR Series D
"Forward Deployed Engineer" San Francisco Bay Area Series B OR Series C OR Series D
```

### Priority 2: Core skill match

These match the strongest technical skills — TypeScript, Cloudflare Workers, LLM/agentic engineering.

```
site:linkedin.com/jobs "TypeScript" "Claude" OR "LLM agents" San Francisco
site:indeed.com "Cloudflare Workers" San Francisco Bay Area
site:wellfound.com "Model Context Protocol" OR "MCP" engineer
"React" "Node.js" software engineer San Francisco Bay Area -junior -intern
```

### Priority 3: Adjacent roles worth a look

Not actively requested, but worth including given the customer-facing + full-stack-ownership background — drop if they turn out to be noise.

```
site:linkedin.com/jobs "Implementation Engineer" San Francisco
site:linkedin.com/jobs "Customer Engineer" TypeScript OR Cloudflare San Francisco
```

### Priority 4: Broader technical net

Wider net across full-stack/backend roles matching the core stack.

```
site:indeed.com "full stack engineer" TypeScript San Francisco
site:linkedin.com/jobs "backend engineer" Cloudflare OR AWS San Francisco Bay Area
site:wellfound.com software engineer TypeScript remote
```

## Location Filter

- **Ideal:** Remote (US-based) or hybrid, anywhere in the SF Bay Area
- **Acceptable:** On-site, within San Francisco city proper
- **Borderline:** On-site elsewhere in the greater Bay Area (Oakland, Peninsula, South Bay, East Bay) — flag for discussion, not an automatic pass
- **Too far:** On-site outside the Bay Area with no remote option

## Salary Filter

Minimum $180k base. Exclude postings that list a range entirely below this unless the user flags a specific reason to reconsider.

## Language Filter

Your working languages and levels are in CLAUDE.md's Languages table. When filtering scraped results, apply `04-job-evaluation.md`'s Language Gate: a posting requiring a language you haven't declared at all is excluded; a posting requiring a higher level than you declared in a language you do work in is not excluded, flag it clearly instead (see `job-scraper/SKILL.md`'s Step 3 "Quick Fit Assessment" for how the flag surfaces in `/scrape` output). Postings simply *written* in a language you don't work in, that don't require it on the job, are fine.

## Date Filter

Only include jobs posted within the last 14 days, or with an application deadline that has not yet passed. If a posting date cannot be determined, include it but flag as "date unknown".

## Adapting Queries

If the user specifies a focus area, select queries from the matching category and also generate 2-3 custom queries for that focus. For example:
- "/scrape [focus_area]" -> relevant category queries + custom focus-specific queries

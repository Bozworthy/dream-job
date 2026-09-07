# Company ATS Directory

Built 2026-09-06 from the first test run. Purpose: skip the dead-link problem entirely by going straight to each company's live source of record instead of following cached search-engine links to specific job IDs.

## General rule
Never trust a specific job URL surfaced by web search as current. Either query the company's own live search/API, or browse their current full listing, and only then pick out the live posting.

## Public ATS APIs (verified working 2026-09-06)

These return exact, current, structured JSON — faster and more reliable than browsing, and immune to stale cache problems. Use these first whenever a company's board token is known.

**Greenhouse**
`GET https://boards-api.greenhouse.io/v1/boards/{board_token}/jobs`
Add `?content=true` to a single job's URL (`.../jobs/{id}?content=true`) for the full description.
Verified against: affirm (204 jobs), reddit (148), chime (65), pinterest (189, confirmed Greenhouse-backed despite custom-looking domain).

**Ashby**
`GET https://api.ashbyhq.com/posting-api/job-board/{company_slug}`
Verified against: bumbleinc (returns live postings with title/department/location/publishedAt).

**Lever**
`GET https://api.lever.co/v0/postings/{company}?mode=json`
Confirmed the pattern works (bumbleinc returns `[]` — correctly reflects their empty Lever board; Bumble's real postings are on Ashby, not Lever).

## Per-company notes

| Company | ATS | Direct source | Notes |
|---|---|---|---|
| Affirm | Greenhouse | `boards-api.greenhouse.io/v1/boards/affirm/jobs` | Board token confirmed: `affirm` |
| Reddit | Greenhouse | `boards-api.greenhouse.io/v1/boards/reddit/jobs` | Board token confirmed: `reddit`. No Content Designer role as of 2026-09-06. |
| Chime | Greenhouse (behind careers.chime.com) | `boards-api.greenhouse.io/v1/boards/chime/jobs` | careers.chime.com is Cloudflare-protected and unreliable to browse directly (bot check, stale-looking redirects) — use the API instead, it bypasses this entirely. |
| Pinterest | Greenhouse (behind pinterestcareers.com) | `boards-api.greenhouse.io/v1/boards/pinterest/jobs` | Custom-looking domain is a Greenhouse front end (`?gh_jid=` param gives it away). Use the API — pinterestcareers.com job pages 404 unpredictably even for live roles. |
| Bumble | Ashby | `api.ashbyhq.com/posting-api/job-board/bumbleinc` | Lever board (`jobs.lever.co/bumbleinc`) exists but is empty/unused — don't bother checking it. `team.bumble.com` is blocked by browser policy (dating-app domain) — don't try to browse it directly. |
| Notion | Greenhouse (probably) | `job-boards.greenhouse.io/notion/jobs/{id}` | Board token `notion` returned 404 on the boards-api — token likely differs from the URL slug. Needs re-confirmation before relying on the API; fall back to browsing job-boards.greenhouse.io/notion directly for now. |
| Google | Custom | `google.com/about/careers/applications/jobs/results/?q={query}` | No public API. Use the site's own live search with a query param — confirmed reliable and current. Individual job IDs from search engines are frequently stale/taken down; always re-derive from a fresh query. |
| Meta | Custom | `metacareers.com/jobsearch/` | No public API. Site's own listing/search is reliable; specific job IDs found via web search were current when checked, but verify via the site's own search, not a bare web search result. |
| Stripe | Custom | `stripe.com/jobs/search` (has a search textbox, `ref_32` was "Search for a role" in one session) | No public API. Live search returned "no open roles" for content design as of 2026-09-06 — that result is trustworthy since it came from the site's own search, not a cached link. |
| Figma | Custom | `figma.com/careers/` | No public API, but the full open-jobs list renders directly on the page — no search needed, just read the full list (it's short enough). No UX Writer/Content Design role as of 2026-09-06. |
| Block / Cash App | Custom | `block.xyz/careers` | No public API. Full listing renders on the page grouped by department — read the "Design" category directly. No Content Designer role as of 2026-09-06 despite multiple stale search results claiming otherwise. |
| Atlassian | Custom | `atlassian.com/company/careers` | Not yet tested against live search this run — treat any web-search-found job ID as unverified until checked directly. |
| PayPal | Workday | `paypal.wd1.myworkdayjobs.com/en-US/jobs?q={query}` | Workday's own search works via `?q=` param — confirmed reliable (returned accurate "no content designer roles" result as of 2026-09-06). Specific job IDs from web search were stale (404). |
| Netflix | Unknown | — | Not yet tested. |
| Spotify | Unknown | — | Not yet tested. |

## Efficiency rule going forward
1. If the company is in the table above with a working API, call the API first — it's a single request, always current, no dead links possible.
2. If the company has a custom site with its own live search (Google, Meta, Stripe, PayPal), use that search directly with the query term — never a bare web search.
3. If the company has a custom site with a full listing and no search (Figma, Block), read the full department listing directly.
4. Only fall back to general web search for companies not yet in this table, and treat every resulting job URL as unverified until confirmed through one of the above.
5. Add newly-discovered companies to this table as they come up, so the one-time discovery cost is never paid twice.

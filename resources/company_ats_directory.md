# Company ATS Directory

Built 2026-09-06 from the first test run. Purpose: skip the dead-link problem entirely by going straight to each company's live source of record instead of following cached search-engine links to specific job IDs.

## General rule
Never trust a specific job URL surfaced by web search as current. Either query the company's own live search/API, or browse their current full listing, and only then pick out the live posting.

## Platform-wide search patterns (role-first, not company-first)

Run these every pass, in addition to the named-company checks below. These search an entire ATS platform for the target roles regardless of which company posted them — this is how you catch a strong-fit role at a company that was never on the named list. Added 2026-09-16 after missing Teladoc Health's Lead Content Designer posting (found by Jon via LinkedIn, on Workday, fully remote, $135K-$165K, conversation design + generative AI in a regulated industry) — a company-by-company sweep was never going to find it because Teladoc was never on the list to check.

Role terms to pair with each platform query — run as a couple of separate passes rather than one giant OR chain, since search engines truncate long queries:
- Pass 1: "content designer" OR "content design" OR "UX writer" OR "conversation designer" OR "conversation design" OR "content strategist"
- Pass 2: add "lead" / "staff" / "principal" / "senior" to catch seniority-specific titles that rank differently

Query templates (WebSearch, one platform at a time):
- Greenhouse: `site:job-boards.greenhouse.io OR site:boards.greenhouse.io "content designer" OR "content design" remote`
- Ashby: `site:jobs.ashbyhq.com "content designer" OR "UX writer" OR "conversation design"`
- Lever: `site:jobs.lever.co "content designer" OR "UX writer"`
- Workday: `site:myworkdayjobs.com "content designer" OR "content design" remote`

Confirmed effective 2026-09-16: the Workday query surfaced three previously-unfound Netflix postings (Conversational Designer, Senior Content Designer/Ads Platform, Senior Content Designer/Acquisition) — Netflix's ATS was marked Unknown below; it's Workday, tenant `netflix.wd1.myworkdayjobs.com`.

Known limitation: general web search indexes a fraction of what's actually live on these platforms, with lag and incomplete coverage, especially for lower-profile employers — the same Workday query did not surface Teladoc's posting even after it was known to exist. This catches meaningfully more than company-by-company checks alone, but it isn't a substitute for LinkedIn's own index. Treat a platform-wide sweep coming up empty as "found nothing this pass," not "nothing is out there."

Once a platform-wide sweep surfaces a company not already in the table below, verify it live the same way as a named company (API first if the platform has one, direct site otherwise) and add a row to the table so the discovery cost isn't paid twice. Check it against the reputability bar in job_search_criteria.md before including it in any report.

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
| Netflix | Workday | `netflix.wd1.myworkdayjobs.com` | Found via platform-wide Workday sweep 2026-09-16. Has had Content Design/Conversation Design roles — worth checking each pass. |
| Spotify | Custom (lifeatspotify.com) | `lifeatspotify.com/jobs` | Site is JS-rendered — WebFetch only gets the filter shell, not real listings, on the general jobs page. Individual job detail pages do resolve directly when the exact URL is still live; a closed posting returns a clean 404 on the same URL, which is a reliable "still open or not" signal even though the listing page itself isn't browsable this way. |
| Stripe | Custom (stripe.com/jobs) | `stripe.com/jobs/search?query={term}` | Confirmed working 2026-09-15 — the search page renders real job titles directly (not JS-shell-only like Spotify), and a closed posting's direct URL returns a clean 404. |
| Block / Cash App | Custom (block.xyz/careers) | `block.xyz/careers/jobs/{id}` | WebFetch fails on individual job pages with a "Header overflow" parse error, consistently, as of 2026-09-15/16 — a tool-side issue (likely an oversized response header from their site), not a signal about whether the posting is live. Can't currently verify Block postings by direct fetch; cross-reference via search and flag as unconfirmed, or ask Jon to check by hand. The block.xyz root domain and non-careers paths fetch fine, so it's specific to the /careers/jobs/ path. |
| Google | Custom | `google.com/about/careers/applications/jobs/results/?q={query}` | Individual job pages are JS-rendered — WebFetch gets the page shell/nav only, not the listing content, so status can't be confirmed by direct fetch. Cross-reference via search instead. |
| Apple | Custom (jobs.apple.com) | `jobs.apple.com/en-us/search?product={id}&team={id}` | Confirmed working 2026-09-15 — the search-results page renders real job titles, locations, and posted dates directly. Individual job detail pages are JS-rendered and don't resolve via WebFetch, but the search page alone is enough to verify a listing. |
| Teladoc Health | Workday | `teladoc.wd503.myworkdayjobs.com` | Not a named target company — surfaced via Jon finding a LinkedIn posting. The Lead Content Designer role (JR21040) was confirmed live 2026-09-16 via the Workday CXS API, then confirmed dead by Jon clicking the link himself 2026-09-17 — closed in about a day from first sighting. Worth re-checking this company's board occasionally given the fit (conversation design + generative AI in a regulated industry parallels Jon's Credit Karma AI dispute-filing work), but don't trust a cached JR number — always re-derive from a fresh board check. |

## Efficiency rule going forward
1. If the company is in the table above with a working API, call the API first — it's a single request, always current, no dead links possible.
2. If the company has a custom site with its own live search (Google, Meta, Stripe, PayPal), use that search directly with the query term — never a bare web search.
3. If the company has a custom site with a full listing and no search (Figma, Block), read the full department listing directly.
4. Only fall back to general web search for companies not yet in this table, and treat every resulting job URL as unverified until confirmed through one of the above.
5. Add newly-discovered companies to this table as they come up, so the one-time discovery cost is never paid twice.

# Funnel snapshot, 2026-09-30

First synthesis of application outcomes and portfolio analytics (SOP Step 11). Data: Gmail Aug 1 to Sep 30, and all 635 portfolio events since tracking began Aug 6 (website-analytics-hub.replit.app). Per-application detail lives in application_tracker.md.

## Funnel

| Stage | Count |
|---|---|
| Applications with ATS confirmation | ~30 |
| Resumes built in Drive with no confirmation on record | 9 (see tracker) |
| Evidence a person viewed the portfolio | 3 (IQ Fiber, Chime, EY likely) |
| Interview processes | 2 (IQ Fiber, Pearl), plus 1 agency AI screen (Onward Search) |
| Rejections | 9 |
| Offers | 0 |

## Response timing (9 rejections, small sample)

- **1 day (Cisco):** consistent with an automated screen.
- **CVS (1.6 days):** the Senior Content Designer resume was logged against a Scrum Master requisition. Likely a submission error. Excluded from screening analysis.
- **3–13 days (Wealthfront, Airbnb, Spring Health, PwC, Chime):** mix of screening and human review.
- **~4 weeks (Bolt.new, Amazon AWS):** late batch declines.
- **"Filled" (Chime, Bolt.new):** the role closed. Excluded from ATS-versus-human analysis.
- **Three Staff-level roles failed fast** (Airbnb, Spring Health, Bolt.new). Possible pattern, too few points to call it.

## What drove deeper discovery

1. **Company-specific portfolio page (IQ Fiber):** strongest signal. 31 views of `/iq-fiber` over a week from several devices, with LinkedIn and Microsoft Teams referrers, which points to the link being shared inside the company. It is also the application that moved fastest (recruiter reply in 1 day).
2. **Network:** IQ Fiber's hiring lead already knew Jon's name.
3. **Tagged resume link (`?ref=`):** Chime and likely EY produced human visits past the landing page. Seven other tagged links show no outside visits yet (Airbnb, Netflix, CVS, JPMorgan, Wealthsimple, Huge, Capital One). Four were sent only 5 days ago.

All tagged links land on `/software`. Only IQ Fiber and Bumble got a company-specific page.

## Reading portfolio visits

- **Jon uses macOS.** Every Windows, iOS, Android or Linux visit is someone else. 71 of 635 views came from Windows.
- **Likely a machine:** several resume links opened within seconds of each other, at or just after submission (EverBank 8/19, EY 9/13 at 17:18, 9/30 at 03:14).
- **Likely a person:** views spread over minutes, or a return visit on a later day (Chime 9/8 and 9/10, EY 9/13 to 9/15).

## Dashboard issues that limit the data

1. **Jon's own visits aren't filtered out:** includes 37 localhost and preview visits. 383 of 635 views are macOS and can't be attributed.
2. **Sessions are split:** 283 of 344 sessions have one view (one visitor got 4 session IDs in 15 seconds). Visit depth is unreliable.
3. **Time on page isn't recorded:** active seconds are 0 everywhere, and `/api/analytics/duration` returns 404.
4. **Attribution misses `?ref=` codes:** the "Tracked link" cohort shows 0 while `?ref=` visits exist.
5. **Fixed time filter:** the stats endpoints accept only `period=all` or the default last 7 days.

## Process gap

Two mismatches between Drive and the ATS emails (CVS req, several resumes with no confirmation) mean the submission step is where records drift. Logging the req ID and confirmation email at submission (SOP Step 7) would catch this the same day.

## Options to consider

- **Company page test:** build a company-specific page for the next top-priority application and compare against `/software` links.
- **Follow up on EY:** most outside reading after IQ Fiber, no decision after 17 days.
- **Self-exclusion:** add a self-exclusion flag to the tracking snippet (a localStorage opt-out on Jon's browsers) before judging any more `?ref=` data.
- **CVS:** check whether the Senior Content Designer role is still live and apply to the correct requisition.
- **Staff-level roles:** track Staff-level results separately to test the fast-rejection pattern.

# Funnel snapshot, 2026-09-30

First synthesis of application outcomes and portfolio analytics (SOP Step 11). Data: Gmail Jul 10 to Sep 30, tailored resumes in Google Drive (each one is an application), and all 635 portfolio events since tracking began Aug 6 (website-analytics-hub.replit.app). Per-application detail lives in application_tracker.md.

## Funnel

| Stage | Count |
|---|---|
| Applications (Jul 10 – Sep 30) | 47 |
| With an ATS confirmation email | 35 |
| With no confirmation email | 10, plus 2 unclear (see tracker note) |
| Evidence a person viewed the portfolio | 3 (IQ Fiber, Chime, EY likely) |
| Interview processes | 2 (IQ Fiber, Pearl), plus 1 agency AI screen (Onward Search) |
| Closed | 13 (4 are "filled" or the CVS requisition mix-up) |
| Offers | 0 |

## Response timing (13 closed, small sample)

- **1–2 days (Cisco, Amazon Integrated Campaigns):** consistent with an automated screen.
- **CVS (1.6 days):** the Senior Content Designer resume was logged against a Scrum Master requisition. Likely a submission error. Excluded from screening analysis.
- **3–12 days (Wealthfront, Airbnb, Hospitable, Spring Health, AngelList, PwC):** mix of screening and human review. Two say "after reviewing your work," which suggests a person looked.
- **~4 weeks (Bolt.new, Amazon AWS):** late batch declines.
- **"Filled" (Chime, Bolt.new, Brightway):** the role closed. Excluded from ATS-versus-human analysis.
- **Staff-level roles:** Airbnb, Spring Health and Hospitable (all Staff) were declined in 3–6 days. Possible pattern, too few points to call it.
- **No reply in 70+ days:** Notion, CAI, Red Ventures, SS&C. These are most likely dead.

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

Two mismatches between Drive and the ATS emails mean the submission step is where records drift: the CVS requisition, and 10 applications with no confirmation email (5 of them Google, 2 Capital One). Logging the req ID and confirmation email at submission (SOP Step 7) would catch this the same day.

## Options to consider

- **Company page test:** build a company-specific page for the next top-priority application and compare against `/software` links.
- **Follow up on EY:** most outside reading after IQ Fiber, no decision after 17 days.
- **Self-exclusion:** add a self-exclusion flag to the tracking snippet (a localStorage opt-out on Jon's browsers) before judging any more `?ref=` data.
- **Check candidate portals:** Google and Capital One normally send a confirmation per application. Their portals would show whether those 7 submissions went through.
- **CVS:** check Candidate Home to see which title the application is filed under. No CVS content design role is live as of 9/30.
- **Staff-level roles:** track Staff-level results separately to test the fast-rejection pattern.

# Workflow SOP

## Goal
Produce the best roles, and why they are the best, for Jon to apply to and provide a tailored resume and the information he needs to optimize his success probability of getting the job.

## Job tracker
Location (confirmed by Jon 2026-09-23): the Replit project https://replit.com/@weathercat/Website-Analytics-Hub. Not the abandoned Google Sheet.

Access status as of 2026-09-23: Claude can't read it yet. The replit.com project page needs a Replit login, and this session has no Replit connector. The published app (website-analytics-hub.replit.app) serves only the site-analytics dashboard. Its routes are /, /devices, /events, /pages, /referrers, /snippet, and its public API is /api/analytics/* (summary, timeseries, top-pages, referrers, devices, recent). No tracker route or data is in the published build. Until access is solved, rebuild the applied list from Gmail confirmations and treat it as partial.

## Process
Step 0: Check what Jon has already applied to before running any search pass, automated or on-demand. Cross-reference every company and role against three sources, because none of them is complete on its own:
1. The job tracker (Replit, see above), once it's readable.
2. Google Drive: search for resumes created in the last 90 days (`title contains 'Resume'`). Each tailored resume's creation date counts as the application date, per Jon (2026-09-23). Read the resume's header or summary when the filename doesn't give the exact role title.
3. Gmail: search for application confirmations and rejections since the last pass.

A role is out of the report if any of the three shows an application, and it's also out if the title matches even when the company only uses a generic name ("Amazon ConversationDesign"). When a match is likely but not certain, list the role under "possibly already applied" instead of recommending it. Update resources/applications_log.md with anything new.

This is a real, confirmed failure mode, twice over. The week of 2026-09-14, Pinterest's Content Designer II, Personalization role was presented as new every day Monday through Thursday, even though Jon applied 2026-09-07. On 2026-09-23, Amazon's Sr. UX Conversation Designer (Customer Service) was recommended even though Jon had applied 8/27. Gmail showed no confirmation, and the Drive resume was never checked.

Step 0b: Audit every newly found submitted resume against source_of_truth.md, once per resume. Flag employer or date misattributions, retired phrasings, titles that differ from the chronology, and metrics missing from the SOT. Tell Jon once, in plain terms, because these claims can come up in a screen. Don't re-flag the same resume on later passes. Record the audit date in applications_log.md.

Step 1: Automated search cadence:
- **Monday, 12:00 PM ET**: quick check — scan for new postings and tell Jon approximately how many meet the qualification criteria. Not a full ranked list, just a count so he knows what to expect.
- **Tuesday, 9:00 AM ET**: full search — run the complete search and qualification process, with results ready by 10:00 AM ET.
- **Any other time**: on-demand, triggered by Jon prompting "Let's find a dream job" in the dream-job project. Claude pulls from the most recent automated search rather than searching live, unless enough time has passed that a fresh search makes more sense.

Every pass — automated or on-demand — runs two search modes, not one (full detail in job_search_criteria.md's Search sources section and company_ats_directory.md's platform-wide query templates):
1. Named company sweep — check each named target company directly against its known ATS.
2. Platform-wide role sweep — search each major ATS platform directly for the target roles, independent of company name, so a strong-fit role at an unnamed-but-reputable company doesn't get missed just for being off the list. Verify anything this surfaces the same way as a named-company find, and check it against the reputability bar in job_search_criteria.md before including it in a report.

Step 2: Identify the top 3-5 roles from the most recent search, sorted by priority. Priority order:
1. Fitness — likelihood of getting the job and skills match (primary)
2. Recency of the posting (secondary)
3. Pay, based on the best info available from research (tertiary)

Step 3: Tailor Jon's resume for each role, matching to his preferred content design and formatting.

Step 4: Evaluate and send Jon the list with details and overviews and tailored resume. Alongside each resume, provide:
1. The most direct link to apply at the company — the employer's own careers site or ATS, per the posting qualification criteria in job_search_criteria.md, not an aggregator.
2. Alignment insights that can inform a cover letter — why Jon specifically fits this role, pulled from source_of_truth.md, not written fresh.

Step 5: Jon will share changes made to resume, discuss and update resume generation rules so resumes improve over time.

Step 6: Prepare any ancillary documents (cover letter, blog post for portfolio, LinkedIn post) and tracking links (for blog posts, LinkedIn posts, etc.) that will help the application succeed and allow us to track its progress.

Step 7: Jon applies and shares the final resume and collateral he actually submitted. Receiving that submission is the confirmation the application happened — Claude logs the date and time at that point, starting the clock on monitoring email response. If a role was recommended and no submission was shared by the next time Jon runs "Let's find a dream job," Claude pings Jon to ask whether he applied, and uses his answer to inform future selection and prioritization strategy.

Once submission is confirmed — same day, not deferred — Claude updates the job tracker: company, role, resume link, apply link, tracking link, and date applied. Then Claude begins checking email for a submission-confirmation message from the employer/ATS and records that confirmation date in the tracker once it arrives.

Step 8: Claude continues to monitor progress via emails received, activity on the portfolio site, or link activity, especially tracking for interview requests, updating the job tracker as status changes. LinkedIn activity is monitored by Jon independently (or checked when Claude prompts him to) — not something Claude tracks automatically.

Step 9: Claude helps Jon prepare for each interview, highlighting talking points and follow-up conversations with each interviewer, from recruiter through panel interview.

Step 10: Jon provides Claude with feedback on the interview process.

Step 11: Claude produces a synthesis of metrics and outcomes and discusses adjusting strategy based on the data.

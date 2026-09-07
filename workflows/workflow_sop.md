# Workflow SOP

## Goal
Produce the best roles, and why they are the best, for Jon to apply to and provide a tailored resume and the information he needs to optimize his success probability of getting the job.

## Application tracking sheet
https://docs.google.com/spreadsheets/d/1Wilv7RxgejAtZ_CMQjkMjQacMijoBPD2ymJ32pvtsco/edit
Columns: Date Added, Company, Role, Priority, Resume (Doc), Resume (PDF), Apply Link, Tracking Link, Date Applied, Confirmation Email Received, Confirmation Date, Status, Notes.

## Process
Step 1: Automated search cadence:
- **Monday, 12:00 PM ET**: quick check — scan for new postings and tell Jon approximately how many meet the qualification criteria. Not a full ranked list, just a count so he knows what to expect.
- **Tuesday, 9:00 AM ET**: full search — run the complete search and qualification process, with results ready by 10:00 AM ET.
- **Any other time**: on-demand, triggered by Jon prompting "Let's find a dream job" in the dream-job project. Claude pulls from the most recent automated search rather than searching live, unless enough time has passed that a fresh search makes more sense.

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

Once submission is confirmed, Claude adds the role to the application tracking sheet — company, role, resume link, tracking link, and date applied — then begins checking email for a submission-confirmation message from the employer/ATS and records that confirmation date in the sheet once it arrives.

Step 8: Claude continues to monitor progress via emails received, activity on the portfolio site, or link activity, especially tracking for interview requests, updating the tracking sheet as status changes. LinkedIn activity is monitored by Jon independently (or checked when Claude prompts him to) — not something Claude tracks automatically.

Step 9: Claude helps Jon prepare for each interview, highlighting talking points and follow-up conversations with each interviewer, from recruiter through panel interview.

Step 10: Jon provides Claude with feedback on the interview process.

Step 11: Claude produces a synthesis of metrics and outcomes and discusses adjusting strategy based on the data.

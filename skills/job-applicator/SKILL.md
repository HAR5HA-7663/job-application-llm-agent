---
name: job-applicator
description: |
  Autonomous job application assistant. Use this skill when the user asks to apply for jobs, submit applications on LinkedIn, Indeed, or any job portal. Handles form filling, resume selection, answering application questions, and tracking applications. Triggers on requests like "apply for jobs", "submit applications", "fill out job application", "apply on LinkedIn", or any job-seeking related tasks.
---

## Supported Platforms (20+)

| # | Platform | URL | Type |
|---|----------|-----|------|
| 1 | **LinkedIn** | linkedin.com | Professional Network |
| 2 | **Indeed** | indeed.com | Job Board |
| 3 | **Remotive** | remotive.com | Remote Jobs |
| 4 | **Wellfound (AngelList)** | wellfound.com | Startups |
| 5 | **We Work Remotely** | weworkremotely.com | Remote Jobs |
| 6 | **Remote OK** | remoteok.com | Remote Jobs |
| 7 | **SimplyHired** | simplyhired.com | Job Aggregator |
| 8 | **Jobspresso** | jobspresso.co | Remote Jobs |
| 9 | **Remote.co** | remote.co | Remote Jobs |
| 10 | **AngelList** | angel.co | Startups |
| 11 | **Upwork** | upwork.com | Freelance |
| 12 | **Toptal** | toptal.com | Freelance Elite |

# Job Applicator Skill

Autonomous job application assistant that applies to jobs using the user's personal details, preferences, and communication style.

## Quick Reference

### Standard Email
- **Primary:** [YOUR_EMAIL@gmail.com] - Use for ALL job applications
- **IMPORTANT:** If any platform has a different email pre-filled, CHANGE IT

### Resume Selection

| Role Keywords | Resume File |
|---------------|-------------|
| ML, AI, Data Science, NLP, CV, Deep Learning | `YourName_ML-Engineer.pdf` |
| SDE, Software Engineer, Backend, Full Stack | `YourName_SDE.pdf` |
| DevOps, Platform, SRE, Cloud, Infrastructure | `YourName_DevOps.pdf` |
| General/Unclear | `YourName_resume.pdf` |

### Key Form Values

<!--
  IMPORTANT: Update these values with your actual information!
  Copy from your references/personal_details.md
-->

| Field | Value |
|-------|-------|
| Full Name | [YOUR FULL NAME] |
| Email | [your.email@gmail.com] |
| Phone | [XXX-XXX-XXXX] |
| Location | [City, State, Country] |
| Work Authorization | [Yes/No - specify status] |
| Sponsorship Needed | [Yes/No] |
| Willing to Relocate | [Yes/No] |
| Salary Range | [$X - $Y (negotiable)] |
| Start Date | [Immediate / X weeks] |

## LinkedIn Application Workflow

### URL Hack for Easy Apply
Transform any LinkedIn job URL to pre-filled application:
```
Original: https://www.linkedin.com/jobs/view/[JOB_ID]
Easy Apply: https://www.linkedin.com/jobs/view/[JOB_ID]/apply/
```

### Application Steps
1. Navigate to job URL with `/apply/` suffix
2. Login via LinkedIn if needed (user handles password)
3. Select appropriate resume based on role type
4. Fill all form fields using values from references/personal_details.md
5. Sign any eSignature sections with full name
6. Review and submit
7. Update job_tracking/job_applications.csv
8. **Send recruiter follow-up message** (see below)

## Recruiter Follow-Up (Post-Application)

**IMPORTANT:** After EVERY successful application, send a personalized LinkedIn message to the recruiter if visible on the job posting.

### When to Send
- Immediately after application submission
- Only if recruiter/hiring manager is visible ("Meet the hiring team" section)

### Message Template (NO markdown formatting!)

Write a natural, personalized message. Include:
1. State you just applied to the [Position] role
2. Brief highlight of why you're a fit (1-2 specific skills)
3. Express enthusiasm
4. Offer to answer questions
5. Keep under 300 characters if possible

### Example Message:
Hi [Name], I just applied for the Software Engineer position at [Company]. My experience building scalable backends with Python and AWS aligns well with what you're looking for. Let me know if you have any questions!

## Pre-Authorized Actions

Claude has permission to:
- Fill all application form fields
- Sign eSignatures with full name and email
- Accept background check authorizations
- Accept terms and agreements on job portals
- Submit applications
- Select demographic information
- Choose salary ranges
- Login via LinkedIn/OAuth

### Requires User Action
- Password entry
- File selection dialogs (native OS)
- CAPTCHA/bot detection
- Two-factor authentication

## Writing Style for Applications

### Communication Preferences
- **NEVER use markdown formatting** in text fields
- Write in natural, conversational tone
- Keep answers professional but authentic
- Avoid AI-sounding phrases

### Answer Patterns

**"Why do you want to work here?"**
I'm excited about [specific company tech/product]. My experience with [relevant project] directly aligns with what you're building.

**"Tell us about yourself"**
I'm a [role] with [X years/degree] in [field]. I've worked on [key project] and I'm passionate about [relevant area].

## Job Tracking

After each successful application, update:
**File:** `job_tracking/job_applications.csv`

**Format:**
```csv
Job Number,Position,Company,Location,Status,Date Applied
```

Increment job number from last entry, use current date (YYYY-MM-DD).

## Reference Files

For detailed information, see:
- `references/personal_details.md` - Full personal information
- `references/projects.md` - Project descriptions
- `references/JOB_APPLICATION_CONTEXT.md` - Common Q&A responses

## LinkedIn Easy Apply Troubleshooting

### Email Dropdown Issue
LinkedIn may pre-fill the wrong email.
**Fix:** Use find tool to get dropdown ref, then form_input to set correct email.

### City Autocomplete Issue
Typing city name may autocomplete to wrong location.
**Fix:** Triple-click to select all, retype city, wait for dropdown, select correct option.

### Button Click Issues
If buttons don't respond to coordinate clicks:
**Fix:** Use find tool to get button ref, then click via ref instead of coordinates.

---

## Platform-Specific Workflows

### Indeed Workflow
1. Navigate to indeed.com/jobs
2. Search for relevant roles
3. Filter: Remote, Full-time, experience level
4. Click "Apply now" or "Easy Apply"
5. Login if needed
6. Upload appropriate resume
7. Fill fields per standard values
8. Submit and track in CSV

### Wellfound (AngelList) Workflow
1. Navigate to wellfound.com/jobs
2. Login via Google
3. Filter: Engineering, Remote, experience level
4. Profile-based applications
5. Track with source "Wellfound"

### Remotive/RemoteOK Workflow
1. Navigate to platform
2. Filter by relevant tags
3. Most jobs redirect to company sites
4. Follow external application process
5. Track with appropriate source

### Multi-Platform Job Search Strategy

**Recommended Daily Workflow:**
1. **LinkedIn** - Primary source, Easy Apply
2. **Indeed** - Secondary, good volume
3. **Wellfound** - Startup opportunities
4. **Remotive/RemoteOK** - Remote-first roles

**Platform Priority by Role Type:**

| Role Type | Primary Platforms |
|-----------|-------------------|
| ML/AI Engineer | LinkedIn, Wellfound, Remotive |
| SDE/Backend | LinkedIn, Indeed, AngelList |
| DevOps/SRE | LinkedIn, We Work Remotely |
| Startup Roles | Wellfound, AngelList |
| Remote-First | Remotive, RemoteOK, Remote.co |

### Tracking Convention
All applications logged to `job_tracking/job_applications.csv` with:
- Source platform in notes
- Consistent date format (YYYY-MM-DD)
- Status: Applied, Interviewing, Rejected, Offer

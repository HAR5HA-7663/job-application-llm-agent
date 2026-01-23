# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

---

## IMPORTANT: Standard Email for Applications

**Always use `YOUR_EMAIL@gmail.com` for all job applications** (replace with your actual job-search email).

---

## IMPORTANT: User Communication Preferences

**Writing Style for Emails/Messages:**
- **NEVER use markdown formatting** (no `**bold**`, `*italics*`, or bullet points) when composing emails or messages
- Write in a **natural, conversational tone** - like a real person, not an AI
- Keep it professional but warm and authentic

**Work Style:**
- Be efficient and action-oriented
- Don't ask unnecessary questions when the answer is in the context files
- Update tracking files after each action

**Response Format:**
- Be concise, not verbose
- Use tables and structured summaries for status updates
- Don't over-explain or add unnecessary caveats

---

## IMPORTANT: On New Chat Session

**When opening this project in a new chat, Claude MUST:**

1. **Read this file first** (`CLAUDE.md`) to understand the project structure
2. **Check the Task Log** (at the bottom of this file) to see what was done in previous sessions
3. **Greet the user** with a brief status update
4. **After completing any task**, update the Task Log section

### Example Greeting for New Chat:
```
Welcome back! I've read the project context.

Current status:
- Total applications: [X] tracked in job_applications.csv
- Last task: [Description from Task Log]
- Ready for: [Next logical step or awaiting instructions]

How can I help you today?
```

---

## Repository Overview

This is a personal job application automation repository. It contains your professional context, resumes, and tracking files for intelligent job application automation.

## File Structure

```
job-application-llm-agent/
├── CLAUDE.md                    # Project instructions (this file)
├── resumes/                     # All resume files
│   ├── resume.html              # Main resume (self-contained HTML)
│   ├── YourName_resume.pdf      # General resume
│   ├── YourName_ML-Engineer.pdf # ML/AI focused
│   ├── YourName_SDE.pdf         # Software Engineer focused
│   └── YourName_DevOps.pdf      # DevOps focused
├── references/                  # Context files for form filling
│   ├── personal_details.md      # Personal info, education, skills
│   ├── projects.md              # Project repository
│   └── JOB_APPLICATION_CONTEXT.md  # Common Q&A responses
├── job_tracking/                # Application tracking
│   ├── job_applications.csv     # All applications log
│   └── referral_requests.csv    # Networking/referral tracking
├── ranked_jobs/                 # Company-specific job rankings
│   └── {company}_jobs_ranked.csv
├── cover_letters/               # Generated cover letters
│   └── {Company}_{Role}_Cover_Letter.txt
└── outreach_emails/             # Networking emails
```

---

## LinkedIn Resume Selection (For Job Applications)

When applying to jobs on LinkedIn using Easy Apply, select the appropriate resume based on the role type:

| Role Type | Resume to Use | File Name |
|-----------|---------------|-----------|
| **Software Engineer / SDE / Backend / Full Stack** | SDE Resume | `YourName_SDE.pdf` |
| **ML Engineer / AI Engineer / Data Scientist / NLP / CV** | ML-Engineer Resume | `YourName_ML-Engineer.pdf` |
| **DevOps / Platform / SRE / Cloud Engineer** | DevOps Resume | `YourName_DevOps.pdf` |
| **General / Mixed / Unclear roles** | Default Resume | `YourName_resume.pdf` |

### LinkedIn Resume Selection Tips:
1. **Check "Show more resumes"** - LinkedIn may hide some resumes under this dropdown
2. **Match keywords** - If job title contains "ML", "AI", "Data" → use ML resume; "DevOps", "Platform", "SRE" → use DevOps resume
3. **Default to SDE** for generic "Software Engineer" roles

---

## Job Application Tracking

**IMPORTANT:** After successfully submitting ANY job application, Claude MUST update the job applications CSV file.

### CSV File Location
`job_tracking/job_applications.csv`

### CSV Format
```csv
Job Number,Position,Company,Location,Status,Date Applied
```

### After Each Successful Application:
1. **Read the current CSV** to get the last job number
2. **Append a new row** with:
   - `Job Number`: Increment from last entry
   - `Position`: Job title
   - `Company`: Company name
   - `Location`: Remote/City/State
   - `Status`: "Applied"
   - `Date Applied`: Current date (YYYY-MM-DD format)

### Example Entry:
```csv
11,Software Engineer,Google,Remote - Mountain View CA,Applied,2025-12-29
```

---

## CRITICAL: Role Matching Before Applying

**STOP and verify role fit BEFORE applying to any job.**

### User's Core Competencies (APPLY TO THESE)

<!-- TODO: Update this table with YOUR actual skills -->

| Category | Skills/Experience |
|----------|-------------------|
| **ML/AI** | LLM fine-tuning, deep learning, NLP, computer vision, MLOps |
| **Backend** | Python (FastAPI), Go, Node.js, REST APIs, microservices |
| **DevOps** | Kubernetes, AWS, Docker, CI/CD, Terraform |
| **Data** | PostgreSQL, MongoDB, Redis, data pipelines |

### DO NOT APPLY (Immediate Skip)

<!-- TODO: Update based on YOUR restrictions -->

| Role Type | Reason |
|-----------|--------|
| **Security Clearance Required** | Visa status restriction |
| **10+ years experience required** | Experience level mismatch |
| **Staff/Principal/Director level** | Too senior |
| **Domain-specific tools you don't know** | No experience |

### Role Matching Checklist
1. **Read the job title** - Does it match your target roles?
2. **Check required skills** - Can you demonstrate 60%+ of required skills?
3. **Check experience level** - Is it appropriate for your level?
4. **Check for deal-breakers** - Security clearance? Specific tools not in skillset?

---

## IMPORTANT: Job Application Permissions (Pre-Authorized Actions)

**The user has granted FULL PERMISSION for the following actions during job applications:**

### Pre-Authorized Actions:
1. **Fill all application form fields** using data from context files
2. **Sign eSignatures** - Enter full name and email on authorization forms
3. **Accept background check authorizations** - Reference checks, criminal background checks
4. **Accept terms and agreements** - Privacy policies, application terms
5. **Submit applications** - Click submit/apply buttons
6. **Select demographic information** - As configured in personal_details.md
7. **Choose salary ranges** - Use configured range or midpoint of posted range
8. **Login via LinkedIn/OAuth** - When available

### Standard Job Application Workflow:
1. Navigate to job posting URL
2. Click "Apply" button
3. Login via LinkedIn if available
4. Upload appropriate resume based on role type
5. Fill all form fields using context files
6. Sign any eSignature/authorization sections
7. Review and submit
8. Update `job_applications.csv` with new entry
9. Confirm submission to user

### What Still Requires User Action:
- **Password entry** - Claude cannot enter passwords
- **File selection dialogs** - Native OS file pickers require user interaction
- **CAPTCHA/bot detection** - User must complete these manually
- **Two-factor authentication** - User must handle 2FA codes

---

## Key Form Field Values (Quick Reference)

<!-- TODO: Replace ALL values below with YOUR actual information -->

| Field | Value |
|-------|-------|
| Full Name | YOUR FULL NAME |
| Email | your.email@gmail.com |
| Phone | 123-456-7890 |
| Location | Your City, State, Country |
| Work Authorization | Yes/No (specify visa status) |
| Sponsorship Needed | Yes/No |
| Willing to Relocate | Yes/No |
| Salary Range | $X - $Y (negotiable) |
| Start Date | Immediate / X weeks |

---

## Cover Letter Handling (Optional Fields)

When a job application has an **optional** cover letter upload field:

### Decision Matrix:
| Scenario | Action |
|----------|--------|
| **High-value role** (FAANG, Senior positions) | Generate tailored cover letter |
| **Role with specific requirements** matching your skills | Generate cover letter |
| **Standard Easy Apply** with many applicants | Skip |
| **User explicitly requests** | Always generate |

### Cover Letter Generation Process:
1. **Create file** in `cover_letters/`
2. **File naming**: `{Company}_{Role}_Cover_Letter.txt`
3. **Tailor content** to match job requirements
4. **Format**: Plain text, professional business letter format

---

## Task Log

**Instructions for Claude:** After completing any significant task, add an entry here. Keep entries concise. **Only keep the last 4 entries** - delete older ones when adding new.

### Log Entries

| Date | Task Completed | Details |
|------|----------------|---------|
| YYYY-MM-DD | Initial setup | Repository created and configured |

### Pending/In Progress
- Fill in personal_details.md with your information
- Add your projects to projects.md
- Upload your resumes to resumes/

### Current State Summary
- **Applications:** 0 tracked in job_applications.csv
- **Projects:** 0 documented
- **Resumes:** Not yet added

---

*End of CLAUDE.md*

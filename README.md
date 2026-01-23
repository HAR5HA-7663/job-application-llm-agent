# Job Application LLM Agent

An autonomous job application system powered by Claude Code that manages your entire job search workflow - from organizing your professional profile to automatically applying to jobs and tracking applications.

[![License: MIT](https://img.shields.io/badge/License-MIT-yellow.svg)](https://opensource.org/licenses/MIT)

## What This Does

This repository provides a structured framework for Claude Code (or any LLM with browser automation) to:

1. **Store & Understand Your Profile** - Maintains your personal details, skills, projects, and work history in structured markdown files
2. **Auto-Fill Job Applications** - Uses your stored context to intelligently fill out job application forms
3. **Select Appropriate Resumes** - Automatically picks the right resume variant (ML, SDE, DevOps) based on the job type
4. **Track All Applications** - Logs every application with company, role, location, and date
5. **Rank Jobs by Fit** - Scrapes company career pages and ranks jobs by how well they match your profile
6. **Generate Cover Letters** - Creates tailored cover letters for high-value positions
7. **Send Follow-Up Messages** - Drafts personalized recruiter outreach after applying

## Demo

> *"Apply to the ML Engineer role at Google"*
>
> Claude navigates to the job posting, fills all form fields using your stored profile, selects your ML-focused resume, submits the application, logs it to CSV, and sends a follow-up message to the recruiter.

## Prerequisites

- [Claude Code CLI](https://claude.ai/code) - Anthropic's official CLI tool
- [Claude in Chrome Extension](https://chromewebstore.google.com/detail/claude-in-chrome/) - For browser automation (optional but recommended)
- Chrome browser (if using browser automation)
- GitHub CLI (`gh`) - For repository management

## Quick Start

### 1. Clone or Fork This Repository

```bash
git clone https://github.com/YOUR_USERNAME/job-application-llm-agent.git
cd job-application-llm-agent
```

### 2. Fill In Your Personal Information

Edit the template files in `references/` with your actual information:

```bash
# Required files to edit:
references/personal_details.md    # Your contact info, education, skills
references/projects.md            # Your portfolio projects
references/JOB_APPLICATION_CONTEXT.md  # Common Q&A responses
```

### 3. Add Your Resumes

Place your resume PDFs in the `resumes/` folder:

```
resumes/
├── YourName_resume.pdf          # General resume
├── YourName_ML-Engineer.pdf     # ML/AI focused
├── YourName_SDE.pdf             # Software Engineer focused
└── YourName_DevOps.pdf          # DevOps focused
```

### 4. Install Claude Code Skills

Copy the skills to your Claude Code skills directory:

**Windows:**
```bash
xcopy /E /I skills\job-applicator "%USERPROFILE%\.claude\skills\job-applicator"
xcopy /E /I skills\job-ranker "%USERPROFILE%\.claude\skills\job-ranker"
```

**macOS/Linux:**
```bash
cp -r skills/job-applicator ~/.claude/skills/
cp -r skills/job-ranker ~/.claude/skills/
```

### 5. Configure CLAUDE.md

The `CLAUDE.md` file contains instructions Claude reads when working in this project. Update it with:
- Your email address
- Your name
- Your resume file names
- Your preferred salary range
- Any job-specific preferences

### 6. Start Using

Open Claude Code in this directory:

```bash
cd job-application-llm-agent
claude
```

Then try commands like:
- *"Apply to this job: [LinkedIn URL]"*
- *"Rank jobs at apple.com/careers"*
- *"Show my application status"*

## File Structure

```
job-application-llm-agent/
├── CLAUDE.md                    # Main instructions for Claude
├── README.md                    # This file
├── LICENSE                      # MIT License
│
├── resumes/                     # Your resume files
│   ├── resume.html              # Source HTML (optional)
│   └── *.pdf                    # PDF exports
│
├── references/                  # Your professional context
│   ├── personal_details.md      # Contact, education, skills
│   ├── projects.md              # Portfolio projects
│   └── JOB_APPLICATION_CONTEXT.md  # Q&A responses
│
├── job_tracking/                # Application tracking
│   ├── job_applications.csv     # All applications log
│   └── referral_requests.csv    # Networking contacts
│
├── ranked_jobs/                 # Company job rankings
│   └── {company}_jobs_ranked.csv
│
├── cover_letters/               # Generated cover letters
│   └── {Company}_{Role}_Cover_Letter.txt
│
├── outreach_emails/             # Networking drafts
│
└── skills/                      # Claude Code skills
    ├── job-applicator/          # Auto-apply skill
    │   ├── SKILL.md
    │   └── references/
    └── job-ranker/              # Job ranking skill
        ├── SKILL.md
        └── references/
```

## Skills Overview

### Job Applicator (`/apply`)

Automatically applies to jobs on 20+ platforms including:
- LinkedIn (Easy Apply)
- Indeed
- Wellfound (AngelList)
- Remotive
- We Work Remotely
- And more...

**Features:**
- Smart resume selection based on role type
- Form auto-fill with your stored profile
- eSignature handling
- Application tracking
- Recruiter follow-up messages

**Usage:**
```
Apply to this LinkedIn job: https://linkedin.com/jobs/view/123456
```

### Job Ranker (`/rank`)

Scrapes company career pages and ranks jobs by fit.

**Features:**
- Extracts all US-based positions
- Scores against your skills and experience
- Categories: TOP PICK, HIGH, STRETCH, SKIP
- Exports to CSV for review

**Usage:**
```
Rank jobs at: https://amazon.jobs/en/search
```

## Customization

### Adding New Platforms

Edit `skills/job-applicator/SKILL.md` to add new job platforms:

```markdown
### New Platform Workflow
1. Navigate to newplatform.com/jobs
2. Login if needed (your-email@gmail.com)
3. Fill application fields per standard values
4. Submit and track in CSV
```

### Modifying Form Values

Edit `CLAUDE.md` under the "Key Form Field Values" section:

```markdown
| Field | Value |
|-------|-------|
| Full Name | Your Full Name |
| Email | your.email@gmail.com |
| Phone | 123-456-7890 |
| Salary Range | $X - $Y |
```

### Adding Role-Specific Projects

Edit `references/projects.md` to add your projects:

```markdown
## Project N: Project Name

### Overview
- **Project Name:** Your Project
- **Role:** Your Role
- **Tech Stack:** Python, AWS, etc.

### Key Accomplishments
- Built X achieving Y
- Reduced Z by N%

### Best For Roles
- Backend Engineer
- ML Engineer
```

## Best Practices

### Privacy & Security

1. **Never commit sensitive data** - Add to `.gitignore`:
   ```
   *.env
   *credentials*
   *secrets*
   ```

2. **Use your job-search email** - Not your primary personal email

3. **Review before submitting** - Claude will fill forms, but verify sensitive fields

### Application Strategy

1. **Quality over quantity** - Target roles that match 60%+ of requirements

2. **Use role matching** - Let Claude skip roles requiring skills you don't have

3. **Track everything** - The CSV becomes valuable for follow-ups

4. **Customize for high-value roles** - Generate cover letters for top picks

## Troubleshooting

### Claude Can't Find My Profile

Ensure your `references/personal_details.md` is properly formatted with all required sections.

### Skills Not Loading

Verify skills are in the correct directory:
- Windows: `%USERPROFILE%\.claude\skills\`
- macOS/Linux: `~/.claude/skills/`

### Browser Automation Issues

If using Claude in Chrome:
1. Ensure extension is installed and enabled
2. Allow the extension to run in incognito if needed
3. Check that pop-ups aren't being blocked

### Application Tracking Not Working

Ensure `job_tracking/job_applications.csv` exists with the header:
```csv
Job Number,Position,Company,Location,Status,Date Applied
```

## Contributing

Contributions are welcome! Please:

1. Fork the repository
2. Create a feature branch
3. Make your changes
4. Submit a pull request

### Ideas for Contribution

- Add support for new job platforms
- Improve matching algorithms
- Add interview scheduling features
- Create analytics dashboards

## License

MIT License - See [LICENSE](LICENSE) for details.

## Acknowledgments

- Built with [Claude Code](https://claude.ai/code) by Anthropic
- Browser automation via [Claude in Chrome](https://chromewebstore.google.com/detail/claude-in-chrome/)
- Inspired by the need to streamline job applications

## Author

Created by [Harsha Vardhan Yellela](https://github.com/HAR5HA-7663)

---

**Star this repo if it helps your job search!**

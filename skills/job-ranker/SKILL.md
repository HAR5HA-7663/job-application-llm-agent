---
name: job-ranker
description: |
  Scrape jobs from a company careers page and rank them by fit for the user. Use when user provides a company careers URL and wants jobs analyzed and ranked. Outputs a CSV with jobs ranked from TOP PICK (best fit) to STRETCH (possible but harder). Filters to US-based roles only. Reads user's personal_details.md for background matching.
---

# Job Ranker Skill

Scrape jobs from a company careers page, filter to US roles, and rank by fit.

## Workflow

1. **Navigate** to the provided careers URL
2. **Extract** all job listings (title, location, URL, requirements if visible)
3. **Filter** to US-based roles only (Remote US, or US cities/states)
4. **Read** user's background from `references/personal_details.md`
5. **Rank** each job using the matching criteria below
6. **Output** CSV file: `ranked_jobs/{company}_jobs_ranked.csv`

## CSV Output Format

```csv
Rank,Job Title,Location,Experience Required,Fit Category,Match Score,Key Matches,Gaps,Job URL
1,ML Engineer,Remote US,3-5 years,TOP PICK,85%,"Python, PyTorch, LLMs",None,https://...
```

## Fit Categories

| Category | Match Score | Meaning |
|----------|-------------|---------|
| **TOP PICK** | 80-100% | Strong match, high confidence |
| **HIGH** | 60-79% | Good match, worth applying |
| **STRETCH** | 40-59% | Some gaps but possible |
| **SKIP** | <40% | Poor fit, don't apply |

## Matching Criteria

### User's Core Competencies

<!--
  TODO: Update this section based on YOUR actual skills from personal_details.md
-->

Read from `references/personal_details.md`:
- Primary programming languages
- Cloud platforms (AWS, GCP, Azure)
- Frameworks and tools
- Years of experience
- Work authorization/visa status

### Auto-SKIP Rules (Do NOT include in CSV)

<!--
  TODO: Customize based on YOUR restrictions
-->

- Requires security clearance (if you can't get it)
- Requires more years than you have
- Staff/Principal/Director level (if too senior)
- Specialized tools you don't know

### Scoring Heuristics

- +20% if role matches primary skills
- +15% if experience requirement matches your level
- +10% if remote or preferred location
- -15% if requires slightly more experience than you have
- -25% if requires significantly more experience
- -10% for each major required skill not in your background

## Execution Notes

- Use browser automation (chrome tools) to navigate and scrape
- If careers page has filters, apply: Location=United States, remote
- If pagination exists, scrape all pages
- Extract job details from listing or click into each job if needed
- Save CSV to `ranked_jobs/` directory
- Report summary: total jobs found, jobs after filtering, breakdown by category

## Usage Examples

**User:** "Rank jobs at https://amazon.jobs/en/search"
**Action:** Navigate, scrape all US software/ML roles, rank by fit, save to `ranked_jobs/amazon_jobs_ranked.csv`

**User:** "Find the best jobs for me at Apple"
**Action:** Navigate to Apple careers, apply filters, rank all matches, save CSV

## Output Summary Format

After completing the ranking, report:

```
Job Ranking Complete for [Company]

Total jobs found: X
After US filter: Y
After skip filter: Z

Breakdown:
- TOP PICK (80-100%): N jobs
- HIGH (60-79%): N jobs
- STRETCH (40-59%): N jobs
- SKIP (<40%): N jobs (excluded)

Top 5 Recommendations:
1. [Job Title] - [Match Score] - [Location]
2. ...

Saved to: ranked_jobs/{company}_jobs_ranked.csv
```

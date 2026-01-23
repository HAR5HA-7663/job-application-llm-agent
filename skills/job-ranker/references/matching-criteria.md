# Job Matching Criteria

This file defines how to score and rank jobs against the user's profile.

<!--
  TODO: Update all sections to match YOUR actual skills and preferences
-->

## Core Competencies (High Match)

### Primary Skills (+20% each if required)
- [Python]
- [JavaScript/TypeScript]
- [Your primary language 3]

### Secondary Skills (+10% each if required)
- [AWS/Cloud]
- [Docker/Kubernetes]
- [Your secondary skills]

### Frameworks (+10% each)
- [FastAPI/Flask/Django]
- [React/Vue/Angular]
- [Your frameworks]

## Experience Level Matching

| Job Requirement | Your Experience | Score Modifier |
|-----------------|-----------------|----------------|
| 0-2 years | [Your years] | [+15% if match] |
| 2-5 years | [Your years] | [+15% if match] |
| 5-7 years | [Your years] | [-15% if gap] |
| 7+ years | [Your years] | [-25% if gap] |

## Location Preferences

### Preferred (+10%)
- Remote
- [Your city]
- [Preferred cities]

### Acceptable (+0%)
- [Cities you'd consider]

### Not Preferred (-5%)
- [Cities you'd rather avoid but would consider]

## Auto-SKIP Criteria (Exclude from results)

Jobs matching ANY of these are automatically excluded:

### Hard Restrictions
- [ ] Security clearance required (if you can't get it)
- [ ] US Citizenship required (if you're not)
- [ ] 10+ years experience required (adjust based on your level)
- [ ] Staff/Principal/Director level (if too senior)

### Domain Restrictions
- [ ] [Tools/domains you don't know - e.g., Salesforce, SAP]
- [ ] [Technologies outside your expertise]

### Role Type Restrictions
- [ ] [Roles that don't match your goals]

## Scoring Formula

```
Base Score = 50%

For each PRIMARY skill match:    +20%
For each SECONDARY skill match:  +10%
For each FRAMEWORK match:        +10%
Experience level match:          +15%
Location preference match:       +10%

For each MAJOR skill gap:        -10%
Experience level mismatch:       -15% to -25%
```

## Fit Category Thresholds

| Score | Category | Action |
|-------|----------|--------|
| 80-100% | TOP PICK | Apply immediately |
| 60-79% | HIGH | Worth applying |
| 40-59% | STRETCH | Consider if interested |
| <40% | SKIP | Don't include in results |

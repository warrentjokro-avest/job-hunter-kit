# Job Hunter Kit

A Claude Code setup that runs your job search: it finds fresh postings that match you, tailors your CV and cover letter for each one, screens them like a recruiter, tracks replies in Gmail, preps you for interviews, and fills in application forms in your own browser so you only have to review and click Submit.

## What's inside

| File | Purpose |
|---|---|
| `CLAUDE.md` | The "job lead": the workflow Claude follows (search → tailor → recruiter check → shortlist → apply → track) |
| `.claude/agents/job-scout.md` | Finds and scores postings across job boards |
| `.claude/agents/cv-optimizer.md` | ATS keyword check, tailored CV + cover letter, salary estimate |
| `.claude/agents/recruiter.md` | Screens each application like a recruiter and suggests fixes |
| `.claude/agents/hiring-manager.md` | Interview prep: behavioural and technical questions with answers from your CV |
| `.claude/agents/email-tracker.md` | Reads Gmail (read-only) and updates each application's stage |
| `profile.example.md` | Your targets: roles, location, experience limit, match threshold, salary floor, boards |
| `cv-master.example.txt` | Template for your master CV, the only source of facts |
| `answers.example.md` | Standard answers for application forms |
| `applications.example.csv` | Empty tracker with the expected columns |
| `scheduled-task-prompt.md` | Prompt for an automatic daily run |

## Setup

1. Install [Claude Code](https://claude.com/claude-code) (the desktop app is easiest). Built on macOS: the CV step uses `textutil` for Word files and Chrome for PDFs; on Windows/Linux ask Claude to use `pandoc` instead.
2. Clone this repo and copy the templates:
   ```bash
   cp profile.example.md profile.md
   ```
   ```bash
   cp cv-master.example.txt cv-master.txt
   ```
   ```bash
   cp answers.example.md answers.md
   ```
   ```bash
   cp applications.example.csv applications.csv
   ```
3. Fill in `profile.md`, `cv-master.txt` and `answers.md`. Put every real skill, number and achievement in the CV; the agents never invent anything.
4. Optional but recommended:
   - **Gmail connector**, so it can track replies and email you a daily summary.
   - **Claude in Chrome** extension, so it can fill application forms in your own signed-in browser.
5. Open the folder in Claude Code and say **"run the search"**.

## Daily automatic runs

Create a scheduled task in Claude Code (for example weekdays at 9am, 1pm and 5pm) using `scheduled-task-prompt.md`. Replace `<REPO>` with this folder's full path and `<YOUR EMAIL>` with your address.

## How you use it

- **"run the search"**: numbered shortlist of prepared jobs.
- **"apply to 1, 3"**: fills those forms in your Chrome and stops at Submit for you to review.
- **"check my emails"**: updates the tracker and shows your pipeline.
- **"prep me for <company>"**: interview prep file.

## Safety rules built in

- Never submits an application, creates accounts, logs in, types passwords, or solves CAPTCHAs.
- Never ticks terms, privacy or marketing consents or signs declarations: you do those.
- Never invents experience, tools, dates or numbers.
- Gmail is read-only, except the one summary email to yourself.

Your personal files (`profile.md`, `cv-master.*`, `answers.md`, `applications.csv`, `applications/`) are in `.gitignore` so they never get committed.

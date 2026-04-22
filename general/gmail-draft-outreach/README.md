# Gmail Draft Outreach

> ## Purpose
Automatically generate personalized Gmail drafts for Links Choice procurement outreach. Reads the prospect sheet, generates a custom email 

## Model
- **Default:** `claude-sonnet-4-5`

## System Prompt
# Skill: Gmail Draft Outreach

## Purpose
Automatically generate personalized Gmail drafts for Links Choice procurement outreach. Reads the prospect sheet, generates a custom email for each prospect based on their state, company type, and volume potential, and saves as a draft for Steve to review and send.

## When to Use
- Scheduled: weekly on Monday at 7 AM ET
- On-demand: when new prospects are added to the sheet

## Companies
- **Links Choice** — recycled golf ball procurement (primary)
- **Golf Ball Nut** — potential supplier outreach (secondary)

## Prerequisites
- Google Sheets access to prospect sheet
- Gmail draft creation via Google Workspace API
- Prospect sheet ID: reference `reference_drive_folder_ids.md` for Links Choice folder

## Prospect Sheet Format
Expected columns:
| Company | Contact | Email | State | Type | Volume Est | Status | Notes |
|---------|---------|-------|-------|------|-----------|--------|-------|
| ABC Golf | John Smith | john@abc.com | FL | Course | 50K/yr | TODO | Has range too |

Status values: TODO → DRAFTED → SENT → REPLIED → CONVERTED → DECLINED

## Execution Steps

### Step 1: Read Prospect Sheet
- Fetch all rows where Status = TODO
- Group by state/region for batch processing
- Skip rows with no email address

### Step 2: Classify Prospect Type
Each prospect gets a tailored pitch based on type:
- **Golf Course**: "We buy your range balls and lake balls. You clear inventory, we pay cash."
- **Driving Range**: "Your worn-out range balls are worth money. We buy in bulk."
- **Golf Ball Retriever/Diver**: "We buy direct from divers. Better margins than selling to middlemen."
- **Recycler/Processor**: "We buy sorted, graded inventory. Titleist Pro V1 Mint through bulk mixed."
- **Liquidator/Closeout**: "We buy overstock and closeout golf ball inventory at scale."

### Step 3: Generate Personalized Draft
For each prospect, create a Gmail draft:
- **From**: steve@linkschoice.com (or configured sender)
- **To**: prospect email
- **S

*[truncated — see source for full prompt]*
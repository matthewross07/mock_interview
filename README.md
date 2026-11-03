# ESS Mock Interview Panel — instructor notes

> **AI disclosure:** Matthew R.V. Ross built this site with **Anthropic's Claude Opus 5.5 at High effort**, in Claude Code, in November 2026. The activity concept was first brainstormed with Google Gemini. Claude wrote the page text, characters, interview questions, and timer and mood-card code, and it found and summarized the real job postings (accessed 2026-11-03). Matthew directed and revised the work and is responsible for the content. See `about.qmd` for details.

Student-facing Quarto website for the PSM ESS mock-interview activity. Instructions only, with no grading content.
This README is not rendered to the site.

## Site map

| File | Page |
|---|---|
| `index.qmd` | Instructions: prep, round structure, rotation tables, toolkit, ground rules |
| `jobs.qmd` + `jobs/*.qmd` | Job Board: an auto-generated listing. Each job page holds the candidate's prep info, then an **Interview room** with job-specific questions per seat |
| `panel.qmd` | Meet the Panel: overview of the four characters and how panelists work |
| `_includes/` | Shared pieces pulled into every job page: `_seat-a/b/c/d/ab.qmd` (character story, follow-up move, quirks) and `_mood.qmd` (mood-card button and list) |
| `timer.qmd` | Synced round timer with a QR code and shareable link (syncs across devices, so it works for online pods too) |
| `online.qmd` | Online pods: self-scheduled live call (2-week window) or async video-panel fallback |
| `discussion.qmd` | Follow-up discussion prompt |

## Common updates

- **Add a job:** copy `jobs/_template.qmd` to `jobs/<name>.qmd`. Fill in the front matter, the sections, and the Interview room (who each seat is at this employer, plus 2 job-specific questions per seat). It appears on the Job Board automatically.
- **Edit a character or the mood cards:** change the file in `_includes/` once, and every job page updates.
- **Retire a job:** delete its file, or rename it with a leading underscore (`_old-job.qmd`) to keep it without publishing it.
- **Change round timing:** edit the `PHASES` array near the top of the `<script>` in `timer.qmd`, and update the phase table in `index.qmd` to match.
- **Change the discussion prompt:** edit `discussion.qmd`.

## Preview locally

```bash
quarto preview
```

## Publish to GitHub Pages (when ready)

Google Drive and `.git` folders don't get along well, so it's safer to keep the git repo in a regular local folder (e.g. `~/git/mock_interview`) and copy or move these files there.

One-time setup:

```bash
git init && git add . && git commit -m "Mock interview site"
gh repo create mock_interview --public --source=. --push
quarto publish gh-pages
```

After that, edit and run `quarto publish gh-pages` again whenever you want to update the site.
It'll be live at <https://matthewross07.github.io/mock_interview/>. If you use a different repo name, change `site-url` in `_quarto.yml`.

## Running it in class

1. Before class, post the site link in Canvas and ask students to do the "Before class" prep.
2. In class, open **Timer**, set the pod size, press **Start now**, and project it in full screen. Students can scan the QR code to get the same synced timer on their phones.

## Canvas setup for online (async) students

Online pods have a 2-week window. The default is a self-scheduled live video call; the fallback is an async video-panel thread (Days 1–14). In Canvas:

1. **People → Groups:** create a group set of pods of ~4 (3–5 is fine). Number the members (1, 2, 3, …) in each group's description so students know their rotation number.
2. **Discussions → new discussion → "This is a Group Discussion"** using that group set. Each pod then gets its own copy. In the discussion body, post the two-week window, the Day 1–14 dates for the async fallback, and a link to the Online Students page. Pods use this space to schedule, and async pods run their candidate threads here.
3. **(Optional) Self-scheduled live pods:** Calendar → Scheduler → create an appointment group with 50-minute slots, and limit each slot to 4 users.
4. The follow-up **Discussion** prompt is the same for everyone and can be a normal (non-group) discussion.

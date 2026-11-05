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
| `online.qmd` | Online students: join a time-slot pod in Canvas Groups for a live call, or an async video pod if no time works |

## Common updates

- **Add a job:** copy `jobs/_template.qmd` to `jobs/<name>.qmd`. Fill in the front matter, the sections, and the Interview room (who each seat is at this employer, plus 2 job-specific questions per seat). It appears on the Job Board automatically.
- **Edit a character or the mood cards:** change the file in `_includes/` once, and every job page updates.
- **Retire a job:** delete its file, or rename it with a leading underscore (`_old-job.qmd`) to keep it without publishing it.
- **Change round timing:** edit the `PHASES` array near the top of the `<script>` in `timer.qmd`, and update the phase table in `index.qmd` to match.

## Preview locally

```bash
quarto preview
```

## Where this lives

Work from the local clone at `~/Developer/mock_interview`. **Don't keep it in Google Drive.** Quarto's Sass cache (in `.quarto/`) gets corrupted on Drive's synced file system, and the preview then crashes with `BadResource: Bad resource ID`.

## Publish to GitHub Pages

The site is live at <https://matthewross07.github.io/mock_interview/>. To update it after editing:

```bash
git add -A && git commit -m "Describe the change" && git push
quarto publish gh-pages
```

Stop `quarto preview` before publishing so the two renders don't collide.

**Revert:** the first live version is tagged `v1.0`. To republish an older version, run `git switch --detach v1.0 && quarto publish gh-pages`, then `git switch main`.

## Running it in class

1. Before class, post the site link in Canvas and ask students to do the "Before class" prep.
2. In class, open **Timer**, set the pod size, press **Start now**, and project it in full screen. Students can scan the QR code to get the same synced timer on their phones.

## Canvas setup for online students

Online students sign up for a pod **time** in Canvas. Each group's name is a meeting time, so joining a group is the same as booking the interview. Students who can't make any time go to an async video pod.

1. **People → + Group Set** ("Mock Interview Pods"). Turn on **Allow self sign-up** and **Limit groups to 4 members**, and leave students unassigned.
2. Create about **(online students ÷ 4) + 2** groups, and **rename each with a day, time, and time zone**, for example "Pod A – Tue Nov 18, 6:00 pm MT". Spread the times across weekdays, evenings, and a weekend, all inside the two-week window.
3. **Announce** the sign-up deadline: "People → Groups → join a pod whose time you can make. If none work, message me by [date]."
4. **After the deadline:** turn off self sign-up to lock the groups. Merge half-empty pods (3 is fine), and put students who couldn't make any time into an async pod together (rename it "Async video pod").
5. **(For async pods)** Discussions → new discussion → **"This is a Group Discussion"** using the same group set. Post the Day 1–14 dates and a link to the Online Students page. Async pods run their candidate threads there.

Rotation numbers are **alphabetical by first name** in each group's roster. The site tells students this, so you don't need to number them.

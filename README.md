# [Project Name]

> **One-line pitch:** [Who is this for, and what job does it do for them?]

- **Builder:** [Your Name] (`@github-handle`)
- **Pod:** [Pod Name / Number]
- **Product Page & Living PRD:** [Add your GitHub Pages URL]
- **App:** runs locally through Week 4; add a cloud URL in Build 5.

## Start here: Build 1

**Due Monday, November 9 at noon, New York time.** No class November 3; keep building that week.

1. Join the [class organization](https://github.com/building-with-ai-f26), then use this template to create a **public** repo named `<netid>-<project-slug>`. Ask Christian or Hew if the organization is missing from the owner list.
2. Set up Git and one coding agent during the week of October 27. Follow the [Icerynk setup guide](https://www.icerynk.com/c/fa26-tech-gb-2160-dm2-f2/content/pre-class-setup-github-openrouter-your-coding-agent).
3. Publish [`docs/index.html`](./docs/index.html): **Settings → Pages → Deploy from a branch → main → /docs → Save**. When deployment finishes, open `https://building-with-ai-f26.github.io/<your-repo-name>/`.
4. Fill in PRD v1: a reachable user, their painful before/after workflow, one core workflow, and three non-goals.
5. Build a rough local prototype. Add a screenshot or GIF and an honest Build 1 log to the Product Page, including progress, learning, problems, costs, and hours.
6. Push meaningful commits on **at least two separate days each week outside class**, including the November 3 break.
7. Submit your **Product Page URL and repository URL in Icerynk**. Come ready to demo the prototype in two minutes on November 10.

Create your PostHog account in Week 1. Install it on the Product Page and local app in **Build 2**, then verify events. The Product Page is public from Build 1; the app can stay local through Week 4.

## Repository map

| File / folder | Purpose |
| --- | --- |
| [`docs/index.html`](./docs/index.html) | Required public pitch, living PRD, and weekly build log. Update with actual work and evidence. |
| [`Intent.md`](./Intent.md), [`Plan.md`](./Plan.md), [`journal/`](./journal/) | Optional drafting aids. No duplicate submission is required. |
| [`AGENTS.md`](./AGENTS.md) | Local run commands, project context, and agent rules. Build 2 onward. |
| [`tests/`](./tests/) | Verification guidance. Build 4 offers Track A domain evals **or** Track B user replays. |
| [`SPONSOR_MEMO.md`](./SPONSOR_MEMO.md) | One-page recommendation backed by actual usage, full costs, and risks. Due December 14 at noon. |

[Icerynk](https://www.icerynk.com/c/fa26-tech-gb-2160-dm2-f2/content) holds the assignment instructions and submissions.

## Local setup

Clone **your own repository** and ask your coding agent to document the exact install and run commands here and in `AGENTS.md`.

```bash
git clone https://github.com/building-with-ai-f26/<your-repo-name>.git
cd <your-repo-name>
```

If your app needs API keys, use a local environment file such as `.env`. Keep private keys out of source code, browser code, screenshots, and commits. The template ignores `.env`; `.env.example` contains placeholders only.

## Run the DJ Transition Helper (`app/`)

The prototype is one static page, [`app/index.html`](./app/index.html). It has no backend, no build step, and no API keys.

- **Quickest:** open `app/index.html` in any modern browser (double-click it, or drag it into a browser window).
- **Or serve it locally** from the repo root, then visit <http://localhost:8000/app/>:

```bash
python3 -m http.server 8000
```

How to use it:
1. Choose the song that's playing now from the **Current song** dropdown. The app starts with 20 placeholder songs.
2. **Best next tracks** ranks every other song. Smooth = same key or ±1 on the Camelot wheel with the same letter (12 wraps to 1). Mood shift = same number with the other letter (8A ↔ 8B). Energy boost = +2. A BPM within ±6% is an easy blend; anything wider is flagged. Each suggestion gets a one-sentence explanation.
3. Click **Add to queue** to build your set. **Play** makes a queued song the current one.
4. To use your own songs, paste one per line as `Title - Artist, BPM, Key` (e.g. `Midnight Run - Nova Lane, 124, 8A`) and click **Replace song list**. Lines that don't fit that format are skipped and listed. **Restore samples** brings the placeholders back.

Nothing is saved; reloading the page resets the song list and queue.

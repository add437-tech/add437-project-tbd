# AGENTS.md — Coding Agent Operating Manual

> Give this file to your coding agent and check that it is using these instructions. Keep the stack, commands, and ground rules current.

## 1. Project Overview
- **What this repo builds:** [1–2 sentence summary]
- **Primary user & core workflow:** [See the living PRD in `docs/index.html`]
- **Tech stack:** [e.g., Python 3.12 / FastAPI / Next.js / SQLite / OpenRouter API]

## 2. Commands
- **Install dependencies:** `[e.g., npm install / uv sync]`
- **Run locally:** `[e.g., npm run dev]`
- **Run deterministic tests:** `[e.g., pytest / npm test]`
- **Run model evals:** `[e.g., python tests/eval.py]`

### DJ Transition Helper (`app/index.html`)
- **Install dependencies:** none. It's a single static HTML file with inline CSS/JS, no backend, and no API keys.
- **Run locally:** open `app/index.html` in a browser, or run `python3 -m http.server 8000` from the repo root and visit `http://localhost:8000/app/`.
- **Where the logic lives:** `keyRelation()` (Camelot rules), `bpmRelation()` (±6% blend check), `rankFor()` (sorting), `explain()` (one-sentence reason), and `parseLine()` (the `Title - Artist, BPM, Key` paste format), all in the `<script>` block of `app/index.html`.
- **Manual check:** pick a song, confirm the top suggestions are same/adjacent keys within ±6% BPM, paste a few lines including one bad line (it should be skipped with a message), and add or remove songs from the queue.

## 3. Non-Negotiable Engineering Rules
1. **Plan before coding:** Before touching multiple files, propose a brief plan and wait for approval.
2. **Small batches:** Make small, focused changes that can be reviewed and explained by a human in a single Pull Request.
3. **Explainability:** Avoid unnecessary abstractions or dependencies. Help the human builder understand the main components, what changed, why it matters, what could break, and how it was checked.
4. **Verify changes:** Run relevant checks. For a reproducible logic bug, use a failing test to demonstrate the fix when practical. Record manual checks and known limitations; follow the selected Build 4 evaluation track.
5. **Zero secrets in code:** Never hardcode API keys, tokens, or credentials. Always read from environment variables (`.env`) and update `.env.example` when new variables are needed.
6. **Stop when looping:** If a fix fails twice in a row, stop, summarize what failed, and ask the human before trying a third approach.

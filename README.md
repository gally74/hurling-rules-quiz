# GAA Referee Rules – Practice Quizzes

Static web app for practising GAA Hurling and Gaelic Football referee rules. Multiple quizzes, optional timer, 2 marks per question, 80% to pass.

**Roy Galvin** – GAA, LGFA and Camogie referee.

## What’s included

| Quiz | Description |
|------|-------------|
| **Hurling** | Official rules test practice. Choose year (2022, 2025, 2026), 50 questions. |
| **Gaelic Football** | Official rules test practice. Choose year, 50 questions. |
| **FRC Rules Review** | Football Review Committee rules & FAQ (e.g. kick-out, 4/3 structure, dissent). |
| **Hurling General Knowledge** | Rule-book general knowledge (restarts, frees, puck-out, sideline, etc.). |

- **Timer:** Optional 30-minute countdown (quiz pages or standalone `timer.html`).
- **Offline:** Pure HTML/CSS/JS and JSON; works offline after first load if cached.

## Run locally

The app uses `fetch()` for question data, so open pages over HTTP, not as `file://`.

**Option 1 – npm**

```bash
npm install   # optional, only if you want npm scripts
npm run serve
```

**Option 2 – npx (no install)**

```bash
npx serve .
```

Then open **http://localhost:3000** (or the URL shown). Use the home page to pick a quiz.

## Project structure

```
├── index.html              # Home page (quiz cards)
├── quiz.html               # Hurling rules test (multi-year)
├── quiz-football.html      # Gaelic Football rules test
├── quiz-football-frc.html  # FRC Rules Review
├── quiz-hurling-gk.html    # Hurling General Knowledge
├── timer.html              # Standalone 30-minute timer
├── package.json            # Optional; "npm run serve" → npx serve
├── assets/                 # Card images (hurling, football, FRC, hurling-gk)
└── data/                   # Question sets (JSON)
    ├── questions-2022.json
    ├── questions-2025.json
    ├── questions-2026.json   # Hurling rules test
    ├── football-2025.json
    ├── football-2026.json    # Gaelic Football rules test
    ├── football-2026-frc.json
    └── hurling-general-knowledge.json
```

## Question JSON format

Each file is a JSON array of objects. Every question has:

- `id` – number
- `question` – string
- `type` – `"single"` or `"multiple"`
- `options` – array of `{ "key": "a", "text": "Answer text" }`
- `correct` – one key string (e.g. `"a"`) or array of keys for multiple (e.g. `["a", "c"]`)

Example:

```json
{
  "id": 1,
  "question": "How does the Referee start the game?",
  "type": "single",
  "options": [
    { "key": "a", "text": "By throwing in the ball between two players from each team" },
    { "key": "b", "text": "By blowing the whistle" }
  ],
  "correct": "a"
}
```

## Adding content

### New Hurling or Football rules test year

1. Add `data/questions-YYYY.json` or `data/football-YYYY.json` in the same format as existing files.
2. In `quiz.html` or `quiz-football.html`, add the year to the `AVAILABLE_YEARS` (or equivalent) array.

### New Hurling General Knowledge questions

Append objects to `data/hurling-general-knowledge.json` using the same `id`, `question`, `type`, `options`, `correct` format. IDs should be unique and increment (e.g. next after 46).

### New FRC questions

Edit `data/football-2026-frc.json` (same structure as above).

## Deploy

- **Vercel / Netlify:** Connect the repo; build command can be empty, publish the root.
- **GitHub Pages:** Settings → Pages → Deploy from branch `main`, folder **/ (root)**. Site will be at `https://<username>.github.io/<repo-name>/`.

## License

Unlicense (or use as you like).

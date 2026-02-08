# Hurling Rules Test – Practice Quiz

Practice quiz for the GAA Hurling referee rules test. One quiz app, multiple years: choose the year on the start screen and get 50 questions, 2 marks each, 80% to pass. Optional 30-minute timer.

## Adding another year

1. **Add the question file**  
   Create `data/questions-YYYY.json` (e.g. `data/questions-2025.json`) with the same format as `data/questions-2026.json`: a JSON array of objects, each with `id`, `question`, `type` (`"single"` or `"multiple"`), `options` (array of `{ "key": "a", "text": "..." }`), and `correct` (single key string or array of keys for multiple).

2. **Register the year in the quiz**  
   In `quiz.html`, find the line:
   ```js
   const AVAILABLE_YEARS = ['2026'];
   ```
   Add the new year, e.g.:
   ```js
   const AVAILABLE_YEARS = ['2026', '2025'];
   ```

No separate HTML file per year; the same quiz loads the chosen year’s JSON.

## Using on your iPhone (GitHub Pages)

1. **Push this project to GitHub**  
   Create a new repo (e.g. `hurling-rules-quiz`), then:
   ```bash
   git init
   git add .
   git commit -m "Initial commit"
   git remote add origin https://github.com/YOUR_USERNAME/hurling-rules-quiz.git
   git push -u origin main
   ```

2. **Turn on GitHub Pages**  
   In the repo: **Settings → Pages**. Under “Build and deployment”, set **Source** to **Deploy from a branch**. Choose branch `main` and folder **/ (root)**. Save. After a minute or two the site will be at:
   `https://YOUR_USERNAME.github.io/hurling-rules-quiz/`

3. **Open on your iPhone**  
   In Safari, go to `https://YOUR_USERNAME.github.io/hurling-rules-quiz/` — the root URL opens the quiz. Use **Add to Home Screen** (Share → Add to Home Screen) so it opens like an app.

The quiz is static HTML/JS and works offline after the first load if your browser caches it.
